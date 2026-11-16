---
description: 'Create builders or fixtures that make tests short and intention-revealing'
agent: agent
argument-hint: '[entity or DTO types]'
---
<!-- 104 | J. Testing | write -->
# 104 · Test data builders and fixtures

Act as a senior engineer who keeps tests readable.

## Context
- Types needing test data: [TYPES]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Create test data builders with valid defaults so each test states only what matters to it.

## Constraints
- Test code only; do not add builders or setters to production classes for the benefit of tests.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Defaults that produce a valid, persistable object.
- Unique fields generated so tests do not collide.
- Related objects (an order with items) built in one expression.
- Fixed clock and deterministic ids where assertions need them.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Two existing tests rewritten with the builders to show the before and after.
