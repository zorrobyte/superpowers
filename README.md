# Superpowers (lean fork)

A cut-down fork of [obra/superpowers](https://github.com/obra/superpowers) for one owner working with Claude Code on a single Mac.

The upstream plugin is built around heavy process: a start-up message that pushes a skill on every request, a fresh subagent and a reviewer for every task, and fix-and-re-review loops. With current models and a fast automatic check suite, that costs far more tokens than it saves. This fork keeps the ideas that still pay and drops the rest.

## What is here

Six skills, each short, none loaded until used. No hooks, no start-up text.

| Skill | Use it for |
| --- | --- |
| `brainstorming` | Fuzzy features and design decisions: one question at a time, options with a recommendation, optional browser whiteboard |
| `writing-plans` | A one-page plan when work spans sessions or agents |
| `executing-plans` | Building with one builder, reuse before writing, checks as you go |
| `systematic-debugging` | Root cause before fix; stop after three failed fixes |
| `verification-before-completion` | No "done" without the check output |
| `requesting-code-review` | One review of the final diff, for risky changes only |

## What was removed

- The SessionStart hook and `using-superpowers` (the "you must use a skill" bootstrap).
- `subagent-driven-development`: per-task builders, per-task reviewers and five-round fix loops.
- `test-driven-development`, `using-git-worktrees`, `finishing-a-development-branch`, `dispatching-parallel-agents`, `receiving-code-review`: covered by the project's own rules.
- `writing-skills`, `diagnosing-superpowers`, and support for other tools (Codex, Cursor, Gemini and others).

## Install

    claude plugin marketplace add zorrobyte/superpowers
    claude plugin install superpowers@zorrobyte

## Updating from upstream

`main` tracks upstream; the lean version lives on `lean` (the default branch). The skills here are rewrites, so take ideas from upstream by hand rather than merging. The one thing worth pulling is `skills/brainstorming/scripts` and `visual-companion.md` (the whiteboard server), which are unchanged:

    git fetch upstream && git checkout upstream/main -- skills/brainstorming/scripts skills/brainstorming/visual-companion.md

MIT licensed, as upstream. Original work by Jesse Vincent.
