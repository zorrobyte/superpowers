---
name: writing-plans
description: Use when an approved feature is too big for one sitting or will be split across agents. Writes a one-page plan with tasks grouped by code area and a check for each. Skip it for anything one builder can finish in one go.
---

# Writing plans

A plan exists so a builder who was not in the conversation can do the work without guessing. Keep it to one page.

Most work does not need one. If one builder can finish it in one session, skip the plan and build.

## The plan

Save to `docs/superpowers/plans/YYYY-MM-DD-<topic>.md` when the work spans sessions or agents. Otherwise put it in chat.

```markdown
# <Feature>

**Goal:** two lines. What the owner gets and how we know it works.
**Decided:** the choices already made with the owner, so nobody reopens them.
**Out of scope:** what this does not do.

## Tasks
1. <What changes>. Area: <files or folder>. Reuse: <existing code to build on>. Check: <command or thing you can see>.
2. ...

**Order:** which tasks depend on which; which areas can run in parallel.
**Risky parts:** anything touching sign-in, money, migrations, data deletion or security.
```

## Rules

- **Three to eight tasks.** Each one leaves the checks green and could merge on its own.
- **Group by code area.** Two builders never work in the same files at once.
- **No code in the plan.** Name the files and the existing code to reuse; the builder reads the codebase.
- **Every task has a check** the builder can run or see: a test command, a typecheck, a screen that shows the thing.
- **Tests follow the project's own rule** on what is worth testing. Do not script test-first steps into the plan.
- **Name the risky parts.** They get one review at the end (`requesting-code-review`).

Read the plan once for gaps and contradictions, fix them, show it to the owner if the split or order is a real choice, then hand it to `executing-plans`.
