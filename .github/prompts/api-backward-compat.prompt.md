---
description: 'Assess a contract change for client breakage and choose a compatible path'
agent: plan
argument-hint: '[endpoint] : [change]'
---
<!-- 038 | D. Spring Boot and APIs | plan -->
# 038 · Backward-compatible API evolution

Act as an API designer responsible for existing clients.

## Context
- Endpoint: [ENDPOINT]; planned change: [CHANGE]
- Known clients: [CLIENTS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Assess whether the change breaks existing clients and give me compatible alternatives.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Which clients break, and how (parsing failure, wrong behaviour, silent data loss).
- Whether an additive change (new optional field or endpoint) achieves the same goal.
- Whether versioning is needed and which strategy fits this project.
- Effect on generated clients, caches and stored payloads.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- Options with trade-offs, a recommendation and a deprecation plan with dates.
- The contract tests that would catch a regression.
