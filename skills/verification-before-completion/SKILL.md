---
name: verification-before-completion
description: Use before saying work is done, fixed or passing, and before committing or opening a pull request. Run the check, read its output, then state the result with the evidence.
---

# Verification before completion

Never say something works unless you ran the check in this session and read the result.

## The rule

1. Decide which command or observation proves the claim.
2. Run it in full, now.
3. Read the output: the exit code and the failure count, not just the last line.
4. Say what it shows, with the evidence. If it failed, say that.

| Claim | Proof |
| --- | --- |
| Tests pass | The test command's output showing 0 failures |
| Build or typecheck passes | That command exiting 0 |
| Bug fixed | The original failing steps now succeed |
| Screen looks right | A screenshot you looked at |
| A subagent finished the work | Its diff read by you, plus the check run by you |

A check that passed earlier and has had no code change since does not need running again.

## When it is not fully green

List every failing step by name. Run each one alone. Call it a flake only if it passes alone or fails the same way on the main branch, and quote that evidence. Never write "passes alone" without having seen it pass.

## Words that mean you have not checked

"Should work", "probably", "looks correct", "seems fine". Replace them with the check.
