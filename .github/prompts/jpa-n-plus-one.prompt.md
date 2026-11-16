---
description: 'Find N+1 queries in a method or endpoint and fix them with the right fetch strategy'
agent: agent
argument-hint: '[service method or endpoint]'
---
<!-- 048 | E. JPA, Hibernate and databases | build -->
# 048 · N+1 query detection and fix

Act as a senior Java engineer who specialises in Hibernate performance.

## Context
- Target: [SERVICE_METHOD_OR_ENDPOINT]
- Typical number of parent rows returned: [ROW_COUNT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Walk the entity relationships and fetch types on this path, identify every lazy association touched in a loop or during serialisation, and fix it.

## Constraints
- Compare JOIN FETCH, @EntityGraph, a DTO projection and batch fetching, and justify the one you choose.
- Do not switch associations to EAGER.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Associations touched by mappers, toString, equals or JSON serialisation.
- More than one collection fetched together (Cartesian product, MultipleBagFetchException).
- Join fetch combined with pagination (in-memory paging).
- Other callers of the same repository method that do not need the extra data.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- The SQL before and after, with the statement count for N parents.
- A test that asserts the number of queries, so the problem cannot return.
