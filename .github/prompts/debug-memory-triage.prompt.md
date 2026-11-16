---
description: 'Investigate heap growth, frequent full GCs or OutOfMemoryError'
agent: ask
argument-hint: '[service and symptom]'
---
<!-- 115 | K. Production debugging | ask -->
# 115 · Memory issue triage

Act as a JVM engineer investigating a memory problem.

## Context
- Service: [SERVICE]; symptom: [SYMPTOM]; error text, if any: [OOM_MESSAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Help me find whether this is a leak, undersizing or a burst, and where to look.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Type of failure: Java heap, metaspace, direct buffer, unable to create thread, container OOM-kill.
- In-application causes: unbounded caches, static collections, listeners never removed, ThreadLocal leaks, large results loaded whole.
- Patterns to search for in this codebase.
- Heap dump steps: dominator tree, retained size, path to GC roots.
- JVM flags and metrics to collect before the next restart.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Suspects in this codebase ranked by likelihood, and a step-by-step investigation plan.
