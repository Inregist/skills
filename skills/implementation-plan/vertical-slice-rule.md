# MVP Vertical Slice Rule

## Pattern

When a PRD or product objective asks for an MVP, broad package/scaffold work can masquerade as progress while no release-critical user workflow works end to end.

## Avoid

Starting by building every named package, infra surface, auth layer, schema family, and UI shell from the PRD before proving one persisted workflow.

## Prefer

Pick the smallest release-critical vertical slice first:

```text
user action -> API/service -> domain rule -> persistence -> UI readback -> verification
```

Add package structure only when that slice needs it.

## Allowed When

- The user explicitly asks for scaffolding or architecture first.
- The repo already has a working vertical slice and the task is to align infrastructure/tooling.

## General Lesson

Do not start with the architecture map. Start with the smallest outcome that proves the system is real.

For any big goal:

- Pick one concrete user/job workflow.
- Build it end to end.
- Verify it with real behavior.
- Only then expand sideways.

Examples:

- PRD: build one release-critical flow first.
- Backend: one endpoint through validation, domain logic, persistence, and test.
- Frontend: one screen workflow through loading, action, error/success, and refresh.
- Infra: one deployable service with health check before adding queues/storage/domains.
- Refactor: one call path migrated and verified before global cleanup.

Architecture still matters, but it should serve the first working path, not replace it.
