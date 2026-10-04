---
name: systematic-debugging
description: Use for a bug, a failing test or unexpected behaviour, before proposing a fix. Find the root cause first by reproducing it, reading the error, checking recent changes and testing one idea at a time.
---

# Systematic debugging

Find the cause before you change anything. A fix aimed at a symptom usually moves the bug somewhere else.

## 1. Look

- **Read the whole error**: message, stack, line numbers. For an unfamiliar tool or library, search the exact error text before reading source.
- **Reproduce it.** Find the shortest steps that trigger it every time. If you cannot reproduce it, gather more evidence; do not guess.
- **Check what changed**: recent commits, dependencies, config, environment.
- **In a chain of parts** (app, API, database, third party), find which link breaks: log what goes in and what comes out at each boundary, then dig into the one that fails. See `root-cause-tracing.md`.

## 2. Compare

Find similar code in the same repo that works. List every difference between it and the broken path, however small.

## 3. Test one idea

State it: "I think X is the cause because Y." Make the smallest change that would prove or disprove it. One variable at a time. If it is wrong, form a new idea; do not pile a second change on top.

## 4. Fix the cause

- Fix where the bad value or state starts, not where it surfaces.
- One change. No "while I'm here" edits.
- Add a regression test when the bug reached the owner or production, and name the bug in it.
- Run the check and confirm the original steps no longer fail.

## When to stop

After **three failed fixes**, stop. That pattern usually means the design is wrong, not the line. Tell the owner what you tried, what you saw each time, and what you now suspect.

## Signs you are guessing

"Quick fix for now", "just try changing X", several changes at once, proposing a fix before tracing the data, "one more attempt" after two failures. Go back to step 1.

## Supporting notes in this folder

- `root-cause-tracing.md`: trace a bad value back to where it starts.
- `defense-in-depth.md`: validate at more than one layer once the cause is found.
- `condition-based-waiting.md`: replace fixed timeouts with waiting on a condition (for flaky tests).
- `find-polluter.sh`: find which test leaves state behind that breaks another.
