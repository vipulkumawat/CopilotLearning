---
description: 'Audit exception-to-response mapping for consistency, leakage and status codes'
agent: ask
argument-hint: '[module, or whole application]'
---
<!-- 035 | D. Spring Boot and APIs | ask -->
# 035 · Global error handling audit (RFC 7807)

Act as a senior Spring Boot engineer auditing API error behaviour.

## Context
- Scope: [MODULE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Audit global exception handling and report where clients get inconsistent, leaky or wrong error responses.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Whether all controllers return one consistent error body; whether ProblemDetail (RFC 7807) is or should be used.
- Stack traces, SQL fragments or internal class names reaching clients.
- Mapping of validation errors, malformed JSON, 404, 405, 409, 415 and unexpected exceptions.
- Errors thrown in filters and security, which bypass @ControllerAdvice.
- Whether each error is logged once, with a correlation id the client also receives.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Findings by severity with an example request and the response it produces today.
- A proposed mapping table (exception, status, error code); implement nothing until I approve.
