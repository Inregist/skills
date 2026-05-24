---
name: commit-planner
description: Plan and write reviewable commits from a dirty worktree only when the user explicitly asks to commit. Use when the user says commit, asks for commit messages, or wants changes grouped for teammate review.
---

# Commit Planner

Do not commit until the user explicitly asks.

## Quick Start

1. Inspect `git status` and the diff.
2. Separate unrelated work.
3. Group commits by reviewer understanding, not by file type.
4. Prefer multiple commits when it makes review easier.
5. Use concise Conventional Commits messages.
6. Report what was committed and what remains dirty.

## Grouping Rules

- One behavior or decision per commit.
- Do not mix formatting, refactor, docs, and behavior unless inseparable.
- Do not stage untracked/user files without checking intent.
- Do not hide unrelated changes in a broad commit.

## Message Shape

```text
<type>(optional-scope): <imperative summary>
```

Body only when the reason is not obvious.
