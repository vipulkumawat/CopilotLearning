---
description: 'Review poll, concurrency and partition settings against real processing time'
agent: ask
argument-hint: '[consumer group]'
---
<!-- 069 | F. Kafka | ask -->
# 069 · Consumer group and lag risk review

Act as a senior engineer who tunes Kafka consumers.

## Context
- Consumer group: [CONSUMER_GROUP]
- Measured per-record processing time: [TIME]; peak input rate: [RATE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Check whether the configuration can keep up with load and survive slow processing without rebalancing.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- max.poll.records and max.poll.interval.ms versus worst-case batch time.
- session.timeout.ms and heartbeat settings; rebalance storms from long processing.
- Partition count versus listener concurrency and instance count: idle threads or a bottleneck.
- Per-key ordering: required or accidental; hot keys and skew.
- Offset commit mode and what is reprocessed after a restart.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: setting, current value, symptom it would cause in production, recommendation.
- The throughput estimate behind the recommendation.
