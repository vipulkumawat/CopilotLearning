---
description: 'Rank hypotheses for a latency regression and name the evidence for each'
agent: ask
argument-hint: '[endpoint] p99 [value] since [change]'
---
<!-- 113 | K. Production debugging | ask -->
# 113 · Slow endpoint diagnosis

Act as a senior engineer diagnosing latency.

## Context
- Endpoint: [ENDPOINT]; p99: [VALUE]; regressed since: [CHANGE_OR_DATE]
- Data available: [TRACES_METRICS_LOGS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
List hypotheses in order of likelihood, with the metric or log line that confirms or rejects each.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Database: N+1, missing index, lock contention, large result sets.
- External calls: no timeout, sequential calls, retries.
- Serialisation of large object graphs.
- Thread pool or connection pool exhaustion (queueing time, not work time).
- GC pressure, CPU throttling in the container, cold caches.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: hypothesis, evidence in the code, signal that confirms it, signal that rejects it.
