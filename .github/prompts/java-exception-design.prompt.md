---
description: 'Review exception types, propagation, wrapping and swallowed errors'
agent: ask
argument-hint: '[package]'
---
<!-- 012 | B. Core Java | ask -->
# 012 · Exception handling review

Act as a senior Java engineer reviewing error handling.

## Context
- Target: [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review how errors are raised, translated and handled, and whether failures can be lost.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Catch blocks that swallow, log-and-continue or log-and-rethrow (double logging).
- catch (Exception) or catch (Throwable) hiding programming errors; InterruptedException not restoring the flag.
- Lost causes: new exception created without the original as cause.
- Exceptions used for control flow; business failures thrown as RuntimeException with only a message.
- Checked exceptions inside @Transactional methods that will not roll back.
- Resources not released on the failure path.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Findings by severity with the failure each one hides.
- A proposed exception hierarchy (business, validation, technical-retryable, technical-fatal) mapped to existing types.
