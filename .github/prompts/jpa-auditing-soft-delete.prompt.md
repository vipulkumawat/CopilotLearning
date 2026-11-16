---
description: 'Add created/modified auditing or soft delete without breaking queries and constraints'
agent: agent
argument-hint: '[entity or entities]'
---
<!-- 060 | E. JPA, Hibernate and databases | build -->
# 060 · Auditing and soft delete

Act as a senior JPA engineer.

## Context
- Entities: [ENTITIES]; requirement: [AUDIT_FIELDS_AND_OR_SOFT_DELETE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Add auditing and/or soft delete in the way this project already does it, or propose one consistent mechanism.

## Constraints
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Who the "current user" is for requests, Kafka consumers, batch jobs and scheduled tasks.
- Soft-deleted rows in unique constraints, joins, counts and native queries.
- Bulk updates and deletes bypassing listeners.
- Restoring a deleted row; hard-delete obligations (data retention).
- Time source and time zone of the audit timestamps.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Migration scripts, and tests proving deleted rows are invisible to normal queries and audit fields are set on each write path.
