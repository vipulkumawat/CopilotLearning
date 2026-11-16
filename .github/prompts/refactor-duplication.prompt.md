---
description: 'Find duplicated logic whose copies have drifted apart'
agent: ask
argument-hint: '[package]'
---
<!-- 129 | L. Security and code quality | ask -->
# 129 · Duplication and inconsistency report

Act as a senior engineer hunting duplicated business logic.

## Context
- Target: [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find logic implemented more than once, especially where the copies now behave differently.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Validation, calculation and mapping duplicated across services, consumers and jobs.
- Copies that differ in an edge case (null handling, rounding, boundary).
- Constants and status lists repeated.
- Duplication that should stay, because the contexts genuinely differ.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: logic, locations, behavioural differences, which copy is correct, proposed single home.
