---
name: sbtb
description: Use when your human partner brain-dumps what they worked on and needs a manager-facing update out of it - an EOD, a standup note, a status report, a progress summary. Translates messy, parallel, outcome-buried work notes into a clear, paste-ready update pitched at the right altitude.
---

# SBTB (Spicy Brain Translation Bureau)

## Overview

SBTB is the work-facing translation workflow. Your human partner brain-dumps what they actually did, in whatever order it comes out, and you translate it into an update their manager can read in fifteen seconds and act on.

This is translation, not spin. A spicy brain misreports its own progress in two predictable directions: it undersells near-finished work (it sees every loose thread, so 90% done feels like 50%), and it over-details (everything feels connected, so the update becomes a process diary). SBTB corrects both distortions. The goal is an update that is more accurate to reality than the raw dump and legible to a linear reader. Not inflated. Accurate and readable.

SBTB is also a capture layer, not only an output step. Your human partner records progress by dumping in their native non-linear mode: several tasks and thought parades at once, in any order. Converting that to linear, ticket-mapped form is your job and happens at report time, never theirs. This is the real point. Removing the translation tax is what makes accurate reporting actually happen. A spicy brain forced to linearize its own work before it can record it will record less, and less accurately, than one that can just dump.

## When this triggers

Fires when your human partner dumps work activity and needs it turned outward: end-of-day updates, standup notes, status reports, progress summaries, "what did I get done" messages to a manager or lead.

Does not fire for notes to self or planning. A brain dump with no outward audience is `brain-dump-intake`, not this.

## The translation

1. **Lead with outcomes, not process.** The first line is what moved forward or what is now true, not the journey. "TST environment is deployed and passing smoke tests" beats "I started on TST, hit an OVN issue, traced it, then...".
2. **Report at the altitude of outcomes and plan, not task ordering.** Give the manager enough that the plan is visible and clearly under control. Do not hand them a granular task list. A manager who receives task-level detail will reorder it without the context your human partner has, which produces worse sequencing. Right-altitude reporting is professional, not evasive.
3. **Do not let near-done work read as barely started.** If the dump describes something as 90% done by listing everything still open, translate it to "basically done, X remaining". Match the words to the actual state.
4. **Filter to decision-relevant signal.** The manager gets what they need to make decisions and what they need to act on. Tangents, dead ends explored and closed, and interesting-but-irrelevant detail get cut. If a dead end matters because it explains time spent, summarize it in one line.
5. **Translate systems language.** Your human partner thinks in systems, epics, and patterns. A linear manager may not parse "separated the stateful and compute Terraform state". Translate to the outcome: "set up the infrastructure so a failure in one part can't take down the rest".
6. **Surface blockers clearly and separately.** If there is something the manager needs to do or know, it gets its own line, not buried mid-paragraph.
7. **Make it paste-ready.** The output is something your human partner pastes as their own with no editing. Run it through `nominal-voice` before handing it over.
8. **Hold the mapping.** Maintain the running crosswalk between your human partner's tasks and thought parades and the real work items they map to: ticket numbers, epics, whatever the org's tracker uses. They should never have to think in ticket-tracker structure to make progress. You keep the mapping so the linear, ticket-referenced record is always available at report time without them ever assembling it.

## Red flags

| Symptom | What it means |
|---|---|
| The update reads as a process diary ("first I tried, then this broke") | Translation 1 failed. Lead with the outcome. |
| You handed over a granular task list | Wrong altitude. It invites reordering. Pitch at outcomes and plan. |
| Near-finished work is described as in-progress or barely started | Translation 3 failed. Match the words to the real state. |
| The one thing the manager must act on is buried in paragraph three | Translation 6 failed. Pull blockers out. |
| Systems jargon left untranslated | A linear reader will not parse it. Translate to the outcome. |
| The update is longer than the brain dump | You added instead of translating. Cut. |

## Rationalizations to reject

- "The dump didn't state outcomes, so I can't lead with them." The outcomes are in the dump, described as process. Extracting them is the job.
- "More detail is more transparent." More detail invites reordering and micromanagement. The right altitude is more useful to the manager, not less honest.
- "It's only 90% done, so I should say in progress." If it is 90% done, say basically done with the remainder named. Underselling is a distortion, fix it.
- "This tangent is interesting." If it is not decision-relevant for the manager, it does not go in the update.
- "The systems framing is more accurate, I should keep it." It is accurate and unreadable. Accurate and readable is the bar.

## Verification before handing off

Before giving your human partner the update, check:

- Outcomes are in the first line or two, not the journey
- Pitched at outcomes and plan, not a reorderable task list
- Near-done work is described as near-done
- Anything the manager must act on has its own line
- No untranslated systems jargon
- It is shorter than the brain dump
- It has been through `nominal-voice`
