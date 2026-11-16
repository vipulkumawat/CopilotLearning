---
description: 'Review fetch types, cascades, equals/hashCode, bidirectional sync and missing indexes'
agent: ask
argument-hint: '[entity package]'
---
<!-- 050 | E. JPA, Hibernate and databases | ask -->
# 050 · Entity mapping review

Act as a senior Hibernate engineer reviewing a domain model.

## Context
- Target: entities in [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review the mappings for correctness and for performance traps.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- EAGER on collections or @ManyToOne/@OneToOne left at the default; unintended lazy behaviour.
- Cascade and orphanRemoval settings versus real aggregate ownership.
- equals and hashCode safe with proxies, generated ids and HashSets; Lombok @Data on entities.
- Bidirectional associations not kept in sync; List where Set is intended.
- Enums stored as ORDINAL; column lengths, nullability and precision that disagree with the schema.
- Indexes implied by repository query methods but absent.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Findings by severity with the suggested mapping change and the migration it needs.
