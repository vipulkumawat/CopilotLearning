---
description: 'Test custom queries against the production database engine with real migrations'
agent: agent
argument-hint: '[repository]'
---
<!-- 100 | J. Testing | write -->
# 100 · Repository integration tests with Testcontainers

Act as a senior engineer who does not trust H2 to behave like production.

## Context
- Repository: [REPOSITORY]; production database: [DATABASE_ENGINE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write integration tests for the repository's custom queries against a real database.

## Constraints
- One container reused across tests; schema created by the real Flyway or Liquibase migrations, not Hibernate auto-DDL.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Every custom JPQL, native and derived query with data that matches and data that must not match.
- Pagination and sorting, including ties.
- Constraints: unique, not-null and foreign keys actually enforced.
- Null parameters and empty collections.
- An index-usage or query-count check where it matters.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Tests are independent of execution order and clean up their own data.
