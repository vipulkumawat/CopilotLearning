---
description: 'Find sensitive data in logs and logging that hinders operations'
agent: ask
argument-hint: '[package]'
---
<!-- 124 | L. Security and code quality | ask -->
# 124 · Safe logging review

Act as a senior engineer reviewing logs for security and usefulness.

## Context
- Target: [PACKAGE]; data classed as sensitive here: [SENSITIVE_DATA]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review log statements for leaked data and for poor diagnostic value.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Passwords, tokens, card or account numbers and personal data.
- Whole request, response or entity objects logged (toString exposing sensitive fields).
- Exceptions logged without context, without the stack trace, or twice.
- Missing correlation or trace identifiers and business keys.
- Levels that do not match severity; log injection through unsanitised input; logging in tight loops.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: location, issue, replacement log statement.
