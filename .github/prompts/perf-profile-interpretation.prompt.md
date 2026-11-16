---
description: 'Interpret a flame graph, JFR summary or hot-method list and map it to code'
agent: ask
argument-hint: '[paste profiler output]'
---
<!-- 097 | I. Performance and JVM | ask -->
# 097 · Profiler output interpretation

Act as a performance engineer reading a profile.

## Context
- Profile: [PASTE_HOT_METHODS_OR_JFR_SUMMARY]; type: [CPU_ALLOCATION_LOCK_OR_WALL_CLOCK]
- Workload when it was captured: [WORKLOAD]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Tell me what the profile says the time or memory goes on, mapped to this codebase.

## Constraints
- Distinguish self time from total time, and say what this profile type cannot show.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Top consumers and the application code that calls them.
- Framework overhead versus our own code.
- Lock contention and thread parking; time blocked on I/O.
- Allocation hotspots and the types allocated.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- The three most valuable optimisations with the expected effect, and the next measurement to take.
