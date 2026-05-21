# Installed Skills Audit

This audit maps installed local skills and catalog skills to the current gate-based workflow.

## Current Decision

The source catalog should stay small. The workflow spine is a set of gates, not a full lifecycle.

Keep in `skills/`:

- `caveman-commit` (explicit-only tool)
- `intent`
- `routing-work`
- `discovering-context`
- `grill-me`
- `planning-work`
- `debugging-work`
- `verifying-work`
- `capturing-workflow`

Removed from the spine:

- `executing-work`: direct action is normal agent behavior.
- `reviewing-work`: review is useful, but should be a risk-triggered behavior or external specialist skill, not a default phase.
- `finishing-work`: closeout is normal final-answer behavior.
- `team-conventions`: project instructions belong in `AGENTS.md`/docs, not a workflow skill.

## Gate Fit

| Gate | Catalog Skill | Installed/Specialized Support |
| --- | --- | --- |
| `INTENT` | `intent` | `co-code:intent` |
| `ROUTE` | `routing-work` | `karpathy-guidelines` as optional guardrail |
| `CONTEXT` | `discovering-context` | `zoom-out`, `improve-codebase-architecture` for heavy architecture context |
| `DECIDE` | `grill-me` | `product-designer`, `tech-lead`, `frontend-design` for domain-specific decisions |
| `ACT` | none | `tdd`, `frontend-engineer`, `backend-engineer`, React/Vercel skills when directly relevant |
| `DEBUG` | `debugging-work` | `systematic-debugging`, `diagnose`, `playwright-cli` |
| `PROVE` | `verifying-work` | `playwright-cli`, `tdd`, `web-design-guidelines` |
| `CLOSE` | `caveman-commit` only when explicitly invoked | `handoff` only when requested |
| `CAPTURE` | `capturing-workflow` | `skill-creator`, `write-a-skill` |

## Routing Rules

- FAST: clear, low-risk, reversible. No workflow skill after intent.
- DISCIPLINE: one focused gate prevents likely failure.
- HEAVY: wrong work would be costly. Discover first, then grill or plan.

## Specialized Skills

Keep installed skills available, but outside the source spine:

- `caveman`: communication mode, explicit user preference.
- `caveman-commit`: commit-message generation only; explicit invoke, not routed by default.
- `pnpm-audit-fix`: narrow dependency remediation.
- `playwright-cli`: browser/UI verification.
- `tdd`: test-first implementation when requested or clearly valuable.
- `systematic-debugging` / `diagnose`: heavier debugging reference.
- `frontend-design`, `web-design-guidelines`, React/Vercel skills: frontend-specific work.
- `improve-codebase-architecture`: HEAVY architecture review.
- `handoff`: session transfer.

## Known Risks

- Too many catalog skills increase trigger noise and token cost.
- A phase-chain encourages ceremony and false completion.
- Plugin validation only proves manifest/skill shape, not workflow correctness.
- Workflow claims need dogfood/subagent/current-file evidence.

## Next Build Rule

Add a new catalog skill only after repeated use proves it changes the next action better than ordinary agent behavior.
