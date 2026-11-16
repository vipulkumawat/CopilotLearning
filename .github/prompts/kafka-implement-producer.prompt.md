---
description: 'Publish an event with the right key, headers, serialisation and failure handling'
agent: agent
argument-hint: '[event] -> [topic]'
---
<!-- 063 | F. Kafka | build -->
# 063 · Implement a Kafka producer

Act as a senior engineer who builds reliable Kafka producers.

## Context
- Event: [EVENT_NAME] with [FIELDS]; topic: [TOPIC]
- Trigger: [WHERE_IN_CODE_IT_IS_PUBLISHED]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Implement publishing so that events are not lost, not reordered per key and can evolve.

## Constraints
- State explicitly how publishing relates to the database transaction (outbox, after-commit or transactional producer).
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Key choice and what ordering it guarantees.
- Send failure, timeout and broker unavailability: the result of send() must be handled.
- Database commit succeeds and send fails, and the reverse.
- Headers: event id, type, version, trace context, timestamp.
- Payload size limits and personal data in the payload.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A test asserting key, headers and payload on the produced record, and a test for the failure path.
- The event contract documented with a version.
