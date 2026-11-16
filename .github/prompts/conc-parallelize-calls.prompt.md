---
description: 'Run independent remote or database calls concurrently with timeouts and error handling'
agent: agent
argument-hint: '[method with sequential calls]'
---
<!-- 088 | H. Concurrency | build -->
# 088 · Parallelise independent calls

Act as a senior Java engineer reducing latency safely.

## Context
- Method: [METHOD]; calls believed independent: [CALLS]
- Latency budget: [BUDGET]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Confirm which calls are truly independent, then run them concurrently.

## Constraints
- Use a dedicated bounded executor (or structured concurrency or virtual threads if the project uses them), never the common pool for blocking calls.
- Do not parallelise work that shares a transaction or a persistence context.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- One call fails: fail fast or return partial data?
- One call is slow: per-call and overall timeout, and cancellation of the rest.
- MDC, security context and trace propagation.
- Load multiplication on downstream systems.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Tests for all-success, one-failure and one-timeout; latency before and after.
