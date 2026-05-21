---
name: verifying-work
description: Prove completion claims with fresh evidence. Use before saying work is done, fixed, passing, ready, or verified, and after code, docs, tests, configuration, or workflow changes.
---

# Verifying Work

Do not claim success before evidence.

## Gate

1. Name the claim: fixed, builds, tests pass, docs updated, UI works, skill valid.
2. Choose the smallest check that proves that claim.
3. Run or inspect the check fresh.
4. Read the result.
5. Report what is proven and what remains unverified.

## Check Types

- Code change: test, typecheck, lint, build, or focused reproduction.
- UI change: browser check, screenshot, accessibility or interaction check.
- Skill change: frontmatter present, description trigger clear, body concise, file path correct.
- Docs change: file exists, wording matches decision, no stale contradiction.

If no command exists, do a concrete manual check and say that it was manual.

## Output

Use this shape:

```text
Verified: <check and result>
Proves: <claim supported>
Remaining risk: <none or specific gap>
```
