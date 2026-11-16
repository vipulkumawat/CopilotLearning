---
description: 'Choose between partitioning, multi-threaded steps and remote chunking for a step'
agent: plan
argument-hint: '[step name]'
---
<!-- 077 | G. Spring Batch | plan -->
# 077 · Partitioning and parallelism

Act as a senior engineer scaling a Spring Batch step.

## Context
- Step: [STEP_NAME]; volume: [VOLUME]; current duration: [DURATION]; target: [TARGET_DURATION]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Evaluate whether and how to parallelise the step, and recommend one option.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Data volume and key distribution: can it be split evenly?
- Ordering requirements between records.
- Database contention, connection pool limits and downstream rate limits.
- Thread safety of reader, processor and writer; restartability with multi-threaded steps.
- Whether the real bottleneck is I/O that parallelism will not fix.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A comparison table of the options, the recommendation and the new failure modes it introduces.
