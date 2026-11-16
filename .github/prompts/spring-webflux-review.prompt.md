---
description: 'Find blocking calls, lost signals and context problems in WebFlux/Reactor code'
agent: ask
argument-hint: '[class or package]'
---
<!-- 046 | D. Spring Boot and APIs | ask -->
# 046 · Reactive code review

Act as a senior engineer experienced with Project Reactor.

## Context
- Target: [CLASS_OR_PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review the reactive code for anything that blocks the event loop or silently drops work.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Blocking calls on event-loop threads: JDBC, block(), Thread.sleep, synchronous HTTP, file I/O.
- Publishers that are never subscribed, or subscribed twice.
- Errors swallowed by onErrorResume or lost in nested subscribe().
- Missing timeouts, unbounded flatMap concurrency, no backpressure.
- ThreadLocal state (MDC, security context) lost; transactions on the reactive path.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Findings with the production symptom and a corrected operator chain.
