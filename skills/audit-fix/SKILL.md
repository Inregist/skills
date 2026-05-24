---
name: audit-fix
description: Remediate dependency audit findings with evidence and minimal dependency changes. Use when the user explicitly invokes audit remediation, mentions pnpm/npm audit fix work, or asks to address dependency vulnerabilities.
---

# Audit Fix

Fix audit findings without dependency churn.

## Quick Start

1. Read the audit output and advisory.
2. Identify the vulnerable package and dependency path.
3. Prefer normal package updates before overrides.
4. Avoid broad upgrades unrelated to the advisory.
5. Verify with the audit command and relevant local checks.

## Evidence

- advisory id/package/version;
- dependency path;
- chosen update or override;
- lockfile/package changes;
- verification command output.

## Output

```text
Advisory:
Path:
Fix:
Verification:
Remaining risk:
```
