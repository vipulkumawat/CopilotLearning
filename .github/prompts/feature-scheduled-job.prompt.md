---
description: 'Add a scheduled task that is safe on multiple instances and observable'
agent: agent
argument-hint: '[what the job does and when]'
---
<!-- 029 | C. Feature development | build -->
# 029 · Scheduled job

Act as a senior Spring Boot engineer.

## Context
- Job: [JOB_DESCRIPTION]; schedule: [CRON_AND_ZONE]
- Instances running in production: [INSTANCE_COUNT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Add the scheduled job so that it runs once per schedule across all instances and can fail safely.

## Constraints
- Use the project's existing lock mechanism (for example ShedLock); the cron and zone come from configuration.
- Work in bounded pages; keep transactions short.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Two instances firing together; a run that outlasts the next trigger.
- Failure half-way: the rerun must not double-apply.
- Missed run after downtime; daylight-saving change.
- Nothing to process.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Tests for the unit of work and its idempotency; a metric for last success, duration and items processed.
- A way to trigger and to disable the job manually.
