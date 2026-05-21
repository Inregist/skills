---
name: routing-work
description: Choose the lightest workflow for a task. Use after intent is clear and before non-trivial work, especially when deciding whether to act directly, load a focused skill, ask for design, or use a heavier process.
---

# Routing Work

Pick the smallest workflow that can succeed.

## Modes

**FAST**: intent is clear and risk is low. After the intent check, load no other workflow skill by default. Inspect only needed context, act, verify lightly.

**DISCIPLINE**: clear task that needs one focused gate: bug/failure, clear multi-step implementation, proof, or specialized workflow. Load one primary skill, follow its gate, verify.

**HEAVY**: ambiguous, risky, broad, or design-heavy work. Discover context first, resolve costly ambiguity, then plan only if needed.

## Decision

1. Use `intent` as the cheap preflight when the request might be solved at the wrong level.
2. If intent is clear and the task is tiny and reversible, choose FAST.
3. If there is a bug, failure, regression, or unexplained technical behavior, choose DISCIPLINE -> `debugging-work`.
4. If clear work has multiple ordered steps, choose DISCIPLINE -> `planning-work`.
5. If the claim needs proof before you say it, choose DISCIPLINE -> `verifying-work`.
6. If one skill directly prevents likely failure, choose DISCIPLINE.
7. If wrong work would be costly because scope, design, domain language, or risk is unclear, choose HEAVY -> `discovering-context`.
8. Prefer zero or one primary skill. Add supporting skills only when the next step needs them.

## Output

State briefly:

- mode;
- primary skill after intent, or `none`;
- first next gate: `act`, `context`, `decide`, `plan`, `debug`, or `verify`.

Do not load skills just because they might apply. Load them when they change the next action.
