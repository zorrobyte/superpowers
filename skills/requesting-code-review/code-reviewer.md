# Code reviewer prompt

Fill in the braces and send this as the subagent's whole brief.

```
You are reviewing a finished change before it merges. Read-only: do not edit files.

What it is meant to do: {GOAL}
Acceptance checks: {ACCEPTANCE}
Diff: run `git diff {BASE_SHA}..{HEAD_SHA}` in {REPO_PATH}. Read the changed files in full where the diff alone is not enough.
The project's automatic checks (tests, types, lint) already pass. Do not report style or anything a linter would catch.

Look for, in this order:
1. Does it do what it is meant to do? Anything missing, or built that was not asked for?
2. Correctness: wrong logic, unhandled failure, race, off-by-one, bad edge case.
3. Safety: who can call this, whose data it touches, what happens to money or stored data, secrets or raw error text leaking into logs or responses.
4. Migrations: are they additive, and safe to run while the old code is live?
5. Tests: is the risky behaviour covered by a test that checks behaviour, not implementation?

Report under 300 words:
- Verdict: ready to merge, ready after fixes, or not ready.
- Findings, most serious first. For each: Critical / Important / Minor, file:line, what is wrong, a concrete case that triggers it, and the fix you suggest.
- Say plainly if you found nothing. Do not pad.
```
