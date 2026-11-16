---
description: 'Bring OpenAPI annotations or spec in line with what the controllers really do'
agent: agent
argument-hint: '[controller or package]'
---
<!-- 040 | D. Spring Boot and APIs | write -->
# 040 · OpenAPI documentation sync

Act as a senior engineer documenting an API for client developers.

## Context
- Target: [CONTROLLER_OR_PACKAGE]
- How the spec is produced here: [SPRINGDOC_ANNOTATIONS_OR_YAML_FIRST]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Compare the documented contract with the code and update the documentation to match reality.

## Constraints
- Document only behaviour you verified in code; flag mismatches rather than choosing a side silently.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Every status code the endpoint can actually return, including errors from the global handler.
- Required versus optional fields, formats, limits and enums taken from the validation annotations.
- Security requirements per operation.
- A realistic example for each request and response.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- The updated annotations or spec, and a list of the mismatches found between code and documentation.
