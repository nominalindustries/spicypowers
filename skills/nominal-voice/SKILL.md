---
name: nominal-voice
description: Use whenever drafting text your human partner will send, paste, or publish as their own writing - Slack messages, EOD updates, emails, commit messages, PR descriptions, blog posts, Notion pages, docs, app copy, anything that goes out in their name. Ensures the draft reads as human-written and matches your human partner's mechanical writing conventions. Does not apply to chat replies, internal planning, or tool output.
---

# Nominal Voice

## Overview

Anything your human partner pastes under their own name has to read as them, not as an AI. This skill is the mechanical layer: punctuation and small conventions that act as fingerprints. Tone and register (casual vs manager-facing) are not this skill's job, that belongs to `sbtb`. This skill only governs the marks on the page.

The core principle: AI-generated text has tells. Remove them.

## When this triggers

Fires before handing your human partner any of: Slack messages, EOD updates, emails, commit messages, PR/MR descriptions, blog posts (Businessverse included), Notion pages, app UI copy, marketing copy, README and docs content.

Does not fire for: replies to your human partner in a working chat, internal planning notes, instructions written for a subagent, code itself, or anything your human partner will read but not republish.

## The rules

1. **No emdashes. Ever.** The emdash (the long dash) is the single biggest AI tell, because standard keyboards have no key for it, so humans rarely type one. Replace every one with a comma, a pair of parentheses, or a regular hyphen with spaces around it. Pick whichever fits the sentence.
2. **No en dashes either.** The en dash (the medium dash) shows up in number and date ranges. Use a plain hyphen: "10-15", "Mon-Fri", "pages 3-7".
3. **Approximate ranges get "ish".** If a range is an estimate, write "1-1.5ish", not "1-1.5". If the number is genuinely exact (a count, a port number, a version), leave it alone. The "ish" signals the estimate is fuzzy on purpose.
4. **Commas over dashes for asides.** Where the instinct is a dash-bracketed aside, use commas, or parentheses if it reads more like a side note.
5. **Bullets for structure.** When content has more than two or three parallel points, bullet them. Your human partner reads and writes in bullets.
6. **Plain hyphens for compound modifiers.** "two-tier system", "spicy-brain workflow". Normal hyphen, no drama.
7. **Cut intensifiers that are not load-bearing.** Words like "honestly", "genuinely", "truly", "to be fair", "I'll be honest", "frankly". The test is whether the word adds meaning or just decorates. If it signals something real (a genuine candor flag, a real contrast), it can stay. If it is throat-clearing, cut it. Over-used, these read as fake, the writer protesting too much, and they are a strong AI-default tell, this is most of why ChatGPT-style prose sounds off. Be strictest in manager-facing and formal writing, where even a load-bearing one is often better dropped. In casual peer messages an occasional real one is fine. The failure mode is using them as a reflex, not using them at all.

## Red flags

| Symptom | What it means |
|---|---|
| An emdash anywhere in the draft | Rule 1 violated. Stop, replace it before continuing. |
| An en dash in a range | Rule 2 violated. Swap for a plain hyphen. |
| An estimated range with no "ish" | Rule 3 violated, or confirm the number really is exact. |
| The draft reads uniformly polished, every sentence the same length and shape | It does not sound like your human partner. Loosen it. |
| "Honestly", "genuinely", or similar used as reflex, not adding meaning | Rule 7 violated. If it is not load-bearing, cut it. |
| You "corrected" one of their hyphens into an emdash | You introduced a tell. Undo it. |

## Rationalizations to reject

- "It's just an internal Slack message, nobody checks punctuation." Wrong. The emdash tell applies everywhere your human partner's name is on it, and internal readers are exactly the ones who would notice.
- "An emdash is the grammatically correct choice here." Grammatical correctness is not the goal. The goal is that the text does not read as AI-written. A comma is always available.
- "It's a commit message, it doesn't count." If your human partner commits it, it is their voice in their repo. It counts.
- "The range is precise, so it doesn't need -ish." If it is an estimate, it needs -ish. Only skip -ish when the number is a true exact value.
- "They will fix it themselves." Your human partner should never have to. Hand them a clean draft.
- "'Honestly' just reads as natural and warm here." Ask if it is load-bearing. If it flags something real, keep it. If it is reflex decoration, it reads as fake, that is the ChatGPT-default sound. Cut the reflex ones.

## Verification before handing off

Before giving your human partner any draft, scan the full text for:

- the emdash character: must be zero
- the en dash character: must be zero
- estimate ranges: each one either has "ish" or is a confirmed exact value
- intensifiers ("honestly", "genuinely", etc.): each one either adds real meaning or is cut; none used as reflex

If any check fails, fix it before your human partner sees the draft, not after.
