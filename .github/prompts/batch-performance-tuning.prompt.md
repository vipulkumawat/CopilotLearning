---
description: 'Find the bottleneck of a job from its configuration, queries and step statistics'
agent: ask
argument-hint: '[job name]'
---
<!-- 078 | G. Spring Batch | ask -->
# 078 · Batch performance tuning

Act as a senior engineer tuning batch throughput.

## Context
- Job: [JOB_NAME]; step durations and counts: [STEP_STATISTICS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Estimate the likely bottleneck of each step and rank the changes by expected impact.

## Constraints
- Analysis from code, configuration and database only; no code changes yet.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Chunk size versus memory and transaction duration.
- Reader fetch size, and whether it is actually applied by the driver.
- Writer using JDBC batch statements; JPA writer flushing row by row.
- Row-by-row lookups in the processor that should be preloaded or joined.
- Indexes needed by the reader query; job repository overhead.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Per step: suspected bottleneck, evidence, change, expected gain, how to measure it.
