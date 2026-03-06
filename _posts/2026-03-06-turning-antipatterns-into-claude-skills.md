---
layout: post
title: "Turning Codebase Antipatterns into Claude Skills"
date: 2026-03-06
categories: blog
tags: [ai, claude-code, rails, stimulus, refactoring]
---

I spent a morning last week auditing a Rails codebase for string-based HTML construction in JavaScript controllers. Forty violations across twelve files. The same antipattern, copy-pasted and mutated over months, each instance a small act of forgetting that a better way existed.

The better way was already there. Two controllers in the same codebase used `<template>` tags correctly. One developer had figured it out, used it in their feature, and the knowledge never spread. This is the part that got me thinking.

## The Antipattern

If you have worked with Rails and Stimulus for any length of time, you have seen this. A Stimulus controller needs to add elements to the DOM dynamically --- a card, a list item, a notification. The developer reaches for the most obvious tool: a template literal.

```js
// This is what forty of our controllers were doing
const html = `<div class="card border rounded-lg p-4">
  <p class="font-medium text-gray-900">${item.name}</p>
  <span class="text-sm text-gray-500">${item.category}</span>
  <button class="btn-delete" data-action="click->items#remove">
    <svg>...</svg>
  </button>
</div>`
container.insertAdjacentHTML("beforeend", html)
```

It works. It ships. And it creates a mess that compounds over time.

The HTML structure lives in JavaScript now, invisible to your ERB templates, unreachable by your Tailwind purge config, disconnected from your Rails view helpers. You cannot use `svg_icon("close-x")` inside a template literal. You cannot use `t(".delete")` for i18n. Every Tailwind class in that string is a class your tooling cannot trace. Every piece of markup is something a designer cannot find by searching the views directory.

The worst part is how it spreads. A developer needs a similar card elsewhere, finds this controller, copies the pattern. Now you have the same HTML in two JavaScript files and zero ERB files. Multiply that by twelve controllers and you have a codebase where a significant chunk of your UI lives in the wrong layer.

## The Right Pattern

The fix is the HTML `<template>` element. You define the markup in your ERB view where it belongs, and clone it in JavaScript when you need it. The browser does not render `<template>` content --- it just holds it in the DOM as an inert fragment, ready to be cloned.

I found two variations that work well with Stimulus.

### Pattern 1: Stimulus Target Template

When a template belongs to a specific controller, make it a Stimulus target.

In your ERB partial:

```erb
<div data-controller="items">
  <template data-items-target="cardTemplate">
    <div class="card border rounded-lg p-4">
      <p data-role="name" class="font-medium text-gray-900"></p>
      <span data-role="category" class="text-sm text-gray-500"></span>
      <button data-action="click->items#remove" class="btn-delete">
        <%= svg_icon("close-x") %>
      </button>
    </div>
  </template>

  <div data-items-target="list"></div>
</div>
```

In your Stimulus controller:

```js
import { Controller } from "@hotwired/stimulus"

export default class extends Controller {
  static targets = ["cardTemplate", "list"]

  addCard(item) {
    const card = this.cardTemplateTarget.content
      .firstElementChild.cloneNode(true)
    card.querySelector('[data-role="name"]').textContent = item.name
    card.querySelector('[data-role="category"]').textContent = item.category
    this.listTarget.append(card)
  }
}
```

Notice what happened. The HTML is back in ERB, so `svg_icon` works. Tailwind can see the classes. The JavaScript only does what JavaScript should do: clone a node and fill in data. The `data-role` attributes act as stable hooks for hydration --- they will not collide with Stimulus targets or actions.

### Pattern 2: Global ID Template

Some templates get reused across multiple controllers. A delete button, a loading spinner, an empty-state message. These belong in a shared partial with a DOM `id`.

```erb
<!-- _delete_button_template.html.erb -->
<template id="delete-button-template">
  <button type="button" class="text-red-500 hover:text-red-700">
    <%= svg_icon("close-x", class: "w-4 h-4") %>
  </button>
</template>
```

Then a shared helper function that any controller can import:

```js
// helpers/dom.js
export function createDeleteButton({ action, dataset = {} }) {
  const template = document.getElementById("delete-button-template")
  const button = template.content.firstElementChild.cloneNode(true)
  if (action) button.dataset.action = action
  Object.entries(dataset).forEach(([key, value]) => {
    button.dataset[key] = value
  })
  return button
}
```

Now any controller that needs a delete button calls `createDeleteButton({ action: "click->items#remove" })` and gets a fully rendered button with the correct icon, the correct classes, and the correct accessibility attributes. One source of truth, in a view file where it belongs.

### When NOT to Template

This is important, and I learned it the hard way. Not everything needs a template.

Setting `textContent` on a single element is fine. Toggling a CSS class is fine. Adding or removing a simple class-based state does not require a `<template>` tag. The rule of thumb: if you are constructing a structure with multiple nested elements or embedding HTML tags, use a template. If you are updating a single property on an existing element, just do it directly.

Without this boundary, you end up with a `<template>` for every tiny DOM manipulation, and that is its own kind of mess.

## From Pattern to Skill

Both of these patterns existed in the codebase. Neither had spread. This is the dynamic I see everywhere: someone figures out the right approach, uses it in their feature, and the knowledge stays local. Style guides are supposed to fix this. They don't. A style guide sits in a wiki and hopes developers read it before writing code. Nobody does. They read it during code review, two days after the damage is done.

I realise this is what Claude Code skills actually solve. Not by being a smarter style guide, but by being present at the moment of implementation.

A skill is a markdown file in your project's `.claude/skills/` directory. It has a name, a description that tells Claude when to load it, and the actual guidance. When Claude starts a conversation and the task matches the description, it loads the skill into context. Every session. Every developer.

The description is the trigger:

```yaml
---
name: dom-template-pattern
description: Use when a Stimulus controller needs to create new DOM
  elements, or when refactoring existing innerHTML/template literal
  HTML construction.
---
```

The body of the skill does three things: states the rule, shows the patterns with real file paths from your codebase, and lists the red flags that indicate a violation.

That last part --- real file paths --- matters more than you might think. When Claude reads "Existing example: `_digital_materials.html.erb:77-91`", it can go read the actual implementation. It picks up your naming conventions, your CSS classes, your data attributes. The skill becomes grounded in your codebase, not in generic best practices.

The red flags section teaches Claude to recognise violations:

- Template literals containing HTML tags (`<div>`, `<svg>`, `<span>`)
- `insertAdjacentHTML` or `innerHTML` with string arguments
- `document.createElement` chains building three or more nested elements

When Claude encounters any of these while working on a file, the skill fires and it knows to refactor toward the template pattern instead.

## Writing a Skill From Your Own Antipatterns

Here is the process I used, and I think it generalises well.

First, audit for the antipattern. Ask Claude to search for symptoms --- string-based HTML injection, raw SQL, manual auth checks, whatever your team's recurring sins are. Count the violations. "Forty violations across twelve files" is a compelling reason to invest thirty minutes. Two violations in one file probably is not.

Then find the existing good pattern. It is almost certainly already in your codebase. If nobody did it right yet, build one reference implementation first. You need a concrete example, not an abstract rule.

Write the skill. State the rule in one sentence, impossible to misinterpret. Show both the correct patterns and the red flags. Include the boundaries --- what NOT to apply the pattern to. Without that, Claude will over-apply it, and an over-zealous skill is worse than no skill at all.

Test the skill. Give Claude a hypothetical task that would normally trigger the antipattern. When I tested the DOM template skill, I asked it to add notification cards to a dashboard controller arriving via ActionCable. Claude correctly chose Pattern 1, used `cloneNode` with `data-role` hydration, and explicitly refused to build HTML strings --- citing the skill's rules. That is a passing test.

If Claude had still reached for template literals, I would know the skill needed clearer language or a stronger prohibition.

## The Compound Effect

Once the skill exists, it pays for itself twice. It prevents new violations in every future conversation. And it becomes a refactoring guide --- you can point Claude at each violating file and say "refactor this to follow the dom-template-pattern skill." The refactors come out consistent because they all follow the same source of truth.

I think this is fundamentally different from how we have been thinking about AI coding assistants. We keep asking "how do I make the AI write better code?" The answer is not better prompts. It is encoding your team's hard-won knowledge into a format the AI can use at the right moment.

Your codebase already knows the right patterns. They are just trapped in the files of whoever figured them out first. Skills set them free.
