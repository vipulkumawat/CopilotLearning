---
description: 'Map a distributed workflow, its compensations and the states it can be left in'
agent: ask
argument-hint: '[workflow] across [services]'
---
<!-- 133 | M. Distributed systems and observability | ask -->
# 133 · Saga and compensation review

Act as a distributed systems engineer reviewing a multi-service workflow.

## Context
- Workflow: [WORKFLOW_NAME]; services: [SERVICES]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Map each step and its compensating action, and find where the system can be left inconsistent.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Steps that cannot be compensated and need a different approach (reserve then confirm, last step).
- Failure between any two steps; compensation that itself fails.
- Idempotency of every step and every compensation.
- Timeouts while waiting for each step, and what happens on expiry.
- Concurrent workflows on the same entity; visibility of intermediate states to users.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A Mermaid state diagram and a table of failure scenarios with the expected final state.
