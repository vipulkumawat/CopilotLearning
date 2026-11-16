---
description: 'Encode layering and dependency rules as tests so the architecture cannot erode'
agent: agent
argument-hint: '[root package and rules]'
---
<!-- 109 | J. Testing | write -->
# 109 · Architecture tests with ArchUnit

Act as a software architect automating architecture governance.

## Context
- Root package: [ROOT_PACKAGE]; rules: [RULES, e.g. controllers do not use repositories]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write ArchUnit tests for the rules, and report how many violations exist today.

## Constraints
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Layer dependencies; no cycles between feature packages.
- Domain free of framework imports, if that is the intent.
- Naming and placement conventions; @Transactional only in the service layer.
- No field injection; no use of forbidden APIs (java.util.Date, System.out).

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- The rules, the current violations frozen as a baseline, and the three worth fixing first.
