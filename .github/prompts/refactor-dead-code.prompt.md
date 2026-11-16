---
description: 'Find code, endpoints, properties and dependencies that are provably unused'
agent: ask
argument-hint: '[module]'
---
<!-- 128 | L. Security and code quality | ask -->
# 128 · Dead code and unused configuration report

Act as a senior engineer cleaning up safely.

## Context
- Scope: [MODULE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Report what can be deleted, with the evidence that it is unused.

## Constraints
- Consider reflection, Spring component scanning, bean names, SpEL, serialisation, configuration and external callers before declaring anything dead.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Unreferenced classes, methods and constants.
- Feature flags that are permanently on or off, and the branches they kill.
- Unused properties, beans, dependencies and database columns.
- Endpoints or listeners with no known caller (flag these as "verify with traffic data").

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Three lists: safe to delete, probably dead (needs runtime evidence), keep. Delete nothing.
