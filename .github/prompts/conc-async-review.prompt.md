---
description: 'Review CompletableFuture, @Async and executor usage for lost errors, context and timeouts'
agent: ask
argument-hint: '[package]'
---
<!-- 085 | H. Concurrency | ask -->
# 085 · Asynchronous code review

Act as a senior Java engineer reviewing asynchronous code.

## Context
- Target: [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find where asynchronous work can fail silently, hang or run without its context.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Exceptions swallowed in async branches; futures never joined or checked.
- Executor unbounded, unnamed or the common pool used for blocking work; rejection policy.
- MDC, security context, request scope and transaction lost across threads.
- @Async or @Transactional bypassed by self-invocation; @Async returning void.
- join() or get() without a timeout; blocking inside a completion stage.
- Tasks still running at shutdown.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: location, failure mode, how it would show in production, fix.
