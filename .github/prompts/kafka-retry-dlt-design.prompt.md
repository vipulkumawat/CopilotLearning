---
description: 'Classify failures and design retries, dead-letter topics, replay and alerting for a consumer'
agent: plan
argument-hint: '[consumer class]'
---
<!-- 065 | F. Kafka | plan -->
# 065 · Retry and dead-letter design

Act as a senior engineer designing Kafka error handling.

## Context
- Consumer: [CONSUMER_CLASS]; ordering requirement: [ORDERING]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Design error handling that retries what can succeed, parks what cannot, and never stalls the partition.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Classification: deserialisation error, validation error, downstream timeout, database deadlock, business rule violation.
- Retry policy: count, backoff, blocking versus non-blocking retry topics, and the effect on ordering.
- max.poll.interval.ms versus total blocking retry time.
- Dead-letter topic: naming, headers recorded (exception, original topic, partition, offset), retention.
- How an operator inspects and replays dead-lettered messages safely.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A failure-type table with the chosen handling, the Spring Kafka configuration sketch and alert thresholds.
