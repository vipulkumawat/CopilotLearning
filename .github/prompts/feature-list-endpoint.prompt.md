---
description: 'Add a list endpoint with filtering, sorting and server-enforced paging'
agent: agent
argument-hint: '[resource] filtered by [fields]'
---
<!-- 024 | C. Feature development | build -->
# 024 · Paginated, filtered list endpoint

Act as a senior Spring Boot and JPA engineer.

## Context
- Resource: [RESOURCE]; filters: [FILTER_FIELDS]; default sort: [DEFAULT_SORT]
- Expected table size: [ROW_COUNT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Add a list endpoint with filtering and pagination that stays fast at production volume.

## Constraints
- Spring Data Pageable with a maximum page size enforced server-side.
- Whitelist sortable fields; anything else returns 400.
- Return a projection or DTO; never load unbounded collections or entities with eager graphs.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Default paging; page beyond the end; maximum page size exceeded.
- Invalid sort field; invalid filter value; no filters; empty result.
- Count query cost on a large table; deep-offset paging.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Tests for each case; the generated SQL shown for one filtered request.
- Confirmation that the query uses an index, or the index that must be added.
