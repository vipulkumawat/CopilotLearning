---
description: 'Scaffold entity, migration, repository, service, DTOs, controller and tests for a new resource'
agent: agent
argument-hint: '[resource and fields]'
---
<!-- 027 | C. Feature development | build -->
# 027 · Vertical slice for a new resource

Act as a senior Spring Boot engineer who follows this project's conventions exactly.

## Context
- Resource: [RESOURCE]; fields, types and constraints: [FIELDS]
- Relationships: [RELATIONSHIPS]; operations needed: [OPERATIONS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Create the full vertical slice for the resource, copying the structure of the closest existing resource.

## Constraints
- Schema changes go through a migration script, never ddl-auto.
- DTOs are separate from the entity; only the operations listed are exposed.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Uniqueness and not-null rules enforced in both validation and the database.
- Update of a missing resource; delete with dependants; concurrent update.
- Pagination on the list operation.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Repository test against a real database, service unit tests, controller slice tests.
- The list of generated files, each mapped to the existing file it was modelled on.
