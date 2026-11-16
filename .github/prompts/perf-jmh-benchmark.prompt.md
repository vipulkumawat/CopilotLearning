---
description: 'Write a JMH benchmark comparing implementations without the usual measurement mistakes'
agent: agent
argument-hint: '[code to benchmark and alternatives]'
---
<!-- 095 | I. Performance and JVM | write -->
# 095 · JMH micro-benchmark

Act as a performance engineer who knows JMH pitfalls.

## Context
- Code under test: [METHOD]; alternatives to compare: [ALTERNATIVES]
- Realistic input sizes: [SIZES]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write a JMH benchmark that compares the alternatives fairly.

## Constraints
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Dead-code elimination (use the result or a Blackhole) and constant folding (inputs from @State).
- Warm-up, forks and iteration settings; @Param for input sizes.
- Setup cost kept out of the measured method.
- Realistic data distribution, not only the best case.
- Allocation profiling with the GC profiler.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- The benchmark class, the command to run it and guidance on reading the result, including when the difference is noise.
