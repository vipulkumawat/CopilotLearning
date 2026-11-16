---
description: 'Map an unfamiliar module - entry points, layers, data stores, integrations and risk areas'
agent: ask
argument-hint: '[module or package]'
---
<!-- 001 | A. Understand the codebase | ask -->
# 001 · Codebase tour of a module

Act as a senior Java engineer onboarding a new teammate onto this codebase.

## Context
- Module or package: [MODULE]
- I know Java and Spring but not this code, and I need to be productive in it within a day.
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Produce a guided tour of the module: what it does in business terms, how it is structured, and where the risk is.

## Constraints
- Describe what the code does today, not what the names suggest it should do.
- No file-by-file listing; only what a newcomer needs.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Entry points: REST controllers, Kafka listeners, schedulers, batch jobs.
- The main classes in each layer, and where the layering is violated.
- Data stores, entities and outbound integrations (HTTP, Kafka, files).
- Cross-cutting concerns: security, transactions, caching, error handling.
- The five places where a change is most likely to break something, and why.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A one-page summary, a Mermaid component diagram and an ordered "read these 10 files first" list.
- A list of questions you could not answer from the code.
