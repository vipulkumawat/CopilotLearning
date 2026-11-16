---
description: 'Write a derived, JPQL, Specification or native query with a projection and a real-database test'
agent: agent
argument-hint: '[what the query must return]'
---
<!-- 053 | E. JPA, Hibernate and databases | build -->
# 053 · Write a repository query from a specification

Act as a senior JPA engineer who checks the SQL that is generated.

## Context
- Repository: [REPOSITORY]; what to return: [RESULT_DESCRIPTION]
- Filters, sort and paging: [CRITERIA]; table size: [ROW_COUNT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write the query using the simplest mechanism that fits, returning only what the caller needs.

## Constraints
- Parameters are always bound, never concatenated. Prefer a DTO or interface projection for read-only data.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Optional filters; empty IN list; null parameters.
- Case sensitivity, date range boundaries and time zones.
- Duplicates caused by joins; count query for pagination.
- Large result: paging or streaming rather than a List.

## Code examples
Give one example row set and the expected result, for example: "orders A (PAID, 2 items), B (NEW, 0 items) -> returns A only".

## Confirmation
- The generated SQL shown, and the index it relies on.
- A test against a real database (Testcontainers) covering each case.
