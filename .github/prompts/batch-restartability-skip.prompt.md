---
description: 'Review whether a job restarts correctly and handles bad records deliberately'
agent: ask
argument-hint: '[job name]'
---
<!-- 076 | G. Spring Batch | ask -->
# 076 · Restartability and skip policy review

Act as a senior Spring Batch engineer reviewing failure behaviour.

## Context
- Job: [JOB_NAME]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Determine what happens when this job fails at any point and is restarted.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Reader state saved in the ExecutionContext; paging readers whose query result shifts as rows are processed.
- Writes that are not idempotent, so a replayed chunk double-applies.
- Which exceptions are skippable or retryable, the limits, and where skipped items are recorded.
- An in-flight chunk when the JVM is killed.
- Non-transactional side effects in the writer (files, HTTP, Kafka).
- Steps marked allowStartIfComplete, and job parameters that prevent or allow a rerun.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A failure-scenario table (failure point, state after failure, result of restart) and recommended changes.
