---
name: routing-work
description: Choose the lightest workflow for a task. Use after intent is clear and before non-trivial work, especially when deciding whether to act directly, load a focused skill, ask for design, or use a heavier process.
---

# Routing Work

Pick the smallest workflow that can succeed.

## Modes

**FAST**: intent is clear and risk is low. After the intent check, load no other workflow skill by default. Inspect only needed context, act, verify lightly.

**DISCIPLINE**: clear task that needs one focused gate: bug/failure, clear multi-step implementation, slop-prone execution, test-first behavior work, proof, or specialized workflow. Load one primary skill, follow its gate, verify.

**HEAVY**: ambiguous, risky, broad, or design-heavy work. Discover context first, resolve costly ambiguity, then plan only if needed.

## Decision

1. Use `intent` as the cheap preflight when the request might be solved at the wrong level.
2. If intent is clear and the task is tiny and reversible, choose FAST.
3. If there is a bug, failure, regression, or unexplained technical behavior, choose DISCIPLINE -> `debugging-work`.
4. If the user explicitly asks for TDD/test-first work, choose DISCIPLINE -> `tdd`.
5. If the task is clearly frontend implementation or review, choose DISCIPLINE -> `frontend-engineer`.
6. If the task is clearly backend/API/data implementation or review, choose DISCIPLINE -> `backend-engineer`.
7. If clear work has multiple ordered steps and no role skill fits better, choose DISCIPLINE -> `planning-work`.
8. If implementation is likely to drift, overbuild, or ignore scope, choose DISCIPLINE -> `karpathy-guidelines`.
9. If the claim needs proof before you say it, choose DISCIPLINE -> `verifying-work`.
10. If one skill directly prevents likely failure, choose DISCIPLINE.
11. If wrong work would be costly because scope, design, domain language, or risk is unclear, choose HEAVY -> `discovering-context`.
12. Prefer zero or one primary skill. For mixed full-stack work, pick the riskiest side first and add the other role only when crossing that boundary.

`tdd` is an ACT support method for behavior changes. Do not route bugs straight to `tdd` before root cause, and do not use `tdd` as final proof; `verifying-work` owns completion claims.

## Output

State briefly:

- mode;
- primary skill after intent, or `none`;
- first next gate: `act`, `context`, `decide`, `plan`, `execute`, `debug`, or `verify`.

Do not load skills just because they might apply. Load them when they change the next action.
