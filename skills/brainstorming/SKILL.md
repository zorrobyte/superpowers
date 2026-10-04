---
name: brainstorming
description: Use for a new feature, a redesign, or a fuzzy product or design decision that needs thinking through with the owner. Asks one question at a time, offers options with a recommendation, and can show mockups on a browser whiteboard. Not for bug fixes, clear instructions or small changes.
---

# Brainstorming

Turn a fuzzy idea into a design the owner recognizes and has agreed to, with as little ceremony as the idea needs.

Skip this skill for bugs, clear instructions and small fixes: just do those.

## Size it first

Say which size you picked, in one line, so the owner can correct you.

- **Question** ("can we...", "is it possible..."): say what you will try in two sentences, find out as cheaply as you can, report a recommendation. Anything you built to find out is throwaway.
- **Small change** to a flow that already exists in the repo: ask only the questions that change the answer, describe the approach in a few sentences in chat (what changes, which files), wait for a yes, then build.
- **Big** (a new feature, a redesign, a change to how parts fit together): the full flow below.

If a small change turns out to be big, stop and say so.

## The full flow

1. **Read first.** Look at the code and docs the idea touches before asking anything.
2. **Say back what you understood** in three or four lines: the goal, who it is for, what success looks like. Mark what the owner said apart from what you assumed.
3. **Ask one question per message.** Multiple choice when you can. Only ask what would change the design; stop asking when the answers stop changing it.
4. **Offer two or three approaches.** Recommended one first, with the reason, in plain words. Cut everything the goal does not need.
5. **Present the design in short sections** (a few sentences each; more only where it is subtle). Check after each: "does this look right?"
6. **Get one clear yes.** That yes covers the design; do not ask again at every later step.

Explain at the owner's level. No jargon without a plain-words gloss.

## What gets written down

- Work that fits one session with one builder: the chat is the spec. Write nothing.
- Work that spans sessions or agents: one page at `docs/superpowers/specs/YYYY-MM-DD-<topic>.md` with the goal, the decisions made, what is out of scope, and the acceptance checks. Then use `writing-plans` if it needs splitting into tasks.

No spec review rounds. Read it once yourself for gaps and contradictions, fix them, and move on.

## Visual companion (the whiteboard)

A browser tab for showing mockups, layouts and diagrams side by side. It is a tool, not a mode.

- **Offer it only when a question is really visual** (which layout, which screen, which flow), not just because the topic is UI. Offer it in its own message, the first time it would help: "This would be easier to show. I can put mockups in a browser tab as we go. It uses more tokens. Want me to?"
- If the owner says yes, read `visual-companion.md` in this skill's folder and start the server with `--open`.
- After that, decide per question: show visual things in the browser, ask text questions in the terminal.
- If the owner says no, carry on in text and do not offer again unless they bring it up.
