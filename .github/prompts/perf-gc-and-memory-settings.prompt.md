---
description: 'Interpret GC behaviour and review heap and container memory settings'
agent: ask
argument-hint: '[paste GC log summary and JVM flags]'
---
<!-- 094 | I. Performance and JVM | ask -->
# 094 · GC log and JVM memory settings review

Act as a JVM performance engineer.

## Context
- JVM flags: [FLAGS]; container memory limit: [LIMIT]; Java version: [JAVA_VERSION]
- GC log extract or metrics: [PASTE]; symptom: [SYMPTOM]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Explain what the garbage collector is doing and whether the memory settings fit the container.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Allocation rate, pause times, promotion rate and old-generation growth after full GC.
- Heap versus container limit: metaspace, thread stacks, direct buffers and native memory (OOM-killed with heap free).
- Collector choice for this latency or throughput goal.
- Humongous allocations, premature promotion, explicit System.gc().
- Whether the cause is the application (leak, burst) rather than tuning.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A diagnosis with evidence, recommended flags with reasons, and the metrics to watch after the change.
