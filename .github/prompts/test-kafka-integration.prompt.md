---
description: 'Test a consumer end to end with Testcontainers Kafka, including poison and duplicate messages'
agent: agent
argument-hint: '[consumer]'
---
<!-- 101 | J. Testing | write -->
# 101 · Kafka integration tests

Act as a senior engineer testing messaging code.

## Context
- Consumer: [CONSUMER]; topic: [TOPIC]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write an integration test that proves the consumer's behaviour against a real broker.

## Constraints
- Awaitility for asynchronous assertions; no Thread.sleep.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- A valid message is processed and its side effect is visible.
- A malformed message reaches the dead-letter topic and does not block the partition.
- Duplicate delivery produces one side effect.
- A transient failure is retried and then succeeds.
- Offsets are committed only after successful processing.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Each test uses its own topic or group so tests cannot affect each other.
