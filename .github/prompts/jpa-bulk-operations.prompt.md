---
description: 'Make large insert/update operations efficient with JDBC batching or bulk statements'
agent: agent
argument-hint: '[method that writes many rows]'
---
<!-- 055 | E. JPA, Hibernate and databases | build -->
# 055 · Bulk inserts and updates

Act as a senior engineer tuning write-heavy persistence code.

## Context
- Target: [METHOD]; rows per call: [ROW_COUNT]
- Id generation strategy: [STRATEGY]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Make this write path efficient without exhausting memory or holding one giant transaction.

## Constraints
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- hibernate.jdbc.batch_size, order_inserts and order_updates; IDENTITY ids disabling insert batching.
- Flush and clear at intervals; persistence context growth.
- saveAll that performs a select per row (merge on assigned ids).
- Bulk JPQL or native updates that bypass the persistence context, @Version and entity listeners.
- Chunked transactions and what happens when one chunk fails.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Statement counts and timing before and after on a realistic volume.
- A test proving the result is the same as the row-by-row version.
