---
description: 'Analyse a deadlock or lock wait and propose ordering, locking or retry changes'
agent: ask
argument-hint: '[paste deadlock report or error]'
---
<!-- 059 | E. JPA, Hibernate and databases | ask -->
# 059 · Database deadlock and lock timeout analysis

Act as a senior engineer who understands database locking.

## Context
- Error or deadlock report: [PASTE_REPORT]
- Code paths believed to be involved: [CODE_PATHS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Reconstruct which transactions took which locks in which order, and how to stop it happening.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- The two (or more) statements and the lock each held and wanted.
- Inconsistent ordering of updates across code paths; Hibernate flush order.
- Missing indexes causing range or table locks; foreign-key locking.
- Long transactions and isolation level.
- Whether retrying the deadlock victim is safe (idempotent) here.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A timeline of the interleaving, the root cause and ranked fixes (ordering, shorter transaction, index, retry).
