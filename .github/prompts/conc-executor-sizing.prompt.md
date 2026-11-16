---
description: 'Review executor sizing, queueing, rejection and isolation between workloads'
agent: ask
argument-hint: '[executor config or package]'
---
<!-- 087 | H. Concurrency | ask -->
# 087 · Thread pool configuration review

Act as a senior engineer who tunes thread pools from measurements.

## Context
- Target: [EXECUTOR_CONFIG]; task type: [CPU_OR_IO_BOUND]; task duration: [DURATION]; arrival rate: [RATE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Check whether each pool is sized and bounded correctly for its workload.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Unbounded queues hiding overload; core/max settings that never grow because the queue is unbounded.
- Rejection policy and what the caller experiences.
- One pool shared by fast and slow tasks; a task waiting on another task in the same pool (starvation deadlock).
- Pool size versus database connections and downstream limits.
- Thread names, metrics and graceful shutdown.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Per pool: current settings, risk, recommended settings with the arithmetic behind them.
