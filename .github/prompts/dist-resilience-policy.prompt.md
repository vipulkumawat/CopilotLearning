---
description: 'Review timeouts, retries, circuit breakers, bulkheads and fallbacks for a dependency'
agent: plan
argument-hint: '[service] -> [dependency]'
---
<!-- 134 | M. Distributed systems and observability | plan -->
# 134 · Resilience policy review

Act as a senior engineer designing for dependency failure.

## Context
- Calls from [SERVICE] to [DEPENDENCY]; library: [RESILIENCE4J_OR_OTHER]
- Upstream SLA: [SLA]; dependency's normal p99: [P99]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review the current resilience configuration and propose a coherent policy.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Timeout budget relative to the upstream SLA, across all retries.
- Retries multiplying load during an outage; retry of non-idempotent calls.
- Circuit breaker thresholds, window size, half-open behaviour and which exceptions count.
- Bulkhead or rate limiter to protect our own threads and the dependency.
- Fallbacks that return stale or wrong data without anyone knowing.
- Order of the decorators.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- The proposed configuration with, for each element, the failure scenario it protects against.
