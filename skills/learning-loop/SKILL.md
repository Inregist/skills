---
name: learning-loop
description: Capture repeated agent mistakes and validated bug lessons into compact reusable rules without bloating the catalog. Use when the user points out a recurring mistake, a slop pattern appears more than once, a fixed bug needs postmortem, or workflow memory should prevent the same mistake in future work.
---

# Learning Loop

Learn from repeated mistakes, not one-off incidents.

## Quick Start

1. Name the repeated mistake class.
2. Check whether an existing skill already owns that behavior.
3. Write the smallest rule that would prevent recurrence.
4. Include allowed exceptions so the rule does not become dogma.
5. Update one target skill only, unless another file must reference it.

## Rule Shape

```text
Pattern:
Avoid:
Prefer:
Allowed when:
Target skill:
```

## Guardrails

- Do not add a new skill for every mistake.
- Do not duplicate the same rule across role skills.
- Prefer one hard rule in the owning discipline skill.
- Keep examples short or move them to a reference file.
- For postmortems, write only after the bug is fixed and validated.
- Do not invent root cause. If root cause is unknown, say unknown and list next evidence needed.

## Postmortem Shape

```text
Root cause:
Mechanism:
Fix:
Validation:
Why it slipped:
Prevention rule:
```

## Output

```text
Mistake:
Rule:
Target:
Why not broader:
```
