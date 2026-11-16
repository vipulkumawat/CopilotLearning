---
description: 'Write JUnit 5 and Mockito tests covering branches, boundaries and failure paths of a service method'
agent: agent
argument-hint: '[ServiceClass.method]'
---
<!-- 098 | J. Testing | write -->
# 098 · Service unit tests with edge cases

Act as a senior Java engineer who writes tests that catch real bugs.

## Context
- Under test: [SERVICE_CLASS].[METHOD]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write unit tests that pin down the behaviour of the method, one behaviour per test.

## Constraints
- JUnit 5, Mockito and AssertJ. Real value objects; mock only collaborators that cross a boundary.
- Test names state the behaviour in business language.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- The happy path.
- Every branch and every exception path.
- Boundary values, null and empty inputs.
- Interactions that matter (verify those only; no verification of incidental calls).

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- List the test cases first, then write them.
- Report any behaviour that looks like a bug instead of writing a test that blesses it.
