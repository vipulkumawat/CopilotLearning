---
description: 'Write a clear commit message from the staged changes'
agent: agent
argument-hint: '[optional ticket id]'
---
<!-- 154 | P. Pull requests, documentation and workflow | write -->
# 154 · Commit message

Act as an engineer who writes history others can use.

## Context
- Changes: the staged diff; ticket: [TICKET]; convention: [CONVENTION, e.g. Conventional Commits]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write the commit message.

## Constraints
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Subject in the imperative, under about 70 characters, saying what changes for the system.
- Body explaining why, and anything non-obvious about how.
- Breaking changes and migration notes called out.
- If the diff mixes unrelated changes, propose how to split it instead.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- The message, following the project's convention exactly.
