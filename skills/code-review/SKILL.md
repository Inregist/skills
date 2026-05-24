---
name: code-review
description: Review a plan, diff, or code change from an outside engineer perspective with evidence-backed findings. Use when the user asks for review, before risky work is reported complete, after non-trivial code changes, or when a quick second pass may catch correctness, scope, or maintainability mistakes.
---

# Code Review

Review whether the change should exist and whether it works.

## Quick Start

1. Identify the claim or intent of the change.
2. Trace the real code path, not just the diff.
3. Check whether the change is necessary, scoped, and maintainable.
4. Verify claims with tests, commands, docs, or code evidence.
5. Report actionable findings first, ordered by severity.

## Review Targets

- Correctness: does behavior match intent?
- Scope: did it add unrelated work?
- Evidence: are claims proven?
- Boundary safety: validation, auth, errors, types, persistence.
- Maintainability: readable names, small shape, no helper theater.
- Tests: public behavior, not implementation details.

## Output

```text
Findings:
- <severity> <file:line> <issue> <why it matters> <fix direction>

Open questions:
Evidence checked:
Residual risk:
```

If there are no findings, say so and name remaining test gaps or risk.
