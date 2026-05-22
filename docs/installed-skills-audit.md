# Installed Skills Audit

This audit maps installed local skills and catalog skills to the current gate-based workflow.

## Current Decision

The workflow spine should stay small. The source catalog may also include explicit-only tools and selected domain specialists.

Spine skills:

- `intent`
- `routing-work`
- `discovering-context`
- `grill-me`
- `planning-work`
- `karpathy-guidelines`
- `debugging-work`
- `verifying-work`
- `capturing-workflow`

Explicit-only:

- `caveman`
- `caveman-commit`
- `handoff`
- `pnpm-audit-fix`

Domain/support skills:

- `frontend-engineer`
- `backend-engineer`
- `frontend-design`
- `vercel-composition-patterns`
- `vercel-react-best-practices`
- `web-design-guidelines`
- `playwright-cli`
- `tdd`
- `code-quality-principles`

Removed from the spine:

- `reviewing-work`: review is useful, but should be a risk-triggered behavior or external specialist skill, not a default phase.
- `finishing-work`: closeout is normal final-answer behavior.
- `team-conventions`: project instructions belong in `AGENTS.md`/docs, not a workflow skill.

## Gate Fit

| Gate | Catalog Skill | Installed/Specialized Support |
| --- | --- | --- |
| `INTENT` | `intent` | `yeehaw:intent` |
| `ROUTE` | `routing-work` | `karpathy-guidelines` as optional guardrail |
| `CONTEXT` | `discovering-context` | `zoom-out`, `improve-codebase-architecture` for heavy architecture context |
| `DECIDE` | `grill-me` | `product-designer`, `tech-lead`, `frontend-design` for domain-specific decisions |
| `ACT` | `karpathy-guidelines` when slop is likely; `tdd` for explicit test-first behavior loops | `frontend-engineer`, `backend-engineer`, React/Vercel skills when directly relevant |
| `DEBUG` | `debugging-work` | `systematic-debugging`, `diagnose`, `playwright-cli` |
| `PROVE` | `verifying-work` | `playwright-cli`, `web-design-guidelines` |
| `CLOSE` | `handoff` and `caveman-commit` only when explicitly invoked | normal final answer behavior |
| `CAPTURE` | `capturing-workflow` | `skill-creator`, `write-a-skill` |

## Routing Rules

- FAST: clear, low-risk, reversible. No workflow skill after intent.
- DISCIPLINE: one focused gate prevents likely failure.
- HEAVY: wrong work would be costly. Discover first, then grill or plan.

## Specialized Skills

Keep other installed skills available, but outside the source spine:

- `caveman`: communication mode; copied into source catalog; explicit user preference.
- `caveman-commit`: commit-message generation only; explicit invoke, not routed by default.
- `pnpm-audit-fix`: narrow dependency remediation; copied into source catalog; explicit invoke only.
- `playwright-cli`: browser/UI verification; copied into source catalog.
- `tdd`: copied into source catalog; behavior tripwire during coding, not generic final verification.
- `systematic-debugging` / `diagnose`: heavier debugging reference.
- `frontend-design`, `web-design-guidelines`, React/Vercel skills: frontend-specific work; copied into source catalog.
- `improve-codebase-architecture`: HEAVY architecture review.
- `handoff`: copied into source catalog; explicit session transfer.

## Known Risks

- Too many catalog skills increase trigger noise and token cost.
- A phase-chain encourages ceremony and false completion.
- Plugin validation only proves manifest/skill shape, not workflow correctness.
- Workflow claims need dogfood/subagent/current-file evidence.

## Next Build Rule

Add a new catalog skill only after repeated use proves it changes the next action better than ordinary agent behavior.
