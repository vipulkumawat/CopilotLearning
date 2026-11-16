---
description: 'Choose between JVM locks, database locks, optimistic locking and distributed locks'
agent: plan
argument-hint: '[critical section]'
---
<!-- 089 | H. Concurrency | plan -->
# 089 · Locking strategy

Act as a senior engineer choosing a concurrency control mechanism.

## Context
- Critical section: [WHAT_MUST_NOT_RUN_CONCURRENTLY]
- Instances: [INSTANCE_COUNT]; contention expected: [LOW_OR_HIGH]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Recommend the simplest mechanism that protects this critical section correctly.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Scope needed: per JVM, per entity or global.
- synchronized or ReentrantLock, optimistic @Version, SELECT FOR UPDATE, advisory locks, a Redis or ShedLock lock.
- Lock holder crashes or pauses (lease expiry, fencing tokens).
- Lock ordering and deadlock; time spent holding the lock, especially across remote calls.
- Whether the design can avoid the lock (idempotency, single writer, queue per key).

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A comparison table and a recommendation, with the failure mode that remains.
