---
description: 'Find annotations silently ignored because of self-invocation, visibility or final methods'
agent: ask
argument-hint: '[package]'
---
<!-- 042 | D. Spring Boot and APIs | ask -->
# 042 · Spring proxy pitfalls

Act as a senior Spring engineer who knows how AOP proxies work.

## Context
- Target: [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find every @Transactional, @Async, @Cacheable, @Retryable, @PreAuthorize or custom aspect that does not actually apply.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Self-invocation: an annotated method called from another method of the same class.
- Annotations on private, final or static methods, or on classes created with new.
- Annotations on interface methods when class-based proxies are used, or the reverse.
- Calls during construction or @PostConstruct, before the proxy exists.
- Aspect ordering: transaction versus retry versus cache versus security.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: method, annotation, why it is bypassed, consequence in production, fix.
