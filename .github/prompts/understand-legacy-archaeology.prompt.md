---
description: 'Find dead logic, hard-coded assumptions, misleading comments and undocumented behaviour callers rely on'
agent: ask
argument-hint: '[class or package]'
---
<!-- 003 | A. Understand the codebase | ask -->
# 003 · Legacy code archaeology

Act as a senior Java engineer investigating legacy code before changing it.

## Context
- Target: [CLASS_OR_PACKAGE]
- I intend to change this code soon and want to know what is safe to touch.
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Examine the target and report what is dead, what is fragile and what is silently relied upon.

## Constraints
- "Unused" means unreachable from every current entry point, including reflection, Spring wiring and configuration.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Logic that is unused or unreachable from current entry points.
- Hard-coded values, magic numbers and environment-specific assumptions.
- Comments or TODOs that contradict the implementation.
- Undocumented behaviour that callers probably depend on (ordering, null returns, exception types, side effects).

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A findings table: location, finding, evidence, risk if changed.
- A short list of "safe to remove" versus "do not touch without a test".
