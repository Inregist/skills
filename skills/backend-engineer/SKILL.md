---
name: backend-engineer
description: Build and review backend, API, and data work with clear request flow, validation, auth, domain rules, persistence, and production safety. Use when working on APIs, server handlers, services, database schema, migrations, auth, permissions, or backend infrastructure; apply engineering-discipline inline and use debug-discipline, tdd, or code-review when concrete risk exists.
---

# Backend Engineer

Own server correctness from boundary input to durable side effects.

## Baseline

Apply `engineering-discipline` inline: make the smallest readable change that solves the request, use existing primitives first, and avoid known coding anti-patterns.

Do not load those skills separately unless the next action needs their full checklist.

## Work Loop

1. Inspect the contract, handler, service, query, schema, auth, and tests near the change.
2. Use existing project, framework, validation, auth, database, and runtime primitives before adding new code.
3. Validate boundary input with the project's schema tool.
4. Resolve auth/session and authorize server-side for the action.
5. Keep request flow visible: input, auth, domain decision, DB or external side effect, typed result.
6. Verify with behavior tests, typecheck, lint, build, migration checks, or a focused reproduction.

## Backend Standards

- Use domain names for procedures, services, queries, errors, and variables.
- Add services or query helpers only when they clarify rules, transactions, permissions, reuse, or failure modes.
- Avoid generic repository, base CRUD, mapper, and pass-through layers.
- Keep DB writes, transactions, constraints, and state transitions explicit.
- Never trust client roles, access flags, hidden form state, or client-side validation.
- Return user-safe typed errors; keep technical detail in logs or dev-only surfaces.
- Treat migrations, data deletion, public APIs, auth, env/secrets, and real-user data formats as production-sensitive.

## Review Gate

- Can a teammate trace request to response and name the invariants?
- Are auth, authorization, validation, writes, and errors visible?
- Did existing backend primitives cover solved behavior?
- Did code quality improve without adding unnecessary layers?
- Did verification cover data, permissions, or production risk?
