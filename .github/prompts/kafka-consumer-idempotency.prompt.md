---
description: 'Review a consumer for duplicate-processing risk and make it idempotent'
agent: agent
argument-hint: '[consumer class]'
---
<!-- 064 | F. Kafka | build -->
# 064 · Consumer idempotency

Act as a senior engineer who assumes at-least-once delivery.

## Context
- Consumer: [CONSUMER_CLASS]
- Side effects it performs: [SIDE_EFFECTS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Trace what happens on redelivery, then propose and implement an idempotency strategy.

## Constraints
- Compare a processed-events table, natural idempotency keys and upserts; the dedup record must commit atomically with the side effect.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Same message delivered twice (rebalance, retry, producer retry).
- Crash after the side effect but before the offset commit.
- Two instances processing the same message concurrently.
- Related events arriving out of order across partitions.
- Side effects outside the database (email, HTTP call) that cannot be rolled back.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A test delivering the same message twice, concurrently and sequentially, asserting one side effect.
- The retention policy for dedup records.
