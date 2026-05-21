---
name: karpathy-guidelines
description: Prevent common LLM coding slop with surgical, minimal, verifiable changes. Use when writing, reviewing, or refactoring code, especially when implementation may overbuild, drift from scope, invent abstractions, or hand-roll solved behavior.
---

# Karpathy Guidelines

Solve the asked problem with the least code that remains easy to read.

Every changed line should trace to the user's goal.

## Before Coding

- State assumptions only when they affect behavior or risk.
- Ask when ambiguity affects product behavior, data model, public API, security, irreversible action, or architecture.
- Prefer the simpler direct approach unless existing code clearly needs a boundary.
- Define success with a concrete check: test, typecheck, lint, build, reproduction, or manual behavior check.

## Simplicity Rules

- Do not add features, modes, config, options, or fallback behavior that was not requested.
- Do not create files, hooks, services, utilities, wrappers, or tiny functions for one-use code.
- Use platform, framework, package, and project primitives for solved domains.
- Do not hand-roll solved behavior unless no suitable primitive exists or the user explicitly asks.
- If hand-rolling is necessary, state the reason briefly.

## Surgical Changes

- Touch only files needed for the request.
- Match nearby style, naming, and boundaries.
- Do not refactor adjacent code, reformat unrelated blocks, or delete unrelated dead code.
- Remove only unused code created by your change.
- If the solution grows beyond the smallest readable shape, simplify before finishing.

## Review Gate

Before done, check:

- Is this the minimum readable code that achieves the goal?
- Did every changed line serve the request?
- Did existing primitives cover solved behavior?
- Did verification prove the requested behavior?
- Are assumptions, risks, or unverified parts stated?
