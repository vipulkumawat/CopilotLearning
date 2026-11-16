---
description: 'Find resource leaks, unbounded reads and charset problems in I/O code'
agent: ask
argument-hint: '[class or package]'
---
<!-- 018 | B. Core Java | ask -->
# 018 · Resource and I/O handling review

Act as a senior Java engineer reviewing I/O code.

## Context
- Target: [CLASS_OR_PACKAGE]
- Largest realistic input size: [SIZE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Check that every resource is closed, nothing is read into memory unbounded and encodings are explicit.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Streams, readers, connections, Files.lines/list/walk and HTTP response bodies not in try-with-resources.
- readAllBytes, toList or String building on input of unbounded size.
- Missing charset (platform default); missing buffering.
- Paths built from user input (path traversal); temp files never deleted.
- Partial writes on failure: no write-to-temp-then-atomic-move.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: location, problem, failure mode at production size, fix.
