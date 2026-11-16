---
description: 'Verify every query and operation is scoped to the caller''s tenant or ownership'
agent: ask
argument-hint: '[module]'
---
<!-- 123 | L. Security and code quality | ask -->
# 123 · Multi-tenant and ownership isolation review

Act as a security engineer checking data isolation.

## Context
- Scope: [MODULE]; isolation rule: [RULE, e.g. every row belongs to a tenant_id taken from the token]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find every path where one tenant or user could read or change another's data.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Repository methods and native queries without the tenant or owner predicate.
- Ids accepted from the client and loaded with findById alone.
- Tenant taken from the request body or a header rather than the authenticated principal.
- Caches, exports, search and batch jobs that ignore the tenant.
- Asynchronous and Kafka paths where the tenant context is lost.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: operation, how isolation is enforced (or not), exploit description, fix.
- A structural recommendation to enforce the rule centrally.
