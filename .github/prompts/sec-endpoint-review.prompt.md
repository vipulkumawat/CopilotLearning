---
description: 'Review an endpoint for authorisation, injection, mass assignment and data exposure'
agent: ask
argument-hint: '[endpoint or controller]'
---
<!-- 120 | L. Security and code quality | ask -->
# 120 · Endpoint security review

Act as an application security engineer reviewing a Spring API.

## Context
- Target: [ENDPOINT_OR_CONTROLLER]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review the endpoint and everything it calls for exploitable weaknesses.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Authentication and authorisation on every operation, including object-level access (IDOR).
- Injection: SQL, JPQL or native queries built from strings; SpEL; command execution.
- Mass assignment: DTOs bound directly to entities; client-controlled id, role, owner or price fields.
- Sensitive data in responses, error messages and logs.
- CSRF, CORS and rate limiting, where relevant.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Findings with severity, a description of the request that demonstrates each and the fix.
