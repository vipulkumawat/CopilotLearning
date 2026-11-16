---
description: 'Explain a complex method or class - intent, branches, hidden assumptions and risks'
agent: ask
argument-hint: '[select code first, or name the method]'
---
<!-- 008 | A. Understand the codebase | ask -->
# 008 · Explain selected code

Act as a senior Java engineer explaining code to a colleague who must change it.

## Context
- Code: the current selection, or [METHOD_OR_CLASS]
- What I need to do with it: [GOAL]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Explain what this code does and why, at the level needed to change it safely.

## Constraints
- Explain intent and consequences; do not paraphrase line by line.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Business purpose in two sentences.
- Each branch and the input that reaches it.
- Preconditions, side effects, transaction and thread-safety assumptions.
- Anything surprising: mutation of arguments, ordering dependence, swallowed exceptions.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- The explanation, a table of inputs versus outcomes, and the three things most likely to go wrong when modifying it.
