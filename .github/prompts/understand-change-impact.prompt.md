---
description: 'Before editing - find callers, tests, contracts and flags affected by a proposed change'
agent: ask
argument-hint: '[method or class] -> [proposed change]'
---
<!-- 004 | A. Understand the codebase | ask -->
# 004 · Change impact analysis

Act as a senior Java engineer assessing the blast radius of a change.

## Context
- Target: [METHOD_OR_CLASS]
- Proposed change: [PROPOSED_CHANGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Determine everything this change can affect before a single line is edited.

## Constraints
- Search usages properly (references, reflection, bean names, SpEL, configuration), not only by text.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- All direct and transitive callers, grouped by entry point.
- Tests that cover this path, and tests that should exist but do not.
- Serialized contracts affected: JSON, Kafka payloads, database columns, cached values.
- Feature flags, profiles or configuration that alter this path.
- Other services or batch jobs that consume the changed data.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A risk table: component, impact, likelihood, mitigation.
- A recommended order of changes and the tests to add first.
