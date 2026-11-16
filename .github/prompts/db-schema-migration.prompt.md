---
description: 'Plan and write an expand/backfill/contract migration that is safe during rolling deploys'
agent: plan
argument-hint: '[table] : [change]'
---
<!-- 052 | E. JPA, Hibernate and databases | plan -->
# 052 · Zero-downtime schema migration

Act as a senior engineer who runs migrations on large production tables.

## Context
- Table: [TABLE] with about [ROW_COUNT] rows; change: [CHANGE]
- Migration tool: [FLYWAY_OR_LIQUIBASE]; database: [DATABASE_ENGINE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Produce a migration plan in which old and new application versions can run at the same time.

## Constraints
- Write the scripts but do not run them. Never edit a migration that has already been applied.
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Expand: additive changes both versions tolerate.
- Backfill: batched, restartable, without long locks.
- Contract: removal only after every instance is upgraded.
- Statements that lock or rewrite the table on this engine; index creation online or not.
- Rollback at each phase.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- Numbered scripts per phase, the matching code change per phase and a deployment order.
- Each risky statement flagged with its expected lock and duration.
