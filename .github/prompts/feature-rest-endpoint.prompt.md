---
description: 'Add a REST endpoint with a record DTO, Bean Validation, mapping and slice tests'
agent: agent
argument-hint: '[HTTP method] [path] for [resource]'
---
<!-- 022 | C. Feature development | build -->
# 022 · REST endpoint with validation

Act as a senior Spring Boot engineer.

## Context
- Endpoint: [HTTP_METHOD] [PATH] to create or update [RESOURCE]
- Fields and rules: [FIELDS_AND_RULES]
- Who may call it: [ROLES]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Add the endpoint end to end: request and response DTOs, controller, service call and tests.

## Constraints
- Request and response DTOs are Java records with Bean Validation; never expose JPA entities.
- Use the status codes and error body format this project already uses.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Valid request; each invalid field; malformed JSON; unknown fields.
- Resource not found; duplicate or conflicting state (409).
- Unauthenticated and unauthorised caller.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- @WebMvcTest tests for every case above, asserting status and error body.
- The endpoint appears correctly in the OpenAPI output if the project generates one.
