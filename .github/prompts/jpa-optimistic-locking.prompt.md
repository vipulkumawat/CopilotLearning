---
description: 'Decide whether an entity needs @Version and add it with conflict handling and a test'
agent: agent
argument-hint: '[entity]'
---
<!-- 051 | E. JPA, Hibernate and databases | build -->
# 051 · Optimistic locking

Act as a senior Java engineer protecting against lost updates.

## Context
- Entity: [ENTITY]
- Who updates it: [ACTORS, e.g. users, batch job, Kafka consumer]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Determine whether concurrent updates can lose data, and if so add optimistic locking end to end.

## Constraints
- Include the migration for the version column and the default for existing rows.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Every code path that reads, modifies and writes the entity, including bulk updates that bypass versioning.
- The business consequence of a lost update here.
- How the conflict is reported to an API client (409) and handled by consumers or jobs (retry?).
- DTO round trips: the version must travel with the data.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A test with two concurrent updates where exactly one succeeds.
- The mapping from OptimisticLockException to the HTTP response.
