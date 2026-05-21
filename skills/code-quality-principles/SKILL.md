---
name: code-quality-principles
description: Apply practical code-quality principles as a lightweight design and review checklist. Use when reviewing, refactoring, or designing code where maintainability, robustness, testability, security, abstraction, coupling, dependency direction, or SOLID tradeoffs matter.
---

# Code Quality Principles

Use this to make code cheaper to change, safer to run, and easier to understand.

## Fast Pass

1. Name the quality risk: incorrect behavior, unclear intent, weak tests, fragile input handling, stale docs, coupling, over-abstraction, globals, concurrency, or security.
2. Pick the smallest change that reduces that risk.
3. Match local style and existing project primitives.
4. Verify with the narrowest meaningful check.

## Checklist

- Verify behavior from the caller or user point of view, especially for user-facing or concurrent changes.
- Follow local code specifications before personal preference.
- Use precise names before comments; update docs when build, test, use, release, or API behavior changes.
- Comment why a non-obvious choice exists; do not narrate obvious code.
- Handle boundary inputs, failures, and unexpected states deliberately.
- Add or adjust useful tests that would fail for the bug or risk; keep test code maintainable.
- Keep components easy to test by reducing hidden state, wide dependencies, and hard-to-reach branches.
- Check async, concurrency, retries, ordering, and side effects for races, deadlocks, duplicate writes, and leaks.
- Use moderate abstraction: hide real complexity, not simple control flow.
- Use design patterns only when the problem already matches the pattern.
- Prefer local state, parameters, and pure functions over globals and shared mutation.
- Refactor when it removes real debt from the current change path.
- Treat security, validation, authorization, safe errors, logs, secrets, and data exposure as design constraints.

## SOLID Pass

- Single Responsibility: split code only when different reasons to change are tangled.
- Open/Closed: add an extension point only for real or imminent variation.
- Liskov Substitution: implementations must honor caller expectations without special cases.
- Interface Segregation: depend on only the methods the caller needs.
- Dependency Inversion: business rules depend on stable contracts; adapters depend on external details.

## Guardrails

- Do not add interfaces, factories, inheritance, layers, or config without current pressure.
- Prefer a small direct function when there is only one behavior.
- Do not refactor adjacent code just because it is imperfect.
- Delete or inline abstractions that no longer protect a real change axis.
