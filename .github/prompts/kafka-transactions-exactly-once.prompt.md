---
description: 'Decide whether Kafka transactions are needed and what they do and do not guarantee here'
agent: plan
argument-hint: '[consumer/producer flow]'
---
<!-- 071 | F. Kafka | plan -->
# 071 · Consume-process-produce and exactly-once assessment

Act as a senior engineer who knows the limits of exactly-once semantics.

## Context
- Flow: [FLOW, e.g. consume topic A, update DB, produce to topic B]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Determine the delivery guarantee this flow has today, the one it needs, and the cheapest way to get it.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Which steps are inside Kafka (offsets, produced records) and which are outside (database, HTTP).
- What Kafka transactions cover, and why a database write is not included.
- isolation.level of downstream consumers.
- Idempotent consumer plus outbox as an alternative.
- Throughput and operational cost of transactions.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A table of failure points with the outcome under each option, and a recommendation.
