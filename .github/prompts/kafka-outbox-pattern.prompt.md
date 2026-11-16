---
description: 'Replace a dual write with a transactional outbox and a reliable relay'
agent: agent
argument-hint: '[service method that writes DB and publishes]'
---
<!-- 067 | F. Kafka | build -->
# 067 · Transactional outbox

Act as a senior engineer implementing reliable messaging.

## Context
- Dual write today: [SERVICE_METHOD]
- Relay option preferred: [POLLER_OR_CDC]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Introduce an outbox table written in the business transaction, and a relay that publishes from it.

## Constraints
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Relay crashes after publishing but before marking the row sent (duplicates: consumers must cope).
- Ordering per aggregate; several relay instances (locking, SKIP LOCKED).
- Poison row that can never be published.
- Outbox growth and cleanup; lag monitoring.
- Poll interval versus latency requirement.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Migration, relay and tests for rollback (no row), crash before publish (not lost) and duplicate publish.
- A metric for the age of the oldest unsent row.
