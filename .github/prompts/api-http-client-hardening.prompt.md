---
description: 'Review timeouts, retries, pooling, error mapping and logging of outbound HTTP calls'
agent: ask
argument-hint: '[external service]'
---
<!-- 037 | D. Spring Boot and APIs | ask -->
# 037 · Outbound HTTP client hardening

Act as a senior Java engineer who has handled dependency outages.

## Context
- Outbound calls to: [EXTERNAL_SERVICE] (RestClient, WebClient, Feign or RestTemplate)
- Our own latency budget for the calling endpoint: [SLA]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review every outbound call to this dependency and say what happens when it is slow, down or misbehaving.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Connect, read and overall timeouts: set, and sensible against our SLA?
- Retries: bounded, backoff with jitter, idempotent operations only?
- Connection pool size, idle eviction and keep-alive.
- Mapping of 4xx and 5xx; responses with an unexpected body.
- Calls made inside an open database transaction.
- Logging that could expose secrets or personal data.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: call site, current setting, risk, recommended setting, failure mode prevented.
