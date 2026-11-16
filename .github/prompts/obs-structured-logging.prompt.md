---
description: 'Add correlation ids and consistent structured context to logs across HTTP, Kafka and async code'
agent: agent
argument-hint: '[service or flow]'
---
<!-- 131 | M. Distributed systems and observability | build -->
# 131 · Structured logging and correlation

Act as a senior engineer improving diagnosability.

## Context
- Scope: [SERVICE_OR_FLOW]; logging stack: [STACK, e.g. Logback JSON encoder]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Make every log line of the flow traceable to one request or message and one business key.

## Constraints
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Trace and correlation id set at every entry point: HTTP filter, Kafka listener, scheduler, batch step.
- MDC propagated to executors and @Async, and always cleared.
- Outbound calls and produced messages carrying the id.
- Business keys as structured fields, not embedded in message text.
- No sensitive data added.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A test proving the id appears in logs across a thread hop, and a sample log line before and after.
