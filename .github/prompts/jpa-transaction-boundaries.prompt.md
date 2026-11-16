---
description: 'Review @Transactional placement, propagation, rollback rules and long transactions'
agent: ask
argument-hint: '[package]'
---
<!-- 049 | E. JPA, Hibernate and databases | ask -->
# 049 · Transaction boundary review

Act as a senior Spring and JPA engineer reviewing data consistency.

## Context
- Target: [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review every @Transactional method and report where the boundary is wrong, too wide or ineffective.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Correct layer, and called through the Spring proxy (no self-invocation, not private).
- Transaction held open during outbound HTTP, Kafka sends or slow computation.
- Propagation and isolation choices; REQUIRES_NEW used to "save a log" and its deadlock risk.
- Checked exceptions that do not roll back; exceptions caught inside the transaction that leave it rollback-only.
- readOnly used where appropriate; writes with no transaction at all.
- Several repository calls that should be one atomic unit.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: method, finding, production risk, fix.
