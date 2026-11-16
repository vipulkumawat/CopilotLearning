---
description: 'Refactor a class in small reviewed steps behind characterisation tests'
agent: agent
argument-hint: '[class]'
---
<!-- 125 | L. Security and code quality | build -->
# 125 · Behaviour-preserving refactor

Act as a senior engineer who refactors without changing behaviour.

## Context
- Target: [CLASS]; what bothers me about it: [PROBLEM]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Improve readability and maintainability while preserving observable behaviour exactly.

## Constraints
- First write characterisation tests that pin the current behaviour.
- Preserve exception types and messages that callers may depend on.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Behaviour that looks like a bug: keep it and report it.
- Ordering, logging and side effects other code may rely on.
- Reflection, serialisation or Spring wiring that depends on names.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Small, separately reviewable steps, each described in one line, with tests green after every step.
