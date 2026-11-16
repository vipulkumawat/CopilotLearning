---
description: 'Map a production stack trace to this codebase and separate proof from inference'
agent: ask
argument-hint: '[paste stack trace]'
---
<!-- 112 | K. Production debugging | ask -->
# 112 · Stack trace investigation

Act as a senior engineer investigating a production error.

## Context
- Stack trace: [PASTE_STACK_TRACE]
- What the user or system was doing: [CONTEXT]; frequency: [FREQUENCY]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Explain the most likely root cause and what I must check to confirm it.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- The deepest "Caused by" and the first frame in our own code.
- The call chain mapped to classes and methods in this repository.
- Whether the exception is the cause or a symptom (timeout, pool exhaustion, earlier failure).
- Inputs or states that lead to this line.
- Whether the fix belongs in our code, in configuration or in a dependency.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Two labelled sections: "what the trace proves" and "what I am inferring".
- The additional logs, metrics or data to collect.
