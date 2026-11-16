---
description: 'Migrate outbound calls to the modern client while preserving timeouts, error handling and interceptors'
agent: agent
argument-hint: '[client class or package]'
---
<!-- 148 | O. Upgrades and migrations | build -->
# 148 · RestTemplate to RestClient or WebClient migration

Act as a senior engineer migrating HTTP client code.

## Context
- Target: [CLIENT_CLASS_OR_PACKAGE]; migrate to: [RESTCLIENT_OR_WEBCLIENT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Migrate the client code, keeping behaviour identical from the caller's point of view.

## Constraints
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Timeouts, connection pool and proxy settings carried over.
- Error handling: status codes that threw before must still throw the same exception types.
- Interceptors: authentication headers, logging, tracing, metrics.
- Message converters and custom ObjectMapper.
- Tests using MockRestServiceServer.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- The existing client tests pass unchanged in intent; any behaviour difference listed explicitly.
