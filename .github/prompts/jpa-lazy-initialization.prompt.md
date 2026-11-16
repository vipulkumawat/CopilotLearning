---
description: 'Diagnose lazy-loading failures and decide where data should be fetched'
agent: ask
argument-hint: '[stack trace or endpoint]'
---
<!-- 054 | E. JPA, Hibernate and databases | ask -->
# 054 · LazyInitializationException and open-session-in-view

Act as a senior Hibernate engineer.

## Context
- Failure or endpoint: [STACK_TRACE_OR_ENDPOINT]
- spring.jpa.open-in-view setting: [VALUE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Explain why the association is accessed outside a session and where the data should be loaded instead.

## Constraints
- Do not recommend EAGER fetching or enabling open-in-view as the fix.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Entities returned from the service and serialised by the controller.
- Access from @Async methods, event listeners, Kafka listeners or scheduled tasks.
- Detached entities held in caches or the HTTP session.
- Queries hidden by open-in-view running during view rendering.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- The exact access that fails, and a fix based on a fetch plan or a DTO built inside the transaction.
