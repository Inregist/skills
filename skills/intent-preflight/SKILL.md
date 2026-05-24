---
name: intent-preflight
description: Understand the user's real intent and choose the next behavior before acting. Use when starting non-trivial coding, debugging, planning, review, or workflow requests; when the user is vague, frustrated, corrective, or thinking aloud; or when the request may be solved at the wrong level.
---

# Intent Preflight

Use this as the front door for non-trivial work.

## Quick Start

1. Infer the intended outcome, not just the literal instruction.
2. Identify whether the user needs action, explanation, diagnosis, decision, planning, or handoff.
3. Inspect available repo evidence before asking if evidence can answer.
4. Choose the smallest next behavior that avoids wrong work.
5. Ask only when choosing wrong would waste work or violate the goal.

## Path Choice

- Direct action: intent clear, low risk, reversible.
- Inspect evidence: repo/docs/tests can answer before asking.
- Interview: work is big, ambiguous, costly, or user is thinking aloud.
- Plan: intent clear, implementation has multiple visible steps.
- Debug: bug, failure, regression, flaky behavior, or unexpected output.
- Execute: code change is scoped and ready.
- Verify: user asks whether something is done/fixed/working.
- Handoff: session state must transfer.

## Output

Keep it short:

```text
Intent: <real outcome>
Next: <path and why>
```

State this only when it helps the user steer. Otherwise proceed with the chosen behavior.
