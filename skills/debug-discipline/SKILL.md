---
name: debug-discipline
description: Diagnose bugs and failures by finding root cause before fixing. Use when handling bugs, regressions, flaky behavior, failing tests, build errors, runtime errors, unexpected output, or when a previous fix did not work.
---

# Debug Discipline

No fix before evidence.

## Quick Start

1. Read the exact error, failing output, or user-visible symptom.
2. Reproduce or identify why it cannot be reproduced yet.
3. Inspect recent changes and nearby working examples.
4. Trace the failing path across each boundary.
5. Form one root-cause hypothesis from evidence.
6. Try to falsify the hypothesis before fixing.
7. Make the smallest fix that addresses the cause.
8. Verify the original failure path.

## Evidence Rules

- Do not patch from vibes.
- Do not fix multiple hypotheses at once.
- Do not hide the failure with defaults or broad catch blocks.
- If the failure crosses layers, inspect each boundary: input, state, config, call, output.
- Keep a short breadcrumb ledger: observed fact, file/line or command, implication.
- If evidence contradicts the hypothesis, update the hypothesis instead of forcing the fix.

## Output

```text
Failure:
Evidence:
Breadcrumbs:
Hypothesis:
Fix:
Verification:
Remaining risk:
```
