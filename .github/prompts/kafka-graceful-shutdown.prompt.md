---
description: 'Review ack mode, commit timing, rebalance handling and shutdown of listeners'
agent: ask
argument-hint: '[consumer class or listener config]'
---
<!-- 072 | F. Kafka | ask -->
# 072 · Offset commit and shutdown behaviour review

Act as a senior Spring Kafka engineer.

## Context
- Target: [CONSUMER_CLASS_OR_CONFIG]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Determine exactly when offsets are committed and what is lost or repeated on shutdown, crash and rebalance.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- AckMode and auto-commit settings; manual acknowledgements never called on some path.
- Work handed to another thread or @Async before the offset is committed.
- Batch listeners: partial failure inside a batch.
- Deployment: in-flight records when the container stops; shutdown timeout.
- Rebalance during processing; static membership and cooperative rebalancing.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A timeline for crash, deploy and rebalance, showing which records are reprocessed or lost, and the fixes.
