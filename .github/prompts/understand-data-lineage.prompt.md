---
description: 'Trace one field from API input to database column, events, caches and reports'
agent: ask
argument-hint: '[entity.field]'
---
<!-- 006 | A. Understand the codebase | ask -->
# 006 · Data lineage of a field

Act as a senior Java engineer tracing how a piece of data moves through the system.

## Context
- Field: [ENTITY.FIELD]
- Reason I am asking: [REASON, e.g. changing its type, wrong values in production]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Trace every place this field is created, transformed, stored, published and read.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Where it enters: request DTOs, consumed events, files, defaults.
- Every mapper, converter, formatter or rounding step applied to it.
- Database column type, nullability, constraints and indexes.
- Where it leaves: response DTOs, published events, exports, logs.
- Places where two code paths write it differently.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A lineage table: stage, class.method, transformation, type.
- A list of inconsistencies and of consumers outside this repository that must be told about any change.
