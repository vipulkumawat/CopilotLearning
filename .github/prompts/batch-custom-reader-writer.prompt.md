---
description: 'Implement a custom batch component that is restartable, transactional and testable'
agent: agent
argument-hint: '[component purpose]'
---
<!-- 079 | G. Spring Batch | build -->
# 079 · Custom ItemReader, ItemProcessor or ItemWriter

Act as a senior Spring Batch engineer.

## Context
- Component: [READER_PROCESSOR_OR_WRITER] for [PURPOSE]
- Source or target system: [SYSTEM]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Implement the component, preferring an existing Spring Batch implementation if one fits.

## Constraints
- Step-scoped where it uses job parameters; state kept through ItemStream, not in fields that survive between runs.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- End of input; empty input; restart from the last committed position.
- Exception part-way through a chunk and the rollback that follows.
- Processor returning null to filter an item.
- Writer receiving an empty chunk; partial failure in a bulk write.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Unit tests including an open/update/close restart cycle, and a step-level test.
