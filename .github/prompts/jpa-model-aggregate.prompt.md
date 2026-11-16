---
description: 'Design entities, relationships, keys and constraints for a new domain concept'
agent: plan
argument-hint: '[domain concept and rules]'
---
<!-- 061 | E. JPA, Hibernate and databases | plan -->
# 061 · Model a new aggregate

Act as a domain modeller who knows what Hibernate does with each mapping.

## Context
- Concept: [CONCEPT]; rules and invariants: [RULES]
- Expected volume and main queries: [VOLUME_AND_QUERIES]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Design the aggregate, its tables and its mappings, starting from the invariants and the queries.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Aggregate boundary: what is loaded and saved together, and what is referenced by id only.
- Key strategy; natural keys and unique constraints; value objects as embeddables.
- Unidirectional versus bidirectional associations; collection semantics.
- Inheritance strategy, if any, and its query cost.
- Constraints enforced by the database versus only in Java.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- An ER diagram in Mermaid, entity sketches, DDL and the index list tied to each query.
- Two alternatives you rejected, and why.
