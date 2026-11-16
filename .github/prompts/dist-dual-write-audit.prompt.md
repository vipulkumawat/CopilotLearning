---
description: 'Find places where two systems are updated without atomicity'
agent: ask
argument-hint: '[package or service]'
---
<!-- 135 | M. Distributed systems and observability | ask -->
# 135 · Dual-write and consistency audit

Act as a distributed systems engineer hunting consistency bugs.

## Context
- Scope: [PACKAGE_OR_SERVICE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find every operation that updates more than one system and say what happens when the second update fails.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Database plus Kafka, database plus HTTP call, database plus cache, database plus file or email.
- The order of the writes and the state after a crash between them.
- Calls made inside the transaction that cannot be rolled back.
- Missing reconciliation or retry.
- Consumers that could observe an event before the data is committed.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: operation, systems, failure window, consequence, fix (outbox, after-commit, idempotent retry, reconciliation).
