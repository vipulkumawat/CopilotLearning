---
description: 'Choose message keys and partitioning to get the ordering the business needs'
agent: plan
argument-hint: '[topic or event flow]'
---
<!-- 070 | F. Kafka | plan -->
# 070 · Partition key and ordering design

Act as a senior engineer designing Kafka topics.

## Context
- Flow: [TOPIC_OR_EVENT_FLOW]
- What must be processed in order: [ORDERING_REQUIREMENT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Design keys and partitioning so required ordering holds and load spreads evenly.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Entity whose events must stay ordered, and events that span two entities.
- Skewed or hot keys; null keys.
- Increasing partition count later (key-to-partition mapping changes).
- Retries and retry topics breaking order; concurrency inside one partition.
- Whether consumers should tolerate disorder (version checks) instead.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- The key choice with reasoning, the partition count estimate and what happens to ordering in each failure case.
