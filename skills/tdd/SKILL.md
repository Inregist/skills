---
name: tdd
description: Test-driven development with red-green-refactor loop. Use when the user asks for TDD/test-first work, or when you intentionally choose a test-first loop for a testable behavior change. Do not use as generic final verification, visual proof, architecture review, or docs/workflow proof.
---

# Test-Driven Development

Use this as a behavior tripwire while coding: one failing behavior test, smallest passing implementation, refactor only while green.

TDD catches behavior slop. It does not prove UI visuals, product decisions, architecture quality, readability, security, performance, or docs correctness unless those are expressed as behavior tests.

## Philosophy

Tests verify behavior through public interfaces, not implementation details. Prefer integration-style tests that exercise real code paths and read like specifications.

Avoid tests coupled to private methods, internal collaborators, or data structure shape. If a test fails after a refactor while behavior is unchanged, it was testing implementation.

See [tests.md](tests.md) for examples and [mocking.md](mocking.md) only when the task needs that detail.

## Anti-Pattern: Horizontal Slices

Do not write all tests first, then all implementation. Bulk RED tends to test imagined behavior, data shapes, or function signatures before the real implementation path is understood.

Use vertical tracer bullets instead: one behavior test, one minimal implementation, repeat. Each test should respond to what the last cycle proved.

## Workflow

### 1. Planning

When exploring the codebase, use the project's domain glossary so that test names and interface vocabulary match the project's language, and respect ADRs in the area you're touching.

Before writing any code:

- [ ] Infer the public interface and behavior from the request and codebase.
- [ ] Ask only when the interface, priority, or expected behavior is not discoverable.
- [ ] List the first behavior to test, not implementation steps.
- [ ] Pick the first behavior that gives the fastest useful feedback.

For bug fixes, use root-cause debugging first. After the cause is known, add a regression test if the behavior is testable.

For frontend work, use TDD for logic/state behavior only. Use browser proof for visuals and interaction.

### 2. Tracer Bullet

Write one test that confirms one thing:

```
RED:   Write test for first behavior -> test fails
GREEN: Write minimal code to pass -> test passes
```

This is your tracer bullet - proves the path works end-to-end.

### 3. Incremental Loop

For each remaining behavior:

```
RED:   Write next test -> fails
GREEN: Minimal code to pass -> passes
```

Rules:

- One test at a time
- Only enough code to pass current test
- Don't anticipate future tests
- Keep tests focused on observable behavior

### 4. Refactor

After all tests pass, look for [refactor candidates](refactoring.md):

- [ ] Extract duplication
- [ ] Deepen modules (move complexity behind simple interfaces)
- [ ] Apply SOLID principles where natural
- [ ] Consider what new code reveals about existing code
- [ ] Run tests after each refactor step

**Never refactor while RED.** Get to GREEN first.

## Checklist Per Cycle

```
[ ] Test describes behavior, not implementation
[ ] Test uses public interface only
[ ] RED fails for the expected reason
[ ] Test would survive internal refactor
[ ] Code is minimal for this test
[ ] No speculative features added
```

Final completion still uses `verification-discipline`: rerun the relevant tests and report what they prove.
