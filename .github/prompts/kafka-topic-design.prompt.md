---
description: 'Design partitions, retention, compaction and naming for a new topic'
agent: plan
argument-hint: '[topic purpose]'
---
<!-- 073 | F. Kafka | plan -->
# 073 · Topic configuration design

Act as a platform-minded engineer designing a Kafka topic.

## Context
- Purpose: [PURPOSE]; producers and consumers: [PARTIES]
- Volume: [MESSAGES_PER_SECOND], message size: [SIZE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Propose the topic configuration and justify each setting from the requirements.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Partition count from throughput and consumer parallelism; replication factor and min.insync.replicas.
- Retention by time and size; compaction for latest-state topics; tombstones.
- Replay needs: how far back a new consumer must read.
- Naming, ownership, access control and personal-data retention obligations.
- Maximum message size and what to do with larger payloads.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- The configuration with a one-line reason per setting, and what would make us revisit it.
