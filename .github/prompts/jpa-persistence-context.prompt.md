---
description: 'Find bugs from dirty checking, detached entities, merge and stale reads'
agent: ask
argument-hint: '[service class]'
---
<!-- 056 | E. JPA, Hibernate and databases | ask -->
# 056 · Persistence context pitfalls

Act as a senior Hibernate engineer.

## Context
- Target: [SERVICE_CLASS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find behaviour that depends on persistence-context mechanics the author probably did not intend.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Unintended updates through dirty checking (setters called on managed entities "just to compute").
- save() on detached or client-supplied entities overwriting columns with null (merge).
- Stale first-level cache after bulk or native updates; missing flush before a native query.
- Entities shared across threads or kept beyond the transaction.
- getReferenceById versus findById; existence checks that load whole entities.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Each finding with the sequence of calls that shows the problem, and the fix.
