---
description: 'Cache a read path with explicit key, TTL, invalidation and stampede protection'
agent: agent
argument-hint: '[method to cache]'
---
<!-- 033 | C. Feature development | build -->
# 033 · Add caching to a read path

Act as a senior Java engineer who treats caching as a consistency decision.

## Context
- Method or query: [METHOD]; call rate and latency today: [NUMBERS]
- How stale the data may be: [STALENESS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Decide whether caching is the right fix, then add it with the project's cache abstraction.

## Constraints
- Every cache has a bounded size and a TTL; cached values are immutable DTOs, not entities.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- All writes that must evict or update the entry, including ones in other services or jobs.
- Key design: tenant, user, locale or permissions that change the result.
- Null or empty results; exceptions must not be cached.
- Many concurrent misses on one key; multiple instances with local caches.
- Cache unavailable: fall through to the source.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Tests for hit, miss, eviction on write and fall-through.
- Hit ratio and size metrics, and the staleness window stated in a comment.
