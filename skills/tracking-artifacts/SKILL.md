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
5. **Clear status states.** Each item shows an unambiguous state, done, blocked, in progress, each with a distinct icon. State should be readable at a glance.
6. **Let items be added and removed in-app.** The tracker is living. Your human partner adds tickets and clears them without editing code.
7. **Nominal aesthetic.** Dark, industrial, utilitarian, with a restrained accent color. It should look like a piece of equipment, not a consumer to-do app.

## Red flags

| Symptom | What it means |
|---|---|
| The tracker uses React state with no `window.storage` | It resets on close. The whole point is persistence. |
| Items have no categorized ticket IDs | "That thing in the middle of the list" is back. Add prefixed IDs. |
| Everything is one flat list | Parallel categories are how it holds parallel parades. |
| You promised live multi-device sync | It is not live. Last-write-wins. Set the expectation. |
| Status is ambiguous or text-only | Give each state a distinct icon, readable at a glance. |
| It looks like a generic consumer to-do app | Wrong register. Dark, industrial, Nominal. |

## Rationalizations to reject

- "Browser storage in artifacts is unreliable, I will use React state." The persistent storage API is the feature that defines this genre. Use it.
- "Simple sequential numbers are fine for IDs." Category prefixes are the lesson. `DOM-002` survives reordering and is referable. `7` is not.
- "One list is simpler than categories." One list cannot hold parallel parades. Categories are the structure.

## Notes

The artifact storage API has a documented contract: keys under 200 characters with no whitespace or slashes, values under 5 MB, last-write-wins on concurrent updates. Batch related data into single keys rather than many small ones. Always wrap storage calls in error handling and show a loading state while data arrives.
