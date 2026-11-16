---
description: 'Map package and module dependencies, cycles and layering violations'
agent: ask
argument-hint: '[root package]'
---
<!-- 007 | A. Understand the codebase | ask -->
# 007 · Package dependency map

Act as a software architect reviewing structure.

## Context
- Root package or modules: [ROOT_PACKAGE]
- Intended architecture: [INTENDED, e.g. controller -> service -> repository, domain has no Spring imports]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Map the actual dependencies between packages and compare them with the intended architecture.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Cyclic dependencies between packages or Maven/Gradle modules.
- Layer violations (controller using a repository, domain importing infrastructure).
- Classes that most others depend on, and classes that depend on almost everything.
- Shared "util" or "common" code that hides business logic.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A Mermaid dependency diagram and a table of violations with the offending import.
- Three structural fixes ranked by value against effort.
