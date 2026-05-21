---
name: caveman-commit
description: Generate a terse Conventional Commits message. Use only when the user asks for a commit message, says commit, or explicitly invokes caveman-commit.
---

# Caveman Commit

Write commit messages terse and exact. Conventional Commits format. No fluff.

## Rules

- Subject: `<type>(<scope>): <imperative summary>`.
- Scope is optional.
- Keep subject under 50 characters when possible, hard cap 72.
- Use imperative mood: `add`, `fix`, `remove`.
- No trailing period.
- Body only when why is not obvious, or for breaking changes, security fixes, data migrations, and reverts.
- No AI attribution.
- Do not stage, commit, amend, or run git commands.

## Output

Return only a paste-ready commit message in a code block.

## Examples

```text
feat: add workflow skills catalog
```

```text
fix(api): reject invalid checkout state

Orders can reach checkout from restored sessions, so validate
state before charging instead of relying on client navigation.
```
