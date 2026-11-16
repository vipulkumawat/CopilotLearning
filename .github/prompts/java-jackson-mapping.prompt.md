---
description: 'Review Jackson configuration and DTO mapping for contract and data-loss problems'
agent: ask
argument-hint: '[DTO package or ObjectMapper config]'
---
<!-- 019 | B. Core Java | ask -->
# 019 · JSON mapping review

Act as a senior Java engineer reviewing JSON contracts.

## Context
- Target: [DTO_PACKAGE_OR_CONFIG]
- Consumers of this JSON: [CONSUMERS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Check that what is serialised and deserialised matches the intended contract.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- More than one ObjectMapper with different settings (Spring-managed versus new ObjectMapper()).
- Unknown-property, null-inclusion and date-format settings; BigDecimal and long precision for JavaScript clients.
- Enums serialised by name with no handling of unknown values.
- Entities serialised directly: lazy loading, cycles, leaked internal fields.
- Polymorphic typing (@JsonTypeInfo) and its security implications.
- Records, Lombok builders and constructors that Jackson cannot bind.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table of issues with an example payload showing each problem.
- Serialisation round-trip tests to add for the critical DTOs.
