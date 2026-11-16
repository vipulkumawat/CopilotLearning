---
description: 'Test response mapping, error translation, timeouts and retries of an outbound client with WireMock'
agent: agent
argument-hint: '[client class]'
---
<!-- 102 | J. Testing | write -->
# 102 · Tests for an external HTTP client

Act as a senior engineer testing integration code.

## Context
- Client: [CLIENT_CLASS] calling [EXTERNAL_SERVICE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write tests for the client using WireMock (or MockRestServiceServer if that is the project's choice).

## Constraints
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Successful response mapped to our model.
- Each relevant 4xx and 5xx response and how it is translated.
- Timeout and connection failure.
- Malformed, empty or unexpected response body.
- Retry behaviour: the exact number of attempts, and no retry for non-idempotent calls.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Sample payloads stored as test resources, with a note of the fields the client actually depends on.
