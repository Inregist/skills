---
name: pnpm-audit-fix
description: Fix actual pnpm audit findings by removing stale overrides, inspecting dependency paths, and preferring normal updates before overrides. Use only when explicitly invoked or when the user directly asks to run pnpm-audit-fix.
---

# pnpm Audit Fix

Use this only for explicitly invoked pnpm audit remediation. Keep the fix narrow and prefer real dependency resolution over forced overrides.

## Workflow

1. Identify the vulnerable package and advisory.
  - If the package is not already known, run `pnpm audit`.

2. Remove any existing override for the vulnerable package.
  - Overrides may be stale or may hide the real dependency path.

3. Inspect why the package is installed.
  - Run `pnpm why <package>`.

4. Try normal updates first.
  - If the vulnerable package is direct, run `pnpm update <package>`.
  - If it is transitive, update the nearest direct parent shown by `pnpm why`.
  - Avoid broad updates unless the user explicitly asks.

5. Verify the result.
  - Run `pnpm audit`.
  - Run the relevant package tests, typecheck, or build checks for the changed area.

6. Use an override only if updates cannot resolve the finding cleanly.
  - Before adding an override, state why normal update failed.
  - Use the narrowest override possible.
  - Treat the override as temporary unless there is a clear reason it should stay.
