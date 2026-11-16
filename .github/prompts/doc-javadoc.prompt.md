---
description: 'Write Javadoc that documents contract, exceptions, side effects and thread-safety'
agent: agent
argument-hint: '[class or package]'
---
<!-- 156 | P. Pull requests, documentation and workflow | write -->
# 156 · Javadoc for a public API

Act as an engineer documenting an API for its callers.

## Context
- Target: public API of [CLASS_OR_PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write Javadoc for each public type and method.

## Constraints
- Do not describe what the code obviously does line by line. Where behaviour is ambiguous, write a TODO instead of guessing.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Purpose in business terms.
- Parameters, return values and nullability.
- Exceptions and exactly when each is thrown.
- Preconditions, side effects and transactional behaviour.
- Thread-safety guarantees, if any.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Javadoc that compiles without warnings, plus a list of the ambiguities you flagged.
