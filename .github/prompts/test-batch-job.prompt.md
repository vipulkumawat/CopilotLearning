---
description: 'Test a job and its steps with spring-batch-test, including restart'
agent: agent
argument-hint: '[job name]'
---
<!-- 106 | J. Testing | write -->
# 106 · Spring Batch job tests

Act as a senior engineer testing batch jobs.

## Context
- Job: [JOB_NAME]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write tests for the job at step and job level against a real database.

## Constraints
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Happy path with read, write and filter counts asserted.
- Skippable bad record: skip count and reject record asserted.
- Fatal failure mid-step, then restart: no duplicates and the correct final state.
- Empty input.
- Step-scoped components tested with job parameters.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Job repository tables cleaned between tests; assertions on exit status and on the data written.
