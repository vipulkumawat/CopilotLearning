---
description: 'Review producer configuration and usage for message loss, duplication and reordering'
agent: ask
argument-hint: '[package]'
---
<!-- 066 | F. Kafka | ask -->
# 066 · Producer reliability review

Act as a senior engineer reviewing Kafka producer guarantees.

## Context
- Target: producer configuration and send calls in [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Verify that the configuration and the calling code deliver the guarantees the business assumes.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- acks, enable.idempotence, retries, delivery.timeout.ms and max.in.flight.requests.per.connection.
- send() results ignored, or blocking get() on a request thread.
- Dual writes: database commit plus Kafka send with no outbox or transaction.
- Whether transactional sends are needed for consume-process-produce.
- Serialiser failures, oversized records and buffer exhaustion.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: risk, failure scenario, current setting, recommended setting.
