---
description: 'Find NullPointerException risks and unclear null contracts'
agent: ask
argument-hint: '[class or package]'
---
<!-- 011 | B. Core Java | ask -->
# 011 · Null-safety review

Act as a senior Java engineer reviewing null handling.

## Context
- Target: [CLASS_OR_PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find where null can appear unexpectedly and where the null contract of an API is unclear.

## Constraints
- Prefer fixing the contract (non-null by default, validation at the boundary) over scattering null checks.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Return values that can be null without saying so; Optional used as a field or parameter.
- Unboxing of nullable wrappers; chained getters on entities, maps and external responses.
- Optional.get() without a check; orElse(expensiveCall()) evaluated eagerly.
- Collections returned as null instead of empty.
- Null from JPA queries, Map.get, getBody() of HTTP responses and deserialised JSON.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: location, how null gets there, consequence, suggested fix.
