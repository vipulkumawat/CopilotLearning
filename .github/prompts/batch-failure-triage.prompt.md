---
description: 'Diagnose a failed or stuck job execution from logs and the job repository'
agent: ask
argument-hint: '[job name and failure details]'
---
<!-- 081 | G. Spring Batch | ask -->
# 081 · Failed job triage

Act as a senior engineer supporting batch jobs in production.

## Context
- Job: [JOB_NAME]; execution id or run date: [EXECUTION]
- Exit description or log: [PASTE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find why the execution failed or hangs, and tell me whether it is safe to restart.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- The failing step, item and exception; data problem or system problem.
- What was committed before the failure.
- An execution left in STARTED after a crash, blocking the next launch.
- Whether a restart resumes or repeats work, and whether repeats are harmless.
- Downstream jobs or consumers that already acted on partial output.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Root cause with evidence, a restart or repair procedure, and the queries on the BATCH_ tables I should run to confirm.
