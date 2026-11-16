---
description: 'Review a frequently executed code path for avoidable CPU, allocation and I/O cost'
agent: ask
argument-hint: '[method or endpoint]'
---
<!-- 093 | I. Performance and JVM | ask -->
# 093 · Hot path performance review

Act as a performance engineer who measures before optimising.

## Context
- Hot path: [METHOD_OR_ENDPOINT]; call rate: [RATE]; current latency: [LATENCY]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Identify avoidable cost on this path and say how to measure each suspicion.

## Constraints
- Rank by expected gain; do not suggest micro-optimisations without evidence they matter.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Repeated I/O: queries or remote calls in loops, data loaded and then discarded.
- Algorithmic cost: nested scans, repeated sorting, regex compiled per call.
- Allocation: boxing, large intermediate collections, string building, per-call ObjectMapper or formatter creation.
- Logging and serialisation cost on the hot path; synchronised sections.
- Work that could be cached, batched or moved off the request path.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A ranked list: suspicion, evidence in code, how to measure (metric, profiler view or JMH), fix.
