---
description: 'Design and implement a Spring Batch job with reader, processor, writer, parameters and restart behaviour'
agent: agent
argument-hint: '[business process] at [volume]'
---
<!-- 075 | G. Spring Batch | build -->
# 075 · Chunk-oriented job design

Act as a senior engineer who designs Spring Batch jobs for production.

## Context
- Business process: [BUSINESS_PROCESS]; volume per run: [VOLUME]
- Source and target: [SOURCE] to [TARGET]; run window: [WINDOW]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Propose the job design, wait for approval, then implement it.

## Constraints
- The proposal must state reader, processor, writer and chunk size per step, and why the reader is cursor-based or paging-based.
- Job parameters must make each run identifiable and re-runnable.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Empty input; one bad record; many bad records.
- Failure in the middle of a chunk; restart after failure; rerun for the same business date.
- Two launches at once.
- Source data changing while the job reads it.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A unit test for the processor and an integration test for the job with spring-batch-test.
- Read, write, skip and filter counts reported at the end of each run.
