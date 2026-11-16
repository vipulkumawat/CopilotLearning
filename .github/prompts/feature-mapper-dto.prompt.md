---
description: 'Create DTOs and a mapper between API, domain and entity models'
agent: agent
argument-hint: '[source type] -> [target type]'
---
<!-- 028 | C. Feature development | build -->
# 028 · DTOs and mapper

Act as a senior Java engineer who keeps layers decoupled.

## Context
- Map between: [SOURCE_TYPE] and [TARGET_TYPE]
- Mapping approach used in this project: [MAPSTRUCT_OR_MANUAL]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Create the DTOs and the mapper, making every non-trivial field mapping explicit.

## Constraints
- No lazy associations triggered by mapping; no entity references inside DTOs.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Null source, null nested object, empty collections.
- Fields with different names, types or units; enums with different value sets.
- Fields that must never be mapped inbound (id, version, audit fields, owner).
- Unmapped target fields must fail the build or a test, not pass silently.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A mapper test asserting every field in both directions, including the ignored ones.
