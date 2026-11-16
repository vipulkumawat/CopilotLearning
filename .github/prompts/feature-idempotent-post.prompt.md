---
description: 'Make a POST endpoint idempotent with an Idempotency-Key header'
agent: agent
argument-hint: '[path]'
---
<!-- 025 | C. Feature development | build -->
# 025 · Idempotent POST endpoint

Act as a senior backend engineer who designs for retries.

## Context
- Endpoint: POST [PATH]
- Side effects it triggers: [SIDE_EFFECTS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Investigate how duplicates are handled today, then design and implement Idempotency-Key support.

## Constraints
- The design must cover key storage (table or Redis), TTL, response replay and in-flight requests.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Same key, same body: replay the stored response.
- Same key, different body: reject.
- Two identical requests arriving at the same moment.
- Crash after the side effect but before the response is stored.
- Missing key; expired key.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A concurrency test firing the same request in parallel and asserting exactly one side effect.
- The migration or cache configuration needed, with its retention policy.
