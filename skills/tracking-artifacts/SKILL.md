---
name: tracking-artifacts
description: Use when your human partner needs to track an ongoing, multi-part effort - a project, a sprint, a formation checklist, an ops backlog. Builds a persistent, cross-device interactive tracker artifact that holds non-linear state, with categorized ticket IDs and the Nominal aesthetic.
---

# Tracking Artifacts

## Overview

A tracking artifact is an interactive artifact, usually React, that holds the state of an ongoing effort and survives across sessions and devices. The genre includes the Spicy Brain Translation Bureau, the Homelab Arcade, and the Nominal Industries Ops Desk.

Its real job is the same one `sbtb` does: it lets your human partner record progress without first converting non-linear work into a linear list. Several parades are tracked at once, in parallel categories, and they update whichever one moved without linearizing anything. The artifact holds the structure so their brain does not have to.

## When this triggers

Fires when your human partner needs to track an ongoing, multi-part effort and would benefit from a live artifact rather than a static list: project trackers, sprint boards, formation or setup checklists, ops backlogs, anything they will return to repeatedly.

## How to build one

1. **Use persistent storage.** Build it with the artifact storage API (`window.storage`) so state survives a closed tab and follows them across devices. This is the feature that makes the genre work. Without it the tracker resets and is useless.
2. **Know the cross-device caveat.** Storage persists per account, but an artifact loads from storage on open and instances do not live-sync with each other. Check off on phone, close it, open on desktop, the change is there. Two instances open at once is last-write-wins. Tell your human partner this so they refresh on a device switch.
3. **Categorized ticket IDs are mandatory.** Every trackable item gets an ID with a category prefix and a number: `LLC-001`, `DOM-002`, `MX-003`. This is a hard rule learned the hard way. Without it, referring to work becomes "that one thing in the middle of the list", which is exactly the failure the tracker exists to prevent. The IDs also let `sbtb` map items to real org tickets cleanly.
4. **Organize into parallel categories.** Group items into epics or sections, each independently collapsible. Parallel categories are how the artifact holds parallel parades. Give each a short playful tagline in the Businessverse register ("Dept. of Incorporation", "The Boss Fight"), it costs nothing and your human partner enjoys it.
5. **Clear status states.** Each item shows an unambiguous state. Default to three: todo, in progress, done, each with a distinct icon, readable at a glance. Add a further state like blocked only when the work actually has it, see "Status states: start with three, earn the rest" below.
6. **Let items be added and removed in-app.** The tracker is living. Your human partner adds tickets and clears them without editing code.
7. **Nominal aesthetic.** Dark, industrial, utilitarian, with a restrained accent color. It should look like a piece of equipment, not a consumer to-do app.

## Surviving your own edits

A tracker is not built once. You will change its structure while it is in use, adding tickets, renaming categories, regrouping. The saved state in `window.storage` has to survive that. Two techniques, both mandatory.

1. **Version the storage key.** Use a key like `tracker-name-v1`. When you change the task structure in a way that old saved state cannot map onto cleanly, bump it to `-v2` and re-seed. A stale state blob loading into a changed structure either collides or silently drops items. The version bump is the clean break.
2. **Seed from known state, not from empty.** On a fresh load with no saved data, do not start blank. Seed the tracker with where the effort actually is right now, items already done marked done, in-progress marked in progress. The tracker should open reflecting reality. A blank tracker on first open makes your human partner redo state they already reported.

When you bump the version, re-seed from the latest state your human partner gave you. Ask them if you are not sure. A screenshot is the fastest way for them to tell you.

## Two storage bugs that will eat state

Both of these have actually happened. Guard against both.

1. **The empty-state clobber.** The save effect runs on the initial render, when state is still the empty default, before the load from storage has finished. It writes `{}` over real saved data. Guard the save effect: never save before the initial load has completed, and never save an empty state. This is the bug most likely to silently destroy your human partner's progress.
2. **The remount race.** Updating the artifact remounts the component. The load starts, and the save effect can fire on default state before the load resolves. Same fix: a `loaded` flag that gates all saves, set true only after the load attempt finishes.

## Screenshot reconciliation

The tracker will drift from reality. Your human partner checks things off, forgets which, closes the tab. When that happens, the fastest path back in sync is a screenshot. They snap a picture of the tracker, you read the states off it, you re-seed. This is a normal part of the workflow, not a failure. Tell your human partner it is an option, especially for the "I tapped a bunch of things and do not remember which" case.

## Status states: start with three, earn the rest

Default to three states: todo, in progress, done. Tap to cycle through them. For many trackers that is the whole set and adding more just makes every update a bigger decision.

Add a state only when a real one exists in the work. An ops backlog that genuinely stalls on external dependencies needs a blocked or waiting state, so add it. A solo serial project where nothing ever blocks does not, so do not. Match the state set to the actual shape of the work. Every extra state is another choice your human partner makes on every item, and a tracker that is tedious to update stops getting updated.

## Item metadata tags

Tasks often carry a dimension beyond their status. Tag it. The right tags are not universal, they depend on how this particular person sorts their work, so ask what dimension they actually navigate by.

Examples that have earned their place:

- An energy tag (a "couch" tag) marking low-effort items. This is an activation tool, not an effort cap. The hardest part of a task is starting it, and on a low-energy day a tracker with no visible easy entry point yields no progress at all. The couch tag guarantees there is always a startable item in view, so a tired-but-wanting-to-work state can still become a couch-task state instead of a no-progress one. It keeps the entry point from ever being empty.
- An optional or stretch tag separating committed work from nice-to-have.
- A context or client tag, for someone juggling many parallel contexts.

Do not prescribe a fixed tag set. Find the one or two dimensions that are load-bearing for this person and tag those.

## Non-task panels

A tracker is sometimes more than its task list. The Homelab Arcade carries hardware inventory, an incoming-gear panel, a sell pile, a wishlist, none of them task lists, all of them things the effort needs visible. If an effort has reference data that lives alongside the work, give it its own panel. This is optional and effort-dependent, not every tracker needs it, but look for it.

## Red flags

| Symptom | What it means |
|---|---|
| The tracker uses React state with no `window.storage` | It resets on close. The whole point is persistence. |
| Items have no categorized ticket IDs | "That thing in the middle of the list" is back. Add prefixed IDs. |
| Everything is one flat list | Parallel categories are how it holds parallel parades. |
| You promised live multi-device sync | It is not live. Last-write-wins. Set the expectation. |
| Status is ambiguous or text-only | Give each state a distinct icon, readable at a glance. |
| It looks like a generic consumer to-do app | Wrong register. Dark, industrial, Nominal. |
| The save effect has no loaded-state guard | It writes empty default state over real saved data on mount. Gate saves behind a load-complete flag. |
| Storage key is unversioned | A later structure change cannot be cut cleanly from old state. Version the key, bump on structural change. |
| Fresh load starts blank | Seed from known current state so the tracker opens reflecting reality. |
| Five-plus status states | Every state is a decision on every item. Start with three, add only states the work actually has. |

## Rationalizations to reject

- "Browser storage in artifacts is unreliable, I will use React state." The persistent storage API is the feature that defines this genre. Use it.
- "Simple sequential numbers are fine for IDs." Category prefixes are the lesson. `DOM-002` survives reordering and is referable. `7` is not.
- "One list is simpler than categories." One list cannot hold parallel parades. Categories are the structure.
- "I will add the storage version later if I need it." You will need it the first time you restructure, and by then there is state to lose. Version from the start.
- "The save effect is fine, it only runs on change." It also runs on the initial empty render. Without a guard it clobbers saved data before the load finishes.

## Notes

The artifact storage API has a documented contract: keys under 200 characters with no whitespace or slashes, values under 5 MB, last-write-wins on concurrent updates. Batch related data into single keys rather than many small ones. Always wrap storage calls in error handling and show a loading state while data arrives.
