---
description: 'Find untested behaviour, meaningless assertions and fragile tests in a package'
agent: ask
argument-hint: '[package]'
---
<!-- 103 | J. Testing | ask -->
# 103 · Test gap analysis

Act as a senior engineer auditing a test suite.

## Context
- Target: [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Tell me where the test suite gives false confidence.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Per production class: tests present, and of which kind (unit, slice, integration).
- Branches and behaviours not covered, especially error paths.
- Tests that assert nothing meaningful, or only verify mocks.
- Tests that depend on execution order, wall-clock time, random data or shared state.
- Over-mocked tests that would pass if the implementation were wrong.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Gaps ranked by production risk, with the specific test to write for the top ten. Do not write them yet.
