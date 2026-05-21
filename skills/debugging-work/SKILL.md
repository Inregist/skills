---
name: debugging-work
description: Find and fix root causes. Use for bugs, failing tests, regressions, build failures, flaky behavior, performance problems, or unexpected technical behavior before proposing fixes.
---

# Debugging Work

No fixes before root cause investigation.

Debugging fails when the agent guesses, stacks fixes, or patches the symptom. Treat the failure as evidence to explain before editing.

## Gate

Do not propose or apply a fix until you can state:

```text
Failure: <exact observed failure>
Root cause hypothesis: <specific cause>
Evidence: <why this hypothesis fits>
```

## Loop

1. **Read the failure**
   - Read the exact error, stack trace, failing assertion, logs, or user report.
   - Preserve file paths, line numbers, commands, inputs, and environment details.

2. **Reproduce or gather evidence**
   - Run the failing command or identify exact reproduction steps.
   - If not reproducible, add focused logging/instrumentation or inspect state at component boundaries.
   - Do not guess when evidence can be gathered.

3. **Check what changed and what works**
   - Inspect recent diffs, config, dependencies, and nearby code.
   - Find a similar working example in the same codebase when possible.
   - Compare working vs broken behavior before editing.

4. **Form one hypothesis**
   - State one specific root-cause hypothesis.
   - Test one variable at a time.
   - If disproven, replace the hypothesis; do not pile on fixes.

5. **Fix the root cause**
   - Prefer a failing test or minimal reproduction before the fix.
   - Make one scoped change.
   - No unrelated refactor or “while here” cleanup.

6. **Verify the original failure**
   - Re-run the original failing check.
   - Run adjacent tests/checks when risk justifies it.
   - Add regression coverage when practical.

## Stop Rules

- If you do not understand the failure, say what is unknown and gather more evidence.
- If two fix attempts fail, stop and re-run root-cause investigation with the new evidence.
- If three fix attempts fail or each fix reveals a new coupled failure, stop and question the architecture before trying another fix.

## Output

```text
Failure: <what failed>
Root cause: <why>
Fix: <what changed>
Verified: <command/check>
Risk: <remaining gap>
```
