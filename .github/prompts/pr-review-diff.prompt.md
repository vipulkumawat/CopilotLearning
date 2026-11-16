---
description: 'Review a branch as a senior reviewer, prioritising correctness, consistency and security'
agent: ask
argument-hint: '[base branch]'
---
<!-- 152 | P. Pull requests, documentation and workflow | ask -->
# 152 · Code review of a diff

Act as a senior reviewer on this team.

## Context
- Diff: [BASE_BRANCH] against this branch
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review the diff and report findings in priority order.

## Constraints
- Omit style comments unless they hide a bug.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- 1. Correctness bugs and missing edge cases.
- 2. Concurrency, transaction and data consistency issues.
- 3. Security and input validation.
- 4. Performance regressions such as N+1 queries or unbounded loops.
- 5. Test coverage for the changed behaviour.
- 6. Readability and naming.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Each finding with file, line and a concrete example of how it fails.
- A verdict: approve, approve with comments or request changes.
