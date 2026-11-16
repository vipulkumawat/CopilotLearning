---
description: 'Find lock-ordering deadlocks, starvation and stuck waits in code'
agent: ask
argument-hint: '[class or package]'
---
<!-- 090 | H. Concurrency | ask -->
# 090 · Deadlock and liveness review

Act as a senior Java engineer reviewing locking code.

## Context
- Target: [CLASS_OR_PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find code paths that can deadlock, starve or wait forever.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Nested locks acquired in different orders on different paths.
- Calling foreign code (listeners, callbacks, remote calls) while holding a lock.
- wait/notify misuse, missed signals, conditions not rechecked in a loop.
- Lock not released on an exception path; tryLock result ignored.
- Blocking waits without timeout: queues, latches, futures.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Each finding with the lock cycle or wait chain written out, and the fix.
