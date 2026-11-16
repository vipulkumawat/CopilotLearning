---
description: 'Trace one request or message from entry point to database, events and response'
agent: ask
argument-hint: '[endpoint, listener or job]'
---
<!-- 002 | A. Understand the codebase | ask -->
# 002 · Trace a request end to end

Act as a senior Java engineer tracing a production flow.

## Context
- Entry point: [ENDPOINT_OR_LISTENER]
- Scenario to trace: [SCENARIO, e.g. "customer places an order with two items"]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Trace the scenario step by step from the entry point to every side effect and the final response.

## Constraints
- Follow the real call path, including filters, interceptors, aspects and event listeners that are not visible in the method body.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Validation, authentication and authorisation steps, in order.
- Where each transaction starts and ends, and what runs inside it.
- Every database read and write, Kafka publish, outbound HTTP call and cache access.
- The path taken when validation fails, when a dependency times out and when the transaction rolls back.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A numbered step list (class.method per step) and a Mermaid sequence diagram.
- A table of side effects: what, where, inside which transaction, reversible or not.
