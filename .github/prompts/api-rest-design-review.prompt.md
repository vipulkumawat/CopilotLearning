---
description: 'Review resource naming, verbs, status codes, pagination and consistency of controllers'
agent: ask
argument-hint: '[controller or package]'
---
<!-- 039 | D. Spring Boot and APIs | ask -->
# 039 · REST API design review

Act as an API reviewer applying this project's conventions and common REST practice.

## Context
- Target: [CONTROLLER_OR_PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review the API surface for consistency and for surprises a client developer would hit.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Resource naming, nesting and plural forms; verbs hidden in paths.
- Method semantics: safe and idempotent methods that are neither; PUT versus PATCH.
- Status codes for create, async accept, no content, conflict and validation failure.
- Inconsistent pagination, filtering, date formats, id formats and null handling across endpoints.
- Missing Location header, ETag or conditional requests where they matter.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: endpoint, issue, convention it breaks, suggested change, breaking or not.
