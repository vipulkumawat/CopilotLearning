---
description: 'Add a @KafkaListener with deserialisation, validation, idempotent processing and error handling'
agent: agent
argument-hint: '[topic] : [what to do with each message]'
---
<!-- 062 | F. Kafka | build -->
# 062 · Implement a Kafka consumer

Act as a senior engineer who builds reliable Kafka consumers with Spring Kafka.

## Context
- Topic: [TOPIC]; event schema or sample: [SAMPLE_PAYLOAD]
- Processing: [WHAT_TO_DO]; ordering requirement: [ORDERING]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Implement the consumer so that every message is processed effectively once and a bad message never blocks the partition.

## Constraints
- The listener only translates and delegates; business logic lives in a service that can be tested without Kafka.
- Reuse the project's container factory, error handler and naming conventions.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Valid message; unknown fields; missing required fields; undeserialisable bytes.
- Duplicate delivery; redelivery after a crash between side effect and offset commit.
- Downstream timeout (retry) versus business rejection (do not retry).
- Out-of-order events for the same key; event for an entity that does not exist yet.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Unit tests for the service and an integration test with Testcontainers Kafka covering duplicate and poison messages.
- Metrics and logs carrying topic, partition, offset and key, without logging the payload's sensitive fields.
