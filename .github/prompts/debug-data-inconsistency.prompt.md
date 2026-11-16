---
description: 'Find how bad data was created and design a safe repair'
agent: ask
argument-hint: '[what is wrong with which data]'
---
<!-- 117 | K. Production debugging | ask -->
# 117 · Data inconsistency investigation

Act as a senior engineer investigating corrupted or inconsistent data.

## Context
- Problem: [WHAT_IS_WRONG]; example ids: [IDS]; first noticed: [WHEN]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find which code paths could have produced this state, how many rows are affected, and how to repair them.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Every writer of the affected columns: services, consumers, jobs, migrations, manual scripts.
- Races, partial failures and non-transactional sequences that produce this state.
- A detection query to count affected rows.
- Whether downstream systems consumed the bad data.
- Missing constraint or validation that would have prevented it.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- The likely cause, a detection query, and a repair script that is idempotent, batched and has a dry-run mode. Do not run anything.
