---
description: 'Locate a bug, reproduce it with a failing test, then propose the minimal fix'
agent: agent
argument-hint: '[bug description and steps]'
---
<!-- 111 | K. Production debugging | build -->
# 111 · Bug reproduction first

Act as a senior engineer who fixes causes, not symptoms.

## Context
- Bug report: [DESCRIPTION_AND_STEPS]
- Expected versus actual: [EXPECTED] / [ACTUAL]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find the responsible code path, write a failing test for it, then propose the smallest fix.

## Constraints
- Do not fix anything until the test fails for the reason described in the report.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- The lowest level at which the bug can be reproduced.
- Other inputs that hit the same defect.
- Callers relying on the current (wrong) behaviour.
- Existing bad data created by the bug that needs repair.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- The failing test, then the fix, with an explanation of why it removes the cause.
- All existing tests still pass; say exactly which commands you ran.
