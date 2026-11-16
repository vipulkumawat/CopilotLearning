---
description: 'Write @WebMvcTest tests for status codes, validation, serialisation and security of a controller'
agent: agent
argument-hint: '[controller]'
---
<!-- 099 | J. Testing | write -->
# 099 · Controller slice tests

Act as a senior Spring engineer testing the web layer.

## Context
- Controller: [CONTROLLER]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write slice tests that verify the HTTP contract, with the service layer mocked.

## Constraints
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Valid request: status, headers and response JSON shape.
- Each validation rule; malformed JSON; wrong content type.
- Service exceptions mapped to the right status and error body.
- Unauthenticated, wrong role and correct role.
- Pagination and sort parameters, if any.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Assertions on JSON fields (not on whole strings), and one test per row of the access matrix.
