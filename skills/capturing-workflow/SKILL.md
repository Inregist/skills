---
name: capturing-workflow
description: Turn a repeated workflow or repeated agent failure into a reusable skill. Use when a pattern worked well, the same mistake keeps happening, or the user says to make a workflow reusable.
---

# Capturing Workflow

Create a skill only when it will change future behavior.

## Gate

1. Name the repeated situation or failure mode.
2. Define when the skill should trigger.
3. Define when it should not trigger.
4. Write the shortest workflow that prevents the failure.
5. Move heavy examples or references out of `SKILL.md`.
6. Verify frontmatter and word count.

## Shape

```text
skills/<name>/
  SKILL.md
```

`description` says when to use the skill. Body says what to do.

## Avoid

- one-off lessons;
- generic advice the model already knows;
- long persuasion text;
- broad triggers that make the skill load too often.
