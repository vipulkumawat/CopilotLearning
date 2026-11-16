---
description: 'Write a reliable multi-threaded test that proves an invariant under contention'
agent: agent
argument-hint: '[method and invariant]'
---
<!-- 092 | H. Concurrency | write -->
# 092 · Write a concurrency test

Act as a senior engineer who writes deterministic concurrency tests.

## Context
- Method under test: [METHOD]; invariant: [INVARIANT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write a test that drives the method from many threads at once and asserts the invariant.

## Constraints
- No Thread.sleep for coordination; use latches or barriers to start threads together, and Awaitility for eventual assertions.
- Use a real database (Testcontainers) if the invariant is enforced there.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- All threads released at the same instant; more threads than resources.
- Assert both the final state and each caller's outcome (successes plus clean failures equals attempts).
- Exceptions in worker threads must fail the test, not vanish.
- A timeout so a deadlock fails the test instead of hanging the build.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- The test fails against a deliberately unsafe version and passes repeatedly against the real one.
