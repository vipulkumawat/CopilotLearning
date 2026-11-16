---
description: 'Review how jobs are launched, parameterised, scheduled and protected from concurrent runs'
agent: ask
argument-hint: '[job name or launcher class]'
---
<!-- 082 | G. Spring Batch | ask -->
# 082 · Job launching and scheduling review

Act as a senior engineer reviewing batch operations.

## Context
- Target: [JOB_OR_LAUNCHER]; scheduler: [SCHEDULER, e.g. @Scheduled, Control-M, Kubernetes CronJob]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Check that every launch is intentional, identifiable and safe to repeat.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Identifying versus non-identifying parameters; a timestamp parameter that defeats restart.
- Jobs launched automatically at startup (spring.batch.job.enabled).
- Concurrent launches from several instances.
- Exit codes propagated to the scheduler; alerting on failure and on "did not run".
- Late or missed runs and catch-up behaviour for business dates.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: concern, current behaviour, risk, change.
