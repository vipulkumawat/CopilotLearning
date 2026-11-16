---
description: 'Find shared mutable state, unsafe types and non-atomic sequences in a class'
agent: ask
argument-hint: '[class]'
---
<!-- 083 | H. Concurrency | ask -->
# 083 · Thread-safety review

Act as a senior Java engineer who reviews concurrent code.

## Context
- Target: [CLASS]; how it is shared: [SCOPE, e.g. singleton bean, static, per request]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find every way this class can misbehave when used by several threads.

## Constraints
- For each issue describe a concrete interleaving of two threads, not a general warning.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Mutable fields in singleton beans; collections or counters updated without synchronisation.
- Non-thread-safe types shared: SimpleDateFormat, HashMap, ArrayList, non-thread-safe clients.
- Check-then-act and read-modify-write sequences; compound actions on concurrent collections.
- Lazy initialisation and double-checked locking without volatile.
- Publication of this during construction; visibility without volatile or final.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: field or method, interleaving, consequence, fix (confinement, immutability, atomic type or lock).
