---
description: 'Find why the test suite is slow and how to speed it up without losing coverage'
agent: ask
argument-hint: '[module, plus timing report if available]'
---
<!-- 110 | J. Testing | ask -->
# 110 · Slow test suite review

Act as a senior engineer improving build feedback time.

## Context
- Module: [MODULE]; total time: [DURATION]; slowest tests: [PASTE_REPORT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find what makes the suite slow and rank the fixes.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Number of distinct Spring contexts: @MockBean, @DirtiesContext and differing configuration defeating the context cache.
- @SpringBootTest used where a slice or plain unit test would do.
- Containers started per class instead of shared.
- Sleeps and long timeouts; heavy data setup repeated per test.
- Safe parallel execution.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A ranked list: cause, tests affected, fix, expected saving.
