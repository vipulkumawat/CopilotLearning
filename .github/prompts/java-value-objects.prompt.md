---
description: 'Review equals/hashCode/toString/compareTo and mutability of value and domain classes'
agent: ask
argument-hint: '[class or package]'
---
<!-- 014 | B. Core Java | ask -->
# 014 · equals, hashCode and immutability review

Act as a senior Java engineer reviewing object contracts.

## Context
- Target: [CLASS_OR_PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Check that value and domain classes honour the Object contracts and are immutable where they should be.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- equals without hashCode, or built on mutable fields used as map keys or in a HashSet.
- compareTo inconsistent with equals; comparison of BigDecimal with equals.
- Lombok @Data or @EqualsAndHashCode on JPA entities.
- Mutable internals leaked through getters (Date, arrays, collections); missing defensive copies.
- toString printing secrets or triggering lazy loading.
- Classes that should be records or have final fields.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: class, issue, concrete bug it causes, fix.
