---
description: 'Find why a test fails intermittently and how to make it deterministic'
agent: ask
argument-hint: '[test class or failure log]'
---
<!-- 105 | J. Testing | ask -->
# 105 · Flaky test diagnosis

Act as a senior engineer who fixes flaky tests at the cause.

## Context
- Test: [TEST_CLASS_OR_METHOD]; failure output: [PASTE]; fails roughly: [FREQUENCY]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find the source of nondeterminism and propose a deterministic fix.

## Constraints
- Retrying the test or adding sleeps is not a fix.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Shared state: static fields, database rows, Spring context cached between tests, ports, files.
- Timing: sleeps, asynchronous work not awaited, timeouts too tight for CI.
- Dependence on current time, time zone, locale, ordering of sets or maps, or random data.
- Test execution order and parallel execution.
- A real race in the production code that the test is exposing.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- The cause with evidence, the fix, and how to prove it (run count or forced interleaving).
