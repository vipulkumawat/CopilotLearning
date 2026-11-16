---
description: 'Implement a feature with the smallest change set, after an approved plan'
agent: agent
argument-hint: '[feature description]'
---
<!-- 021 | C. Feature development | build -->
# 021 · Plan-first feature implementation

Act as a senior Java engineer working in an existing layered Spring Boot application.

## Context
- Feature: [FEATURE_DESCRIPTION]
- Acceptance criteria: [ACCEPTANCE_CRITERIA]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Analyse the existing architecture (controller, service, repository, domain), propose the smallest change set, then implement it.

## Constraints
- Reuse existing services, validators and mappers before creating new ones.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Happy path, each validation failure, unauthorised caller.
- Behaviour when a dependency fails mid-way; what is rolled back.
- Concurrent requests for the same resource.
- Existing data that does not satisfy the new rules.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Unit tests for new logic and one slice or integration test per new entry point.
- A short summary mapping each acceptance criterion to the test that proves it.
