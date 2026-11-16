---
description: 'Add a client for an external HTTP API with timeouts, error mapping and tests'
agent: agent
argument-hint: '[external service and operation]'
---
<!-- 032 | C. Feature development | build -->
# 032 · Integrate an external API

Act as a senior Java engineer who assumes remote calls fail.

## Context
- External service: [EXTERNAL_SERVICE]; operation(s): [OPERATIONS]
- API description: [OPENAPI_OR_SAMPLE_REQUEST_RESPONSE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Add a client behind an interface owned by our domain, so the rest of the code never sees the vendor's model.

## Constraints
- Use the HTTP client this project already uses; explicit connect and read timeouts; credentials from configuration only.
- Retry only idempotent operations, with a bounded count and backoff.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- 2xx with unexpected or missing fields; 4xx by meaning (not found, invalid, unauthorised); 5xx; timeout; connection refused.
- Slow responses under load; rate limiting (429).
- Our transaction is open while the call is made.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- WireMock tests for every case above, with sample payloads stored as test resources.
- Metrics and logs for the call, with no secrets or personal data.
