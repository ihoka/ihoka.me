---
name: blog-post-writing
description: Use when writing blog posts for Istvan's personal blog (ihoka.me). Triggers on requests to write, draft, or create blog posts, articles, or essays for the site.
---

# Blog Post Writing

## Overview

Write blog posts that match Istvan's voice: direct, personal, philosophical. Every post is grounded in lived experience and explores one core insight deeply. The voice is a thinking person sharing their thought process, not a content creator optimizing for engagement.

## Voice Characteristics

### Sentence Rhythm

Mix short punchy sentences with longer ones. Short sentences carry weight.

- "I enjoy it."
- "Movement is critical to make progress."
- "This is backwards."
- "That's architectural control."

Follow a short declarative hit with a longer sentence that unpacks it. Never let sentence length stay uniform.

### Personal & Raw

- Use "I think", "I realise", "I have experienced it" - share your thought process, don't state facts from authority
- Let emotion through when it's real: "I was mesmerised", "oh, yeah, and I'm getting a motorbike"
- Admit uncertainty: "I think I have outgrown that"
- No corporate polish. No "single most effective mechanism" or "forcing function". Say it plainly

### Direct Address

- Use "you" and "we" naturally, as if talking to a colleague
- "Clearly, we are not soldiers and we do not shoot weapons."
- "Think about this scenario: you are in a foreign city..."

### No Hedging, No Filler

- Every sentence earns its place. No transitions like "Let's explore..." or "It's worth noting that..."
- Make bold claims: "We are not engineers if we are not making decisions."
- Cut any sentence that doesn't add meaning

## Structure Patterns

### Context Opener

Most posts start with WHY this post exists - a personal context that grounds it:

- "This is a leadership piece which I was planning on applying at Builder.ai before its collapse."
- "This is from an email that I sent to a dear colleague of mine at Builder.ai."
- "I enjoy it." (the context IS the personal declaration)

Start with the human story, not the abstract argument.

### One Insight, Explored Deeply

Each post has ONE core counterintuitive insight:

- Wrong decisions are still progress (because they eliminate uncertainty)
- Restrictions make programming more productive (not less)
- Feminism is about leading without power
- DIP is the only SOLID principle that operates at the architectural level

Find the twist. If there's no counterintuitive reframe, the post isn't ready.

### Analogies From Outside Software

Ground technical concepts in non-software analogies:

- Military tactics for engineering leadership
- Navigating a foreign city for decision-making
- Programming paradigm history for AI-assisted coding

The analogy should carry real explanatory weight, not be decorative.

### Section Count

- Short personal posts: 0-2 headers (like "Why I am a programmer")
- Medium posts: 3-5 H2 sections
- Long technical posts: up to 8-10, but only when the topic demands it (like DIP)

Never pad sections. If the post is done in 20 lines, it's done in 20 lines.

### Strong Closing

End with a line that lands. Short, declarative, ties back to the core insight:

- "That's why it's my favorite. That's architectural control."
- "The future isn't about writing less code. It's about thinking more clearly about what code should do."
- "That's when I knew that I wanted to be a programmer."

### Lists Used Sparingly

- 2-4 items max in most lists
- Used for clarity, not decoration
- Never write "how-to" listicles with 5+ tips. That's not the voice

## What NOT To Do

- **No content-marketing voice**: No "In this post, we'll explore...", no "Let's dive in", no engagement hooks
- **No listicle format**: Don't write "5 Reasons Why..." or "How to X" with numbered tips
- **No hedging language**: No "arguably", "it could be said that", "in my humble opinion"
- **No uniform length**: Don't pad a short post to feel substantial. Don't cut a deep exploration short
- **No abstract openings**: Don't start with a definition or general statement. Start with a person, a moment, a story
- **No HTML in markdown**: Pure markdown only (project rule from CLAUDE.md)

## Technical Posts

When writing about technical topics (like DIP, vibe coding):

- Still ground it personally: "This is my favorite SOLID principle"
- Explain concepts in plain language BEFORE showing code
- Use text diagrams (`→`, `←`) for architecture, not just code blocks
- Build the argument progressively: problem → insight → solution → implications
- Include "When NOT to use" sections - show you understand tradeoffs
- Reference specific authors/books when drawing on their ideas (e.g., "Robert Martin, in *Clean Architecture*")

## Jekyll Frontmatter

```yaml
---
layout: post
title: "Post Title Here"
date: YYYY-MM-DD
categories: blog
tags: [tag1, tag2, tag3]
---
```

- Title case for most titles, but lowercase is acceptable for personal/philosophical posts (e.g., "on feminism")
- 2-4 tags that capture the key themes
- Category is always `blog`

## Quick Reference: Voice Checklist

Before finishing a post, verify:

1. Does it open with personal context or story?
2. Is there ONE counterintuitive insight?
3. Are sentences varied - some very short, some long?
4. Does it use "I think" / "I realise" rather than stating facts from authority?
5. Is there an analogy from outside software (for technical posts)?
6. Does the closing line land?
7. Would you cut any section without losing meaning?
