---
description: 'Pin the current behaviour of untested legacy code before refactoring it'
agent: agent
argument-hint: '[class or method]'
---
<!-- 108 | J. Testing | write -->
# 108 · Characterisation tests for legacy code

Act as a senior engineer making legacy code safe to change.

## Context
- Target: [CLASS_OR_METHOD]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write tests that record what the code does today, including behaviour that looks wrong.

## Constraints
- Do not change production code, except the smallest seam needed to test it, shown to me first.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- One test per distinct path through the code, found by reading the branches.
- Exception types and messages, null returns and side effects.
- Hidden inputs: system time, static state, configuration, database content.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Tests named "currently does X", with comments marking results that look like bugs.
- The paths you could not reach, and why.
