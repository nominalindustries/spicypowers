---
name: riddle-me-this
description: Use when your human partner opens with "riddle me this" or otherwise poses a half-formed idea, a "has anyone done X", or an "is this possible" curiosity. It is an exploratory feasibility probe, not a spec to execute. Research it, give a verdict, do not start building.
---

# Riddle Me This

## Overview

"Riddle me this" is your human partner's opener for an exploratory feasibility probe: a half-formed idea or a curiosity they want poked at. The mistake to avoid is treating it as a task to execute. They are kicking tires, not commissioning a build. Match that.

## When this triggers

Fires when your human partner poses a probe rather than a task: "riddle me this", "has anyone done X", "is it possible to Y", "could you Z". The tell is a question about feasibility or prior art, not an instruction with a deliverable.

## How to handle a riddle

1. **Explore, do not execute.** Do not jump into building or writing a spec. The output is understanding, not an implementation.
2. **Check prior art.** Most riddles need a real look at whether someone has done this and how. Search. Do not answer "has anyone done X" from memory alone when X is checkable.
3. **Lead with the verdict.** Is it viable, what would it take, what is the catch. First line is the answer, reasoning after.
4. **Surface the interesting part.** The constraint that makes it hard, or the surprising "actually yes" - that is usually what they were fishing for. Name it.
5. **Match the energy, do not over-scope.** They are poking. A few paragraphs with a clear take beats a forty-step project plan. If they want to go deeper, they will say so.
6. **Notice when a riddle graduates.** If the probe turns out to have real legs, say so explicitly. At that point it can become a brainstorm or a logged `research-adventure`. Naming the graduation is useful, do not just quietly escalate into a build.

## Red flags

| Symptom | What it means |
|---|---|
| You started building or writing a spec | It was a probe. Explore, do not execute. |
| You answered "has anyone done X" without checking | Prior art is checkable. Search before answering. |
| The verdict is buried below the background | Lead with viable-or-not. |
| You returned a full project plan | Over-scoped. They were kicking tires. |
| A promising probe was escalated without saying so | Name the graduation. Let them decide to commit. |

## Rationalizations to reject

- "They asked how to do it, so they want it built." They asked if it is possible. Answer that first.
- "I know the answer, no need to search." For prior-art and feasibility questions your memory may be stale. Check.
- "More detail is more helpful here." Not for a probe. A clear verdict beats a plan they did not ask for.
