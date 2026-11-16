---
description: 'Publish a domain event reliably after the database transaction commits'
agent: agent
argument-hint: '[event and the action that triggers it]'
---
<!-- 034 | C. Feature development | build -->
# 034 · Publish an event after commit

Act as a senior Java engineer who avoids dual-write bugs.

## Context
- Triggering action: [ACTION in SERVICE_CLASS]
- Event: [EVENT_NAME] with [FIELDS]; destination: [KAFKA_TOPIC_OR_IN_PROCESS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Publish the event so that it is sent if and only if the business transaction commits.

## Constraints
- Compare @TransactionalEventListener(AFTER_COMMIT) with a transactional outbox, and justify the choice before coding.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Transaction rolls back: no event.
- Commit succeeds but publishing fails or the JVM dies.
- Event published twice; consumers reading before the data is visible.
- Ordering of events for the same aggregate.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Tests for rollback (no event) and for publish failure (event not lost).
- The event schema documented with a version field.
