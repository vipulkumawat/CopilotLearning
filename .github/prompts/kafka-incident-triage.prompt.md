---
description: 'Triage growing lag, a stuck partition or repeated rebalances'
agent: ask
argument-hint: '[symptom, plus logs or metrics]'
---
<!-- 074 | F. Kafka | ask -->
# 074 · Kafka consumer incident triage

Act as a senior engineer on call for a Kafka-based service.

## Context
- Symptom: [SYMPTOM]; since: [WHEN]; recent changes: [CHANGES]
- Logs or metrics: [PASTE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Give me ordered hypotheses for the incident and the fastest check for each.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Poison message retried forever on one partition.
- Processing slower than max.poll.interval.ms, causing rebalance loops.
- Downstream dependency slow or down; connection pool exhausted.
- Input spike or hot key; too few consumers; consumers assigned no partitions.
- Deserialisation failures after a producer schema change.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: hypothesis, evidence for and against, how to confirm, safe mitigation.
- What must not be done (for example resetting offsets) without understanding the data impact.
