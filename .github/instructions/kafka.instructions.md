---
applyTo: '**/*Consumer*.java,**/*Listener*.java,**/*Producer*.java,**/*Publisher*.java,**/kafka/**/*.java,**/messaging/**/*.java'
description: 'Rules for Kafka consumers and producers'
---
# Kafka code

- Delivery is at least once: every consumer must be idempotent. State how duplicates are detected.
- Listeners only deserialise, validate and delegate to a service that is testable without Kafka.
- Classify every failure as retryable (timeouts, deadlocks) or not (deserialisation, validation, business rejection). Non-retryable messages go to the dead-letter topic; nothing blocks a partition forever.
- Offsets are committed only after processing succeeds. Do not hand work to another thread before the offset is safe.
- Total processing plus blocking retry time must stay under `max.poll.interval.ms`.
- Producers: choose the key deliberately for ordering, handle the result of `send()`, and never publish inside a database transaction without an outbox or an after-commit hook.
- Every event carries an id, type, version and timestamp. Schema changes must be backward compatible.
- Log topic, partition, offset and key on failure. Never log full payloads that may contain personal data.
- Integration tests use Testcontainers Kafka and Awaitility, and include a duplicate and a poison message.
