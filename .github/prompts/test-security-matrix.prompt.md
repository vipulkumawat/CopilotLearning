---
description: 'Generate tests proving each role and ownership combination is allowed or denied'
agent: agent
argument-hint: '[controller or service]'
---
<!-- 107 | J. Testing | write -->
# 107 · Authorisation matrix tests

Act as a security-minded engineer writing access control tests.

## Context
- Target: [CONTROLLER_OR_SERVICE]; roles: [ROLES]; ownership rule: [RULE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Derive the access matrix from the code and write one parameterised test over it.

## Constraints
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Every operation crossed with: anonymous, each role, the owner, a non-owner with the same role.
- Object-level access: another user's or another tenant's id.
- Method-level security on services reached by more than one entry point.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- The matrix as a table, the test, and a list of cells where the code's behaviour looks unintended.
