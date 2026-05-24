---
name: engineering-discipline
description: Guide code execution toward small, readable, maintainable changes and prevent common agent slop. Use when writing or refactoring code, when implementation may drift or overbuild, when readability and simplicity matter, or when past anti-patterns are likely.
---

# Engineering Discipline

Code like a maintainable teammate.

## Quick Start

1. Keep the change as small as readability allows.
2. Use existing project patterns and primitives first.
3. Make every changed line trace to the user goal.
4. Prefer clear domain names over comments or cleverness.
5. Pick verification before claiming completion.

## Anti-Patterns

Avoid these unless the codebase already uses the pattern or the runtime fact is explicit:

- Type escape: `as any`, broad `as Type`, non-null assertions, or `@ts-ignore`.
  Prefer typed boundaries, schemas, generics, unions, or local narrowing.
- Validation gymnastics: long `typeof`/`in` chains for object shapes.
  Prefer existing schema/type validators such as Zod or project helpers.
- Fake fallback: `?? []`, `|| ""`, empty objects, or catch-and-ignore.
  Only fallback when product behavior requires it.
- Helper theater: one-use helpers, wrappers, factories, or services.
  Keep logic local until reuse or complexity is real.
- Lookup branching: `switch`/`if` chains for static key lookup.
  Prefer typed object tables with `satisfies Record<Key, Value>`.
- State mirroring: duplicate server, query, form, or derived state.
  Keep one source of truth.
- Effect abuse: React effects for derived values or event work.
  Derive in render; do event work in handlers.
- Fake tests: private functions, call counts, or mocks of internals.
  Test public behavior.

## Review Gate

- Is this the smallest readable change?
- Did existing primitives cover solved behavior?
- Are types and validation honest?
- Did the check prove the changed behavior?
- Are risks or unverified parts stated?
