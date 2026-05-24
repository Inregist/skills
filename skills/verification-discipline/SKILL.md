---
name: verification-discipline
description: Prove completion claims with fresh evidence. Use when preparing to say work is done, fixed, passing, working, ready, safe, or verified; or after code, docs, config, tests, workflow, or plugin changes.
---

# Verification Discipline

Do not claim success before evidence.

## Quick Start

1. Name the exact claim.
2. Choose the smallest check that can prove that claim.
3. Run or inspect the check fresh.
4. Read the result.
5. Report what is proven and what remains unverified.

## Match Claim To Proof

- Code behavior: focused test, reproduction, typecheck, lint, build, or manual check.
- UI behavior: browser interaction, screenshot, responsive check, or accessibility check.
- Plugin shape: manifest and skill validation.
- Docs: file exists, wording matches the decision, stale contradictions removed.
- Commit state: current git status and log.

Narrow checks prove narrow claims only.

## Output

```text
Verified:
Proves:
Remaining risk:
```
