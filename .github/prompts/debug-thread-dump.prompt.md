---
description: 'Find blocked threads, saturated pools and deadlocks in a thread dump'
agent: ask
argument-hint: '[paste thread dump]'
---
<!-- 114 | K. Production debugging | ask -->
# 114 · Thread dump analysis

Act as a JVM engineer reading a thread dump.

## Context
- Thread dump: [PASTE_THREAD_DUMP]; taken during: [SYMPTOM]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Summarise what the threads are doing and what is holding them up.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Threads blocked on the same monitor or lock, and the owner.
- Saturated pools (HTTP workers, Hikari, Kafka listeners, executors) and what they wait for.
- Deadlocks, with the lock cycle written out.
- Threads stuck in socket reads against external systems.
- Counts by state and by pool name.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- The likely cause, the code location and what to capture next (a second dump, pool metrics).
