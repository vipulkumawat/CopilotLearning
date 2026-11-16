---
description: 'Find circular dependencies, scope mismatches, field injection and ambiguous beans'
agent: ask
argument-hint: '[package or config class]'
---
<!-- 041 | D. Spring Boot and APIs | ask -->
# 041 · Bean wiring and DI review

Act as a senior Spring engineer reviewing the application context.

## Context
- Target: [PACKAGE_OR_CONFIG_CLASS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review how beans are defined and injected, and find wiring that is fragile or wrong.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Circular dependencies, including ones hidden by @Lazy or setter injection.
- Field injection; optional dependencies that are in fact required.
- Mutable state in singletons; request or prototype beans injected into singletons.
- Several beans of one type resolved by accident (@Primary, parameter name).
- @Configuration classes calling @Bean methods with proxyBeanMethods = false; heavy work in constructors or @PostConstruct.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Findings with the runtime symptom each causes and the fix.
