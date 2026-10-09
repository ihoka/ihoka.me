---
layout: post
title: "Write the Language First"
date: 2026-10-09
categories: blog
tags: [ruby, dsl, ai, programming]
---

I have been building [Tactical Trainer](https://tacticaltrainer.eu), a training app based on the Tactical Barbell books. It plans strength and conditioning sessions, and it pushes them to your watch.

For a long time, the app described its own domain in five different formats. Ruby classes for barbell periodization. Hash literals for which lifts make up a session. More hash literals for rotation presets. Markdown files, read by a hand-written parser, for the conditioning workouts. A flat value object for a single movement's dosage. A 747-line generator glued it all together.

None of these formats could say what the books say. So the code guessed. And the guesses drifted.

## What the guessing cost

The markdown parser silently lost data. One workout's 20-second rest vanished, because a `find` took the first match. Another workout's finisher was dropped entirely. "Long Steady State" was seeded as a three-exercise circuit with a spurious `reps: 4`.

The watch export read keys the generator never wrote, and produced descriptions like `": 3x5 @ %"`. Its test passed, because the fixture was hand-written in a shape nothing actually produced.

The app had three different versions of the Operator progression, in code and in two AI prompts. None of them matched the book.

None of these bugs were hard. They were invisible. You could not look at any one place and see what a session *was*.

## My coach already had a language

I don't have a coach in a gym. My coach is K. Black, the author of the Tactical Barbell books. And his books already have a language.

A ladder from 10 down to 1. A cluster of rounds with a rest range between them. A list of lifts, with the deadlift for one work set only. Terse, precise, and every reader knows exactly what to do. There are no hash literals in Tactical Barbell.

So I stopped trying to fit the training domain into data formats. The idea was mine: write the language first, in the shape of the book, and make the code speak it.

```ruby
session "hic-01-connaught-range-10-to-1s" do
  ladder 10.downto(1) do |n|
    burpee reps: n
    sprint distance: n * 10
  end
end
```

```ruby
session "operator-black-bp-sq-wpu-dl-1ws" do
  lift "bench-press"
  lift "squat-back"
  lift "weighted-pull-up"
  lift "deadlift", work_sets: 1, notes: "1 work set only"
end
```

That reads like the book page. And it holds up when the session gets complicated. This is the Transition Complex, from Tactical Barbell II:

```ruby
session "hic-40-transition-complex" do
  repeat 1..3 do
    squat_front reps: 1, load: percent_tm(85)
    repeat 10 do
      sprint distance: 50
    end
    rest 3.minutes
    bench_press reps: 1, load: percent_tm(85),
      alternatives: [ floor_press(reps: 1, load: percent_tm(85)) ]
    plyo_push_up reps: 10
    rest 3.minutes
    deadlift reps: 1, load: percent_tm(85),
      alternatives: [ weighted_pull_up(reps: 1, load: bodyweight_plus(36)) ]
    med_ball_slam reps: 10
  end
end
```

One to three rounds. A heavy single at 85% of your training max, then ten 50-metre sprints, then three minutes of rest. Floor press as an alternative to the bench, weighted pull-ups as an alternative to the deadlift. Every one of those details used to be a string in a markdown file, waiting for a parser to misread it. Now each is a node with a type: a `Repeat` inside a `Repeat`, a `Rest`, a `Dose` with a load and its alternatives. The app plans with them, and the watch exporters fold them into COROS and Garmin workouts.

## Why Ruby

There is an old saying in programming: when you have a hard problem, first write a language in which solving the problem is easy. I don't know who said it first. The clearest version I know is Paul Graham's, in his essay [*Programming Bottom-Up*](https://paulgraham.com/progbot.html), about Lisp: "you don't just write your program down toward the language, you also build the language up toward your program." Grow the language until the program itself becomes short and obvious.

Ruby is the best mainstream language I know for doing this. Blocks give you nesting for free. Optional parentheses and keyword arguments let a method call read like a sentence. `instance_eval` lets a block run in the context of a builder, so `burpee reps: n` is a method call, not a string to be parsed. Rails has trained a whole generation of us to read `config/routes.rb` and `has_many :comments` without thinking of them as code at all.

The usual criticism is that Ruby DSLs are too magical. I think that criticism is about `method_missing`, not about DSLs.

So this DSL refuses to guess. Every directive is a real method, with its arity checked. Movement directives are generated from the exercise table, so the vocabulary *is* the database of movements. `method_missing` exists only to fail:

```text
repaet(3) → unknown directive :repaet — did you mean repeat?
```

A typo blocks the deploy, with a file and line number, instead of silently turning into a different workout. The magic is in service of strictness, not in place of it.

Underneath, the language is small. Three combinators (`Sequence`, `Repeat`, `Interval`) and three leaves (`Dose`, `Rest`, `Choice`). A ladder is not a node type. It is a helper that builds a `Repeat` inside a `Sequence`. The interpreter has six branches. The builders produce frozen `Data` objects that round-trip to JSON, so the same tree is stored in the database, diffed in tests, and exported to two different watch platforms.

## The part that matters now

I didn't write a single line of this DSL. Agents built all of it. A fresh agent per task, a review per task, a final review of the whole branch. The DSL machinery is about 1,800 lines. My part was the idea, the planning, and the reviews.

This is where I think DSLs become more important, not less.

When an agent writes your code, your job shifts. You are no longer the author. You are the reviewer. And reviewing is limited by how much you can hold in your head at once. A 747-line generator full of hash keys is not something I can verify. I can read it, but I can't *see* whether it matches the book.

A session written in the DSL, I can verify in ten seconds. I hold the book open next to it. The ladder goes 10 down to 1. Burpees, then sprint, 10 metres per rep. Correct.

The DSL moves the reasoning up to the level of the domain. The agent can write as much machinery underneath as it likes. That machinery has to be correct once, and it is tested once. The thing that changes all the time, the content, is written in a language a human can check at a glance.

It works the other way too. The app's own AI coach reads and writes these same trees, through a strict parser. It cannot invent a movement that doesn't exist, or a load that the algebra can't express. The language is the guardrail, for the agent and for me.

## The language makes the bugs visible

Once the domain had a language, the bugs had nowhere to hide. Lost rests, dropped finishers, mis-sourced workouts, an export that printed `": 3x5 @ %"`. All of them showed up as soon as I tried to write the sessions down in a form that couldn't guess. The fixes were mostly boring. Finding them was the hard part.

There are limits. One workout has a 5-minute overlay that runs concurrently with everything else, and the algebra can't express that. So it lives in a note, next to the code, with a citation to the book. Watch platforms can't hold everything the tree can say, so every export returns the payload *and* a list of what was lost. Honest about what it can't do.

## When not to

Not every domain deserves a language. If the concepts are not stable, you will spend your time redesigning grammar instead of shipping. If there is only one consumer, a plain data structure is probably enough. I had five formats, three exporters, an AI coach and a book corpus all describing the same thing. That is when a language pays for itself.

## Write the language first

AI makes code cheap. It doesn't make understanding cheap.

The bottleneck is no longer typing. It is knowing whether what was typed is right. A good DSL shrinks the thing you have to check, down to the size of the problem itself.

Write the language first. Then the problem is easy, for you and for the machine.
