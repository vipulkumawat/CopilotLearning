---
description: 'Review ConcurrentHashMap, atomic and cache usage for compound-action bugs and unbounded growth'
agent: ask
argument-hint: '[class]'
---
<!-- 091 | H. Concurrency | ask -->
# 091 · Concurrent collections and in-memory cache review

Act as a senior Java engineer.

## Context
- Target: [CLASS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Check that concurrent collections and caches are used atomically and stay bounded.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- get-then-put instead of computeIfAbsent or merge; long or recursive work inside compute functions.
- Iteration assumptions (weakly consistent); size() used for decisions.
- Atomic variables combined non-atomically; counters that should be LongAdder.
- Maps used as caches with no size limit or expiry.
- Cache stampede: many threads loading the same key.
- Mutable values shared after being published in the map.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: location, bug or risk, concrete interleaving, fix.
