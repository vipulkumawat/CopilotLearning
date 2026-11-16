---
description: 'Reproduce and fix a race in balance, stock, quota or uniqueness logic'
agent: agent
argument-hint: '[method]'
---
<!-- 084 | H. Concurrency | build -->
# 084 · Race condition in check-then-act logic

Act as a senior engineer who fixes races at the data layer.

## Context
- Method: [METHOD]; invariant to protect: [INVARIANT, e.g. stock never below zero]
- Instances running: [INSTANCE_COUNT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Explain the interleaving that breaks the invariant, reproduce it in a test, then fix it.

## Constraints
- The fix must hold across several application instances, so JVM locks alone are not enough.
- Compare a conditional UPDATE, a unique constraint, SELECT ... FOR UPDATE, optimistic locking and an atomic operation.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Two requests for the last unit; many requests at once.
- A retry of the same request; a timeout after the write succeeded.
- Behaviour under the database's default isolation level.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A concurrent test that fails before the fix and passes after it, run enough times to be reliable.
- A clean, specific error for the request that loses the race.
