---
name: browser-proof
description: Prove UI behavior with browser evidence such as interaction checks, screenshots, responsive checks, or accessibility snapshots. Use when frontend work changes visible UI, layout, navigation, forms, interactions, loading/error states, or when visual correctness matters.
---

# Browser Proof

Use browser evidence for UI claims.

## Quick Start

1. Start or connect to the app.
2. Open the relevant route/state in a browser.
3. Exercise the changed interaction or visual state.
4. Capture evidence: screenshot, locator assertion, accessibility snapshot, or interaction result.
5. Report what the evidence proves and what remains unverified.

## Evidence Choices

- Layout/visual: screenshot at relevant viewport.
- Interaction: click/type/submit and observe result.
- Forms: validation, disabled/loading/error/success states.
- Responsive: desktop and mobile viewport checks.
- Accessibility: labels, focus, keyboard path, or accessibility snapshot.

## Output

```text
Checked:
Evidence:
Proves:
Remaining risk:
```
