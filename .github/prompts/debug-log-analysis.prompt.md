---
description: 'Build a timeline from logs and separate the first failure from its consequences'
agent: ask
argument-hint: '[paste logs]'
---
<!-- 116 | K. Production debugging | ask -->
# 116 · Log analysis and timeline

Act as a senior engineer analysing production logs.

## Context
- Logs: [PASTE_LOGS]; services involved: [SERVICES]; incident window: [TIME_RANGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Reconstruct what happened, in order, and identify the first abnormal event.

## Constraints
- Quote log lines exactly; do not invent lines or timestamps.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- The first error versus later cascading errors.
- Correlation by trace id, request id, entity id and thread.
- Gaps in the logs and clock differences between services.
- Rate changes: what became more frequent or stopped.
- Log statements in this codebase that produced each key line.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A timeline table, the most likely trigger and what is still unknown.
