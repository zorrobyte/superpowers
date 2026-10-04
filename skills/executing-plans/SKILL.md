---
name: executing-plans
description: Use to build an approved design or plan. One builder works through the tasks in order, runs the project's checks as it goes, and gets a single review at the end only when the change is risky.
---

# Executing plans

Build the agreed thing with the fewest handoffs. Every new agent starts cold and re-reads everything, so handoffs are the main cost.

## Who builds

- **Small or medium work:** the main session builds it. No subagent.
- **A substantial multi-file build:** one subagent for the whole plan, or one per code area when areas are independent. Name its model explicitly (a mid-tier model; a stronger one only after a mid-tier one has failed twice).
- **Never** a new agent per task, a reviewer per task, or two agents in the same files.

A subagent brief has: the goal, the plan or spec path, the files to read first, what is already decided, the check to run, and "report in under 200 words: what changed, check output, anything you could not do".

## For each task

1. Read the code you are about to change and what calls it.
2. **Reuse before you write.** In order: does this need to exist, is it already in the codebase, does the standard library or platform do it, does an installed package do it. Only then write the minimum that works.
3. Make the change. Match the surrounding code.
4. Run the related tests and the typecheck. Fix what you broke.
5. Commit the task.

## When a check fails

Use `systematic-debugging`: find the cause, make one fix, run the check again. If it still fails after a second, different attempt, stop and report what you tried and what you saw. Do not loop.

## When the plan is wrong

Stop and say so. Do not quietly build something else, and do not build a plan you can see will not work.

## Finishing

1. Run the project's full check once and read the output (`verification-before-completion`).
2. If the change touches sign-in, money, migrations, data deletion or security, get one review of the final diff (`requesting-code-review`). Otherwise none.
3. Follow the project's own rules for branches, pull requests and merging.
4. Report plainly: what was built, the check result, anything left undone.
