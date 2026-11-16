---
description: 'Review HikariCP configuration and find connection leaks or exhaustion causes'
agent: ask
argument-hint: '[service, plus error or metrics if any]'
---
<!-- 058 | E. JPA, Hibernate and databases | ask -->
# 058 · Connection pool sizing and leak review

Act as a senior engineer who has debugged pool exhaustion.

## Context
- Service: [SERVICE]; symptom or metrics: [SYMPTOM]
- Instances: [INSTANCE_COUNT]; database connection limit: [DB_MAX_CONNECTIONS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Determine whether the pool is correctly sized and whether connections are held too long or leaked.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- maximumPoolSize times instances versus the database limit; pool size versus request and consumer thread counts.
- connectionTimeout, maxLifetime, idle and keep-alive settings versus network and database timeouts.
- Connections held during outbound calls, long transactions or open-in-view.
- Code obtaining connections manually without closing; nested REQUIRES_NEW needing two connections.
- Leak detection threshold and pool metrics.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- The likely cause with evidence, recommended settings with the reasoning, and the metric that proves the fix.
