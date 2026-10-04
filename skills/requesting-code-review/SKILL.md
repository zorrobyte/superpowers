---
name: requesting-code-review
description: Use before merging a risky change (sign-in, money, migrations, data deletion, security) or when the owner asks for a review. One independent reviewer reads the final diff once.
---

# Requesting code review

One fresh pair of eyes on the finished change, for changes where a mistake is expensive.

## When

- **Review:** changes to sign-in or permissions, billing or anything that moves money, database migrations, deleting data, secrets or security, and anything the owner asks to have reviewed.
- **No review:** docs, copy, small fixes, and changes the project's automatic checks already cover. Never one review per task.

## How

1. Finish the work and run the project's full check first. A reviewer should not spend effort on what the checks catch.
2. Start one subagent with the prompt in `code-reviewer.md`. Name its model explicitly: mid-tier for most changes, the strongest for subtle ones (concurrency, money math, permissions).
3. Give it the diff range, what the change is meant to do, and the acceptance checks. Do not give it your own conclusions; you want a read that is not anchored on yours.

## Acting on the findings

- Check each finding against the code before acting. Reviewers are sometimes wrong.
- Fix what is Critical or Important. Note Minor items; fix them only if cheap.
- One fix pass, then run the checks. Ask for a second review only if the fix itself touched the risky part.
- If you disagree with a finding, say why with evidence instead of silently skipping it.
