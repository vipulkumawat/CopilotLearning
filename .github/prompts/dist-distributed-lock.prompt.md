---
description: 'Ensure a piece of work runs on only one instance at a time, with safe expiry'
agent: agent
argument-hint: '[work to protect]'
---
<!-- 136 | M. Distributed systems and observability | build -->
# 136 · Distributed lock or single-runner guarantee

Act as a senior engineer who knows distributed locks are leases, not guarantees.

## Context
- Work: [WORK]; maximum duration: [DURATION]; instances: [INSTANCE_COUNT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Add a single-runner guarantee using the mechanism this project already has (ShedLock, a database lock or Redis).

## Constraints
- The protected work must also be idempotent, because a lease can expire while the holder still runs.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Holder crashes while holding the lock.
- Work takes longer than the lease.
- Clock differences between instances.
- Lock store unavailable.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A test with two contenders, and a metric or log showing who ran and for how long.
