---
description: 'Add Micrometer metrics and trace spans to a flow, designed for alerts and dashboards'
agent: agent
argument-hint: '[flow]'
---
<!-- 130 | M. Distributed systems and observability | build -->
# 130 · Metrics and tracing instrumentation

Act as a senior engineer who instruments code for the people on call.

## Context
- Flow: [FLOW]; questions we must be able to answer in production: [QUESTIONS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Add observability to the flow using Micrometer and the tracing setup already in this project.

## Constraints
- Tags are low-cardinality: outcome, type, dependency. Never user ids, entity ids or raw paths.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- A counter for successes and failures tagged by outcome and error category.
- A timer around each external call and around the whole flow.
- Span attributes for business identifiers that are safe to record.
- Trace context propagated across Kafka and asynchronous boundaries.
- Failure paths and early returns still recorded.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A test asserting the meters are registered and incremented.
- For each metric, the alert or dashboard panel it feeds.
