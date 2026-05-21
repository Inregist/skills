---
name: frontend-engineer
description: Build and review frontend features with clear render flow, state ownership, accessibility, and production UI behavior. Use when working on routes, React components, forms, client state, API consumption, or frontend feature slices; apply karpathy-guidelines inline and route to frontend-design, Vercel React skills, web-design-guidelines, or playwright-cli only when that risk exists.
---

# Frontend Engineer

Own the user workflow from data loading to visible UI states.

## Baseline

Apply `karpathy-guidelines` inline: make the smallest readable change that solves the request. Use `code-quality-principles` as a lens when robustness, testability, security, abstraction, coupling, or maintainability risk is concrete.

Do not load those skills separately unless the next action needs their full checklist.

## Specialist Routing

Load at most one specialist first, unless the next action clearly needs another.

- `frontend-design`: creating or restyling visible UI where visual quality matters.
- `vercel-composition-patterns`: reusable component APIs, boolean prop sprawl, compound components, or context/provider architecture.
- `vercel-react-best-practices`: React/Next performance, data fetching, bundle size, RSC/SSR, hydration, or rerender risk.
- `web-design-guidelines`: UI/UX/accessibility review after code exists.
- `playwright-cli`: browser proof for rendered behavior, interactions, responsive layout, or screenshots.

Do not load specialist skills just because the task is frontend. Load them when they change the next action.

## Work Loop

1. Understand the user workflow and acceptance criteria.
2. Inspect nearby routes, components, hooks, forms, query code, and design-system usage.
3. Use existing project, browser, router, form, query, and UI primitives before adding new code.
4. Build the smallest coherent screen or workflow slice.
5. Keep render flow, state ownership, API calls, mutations, and error paths visible.
6. Verify the risky behavior with typecheck, lint, build, tests, or a browser check.

## Frontend Standards

- Use domain names for props, handlers, state, files, and components.
- Keep simple render logic local; split components only for a real responsibility boundary or reuse.
- Create custom hooks only for data fetching, URL state, form setup, subscriptions, or repeated behavior.
- Do not mirror server authorization, validation, or domain rules when the API provides capability data.
- Handle loading, empty, error, disabled, permission, and optimistic states deliberately.
- Keep forms, keyboard flow, labels, focus, errors, and disabled states accessible.
- Fit the existing design system; admin UI should be dense, scannable, and work-focused.

## Review Gate

- Can a junior trace what renders, where state lives, and what can fail?
- Did existing frontend primitives cover solved behavior?
- Did code quality improve without adding unnecessary layers?
- Did verification prove the user-facing behavior?
