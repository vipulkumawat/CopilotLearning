---
description: 'Assess whether the application can safely adopt virtual threads and what to change first'
agent: plan
argument-hint: '[service]'
---
<!-- 086 | H. Concurrency | plan -->
# 086 · Virtual threads adoption assessment

Act as a senior Java engineer evaluating Project Loom for a production service.

## Context
- Service: [SERVICE]; Java version: [JAVA_VERSION]; workload: [WORKLOAD, e.g. blocking JDBC plus HTTP calls]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Assess the benefit and the risks of enabling virtual threads here.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Blocking I/O inside synchronized blocks or native calls (pinning), and whether the Java version in use still pins.
- ThreadLocal usage: large per-thread caches, MDC, security context.
- Downstream limits that concurrency will now hit: connection pools, rate limits.
- Libraries and drivers not friendly to virtual threads; pooled executors that should not be pooled.
- CPU-bound work that gains nothing.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A recommendation (adopt, adopt partly or wait), the ordered changes and the load test that would prove it.
