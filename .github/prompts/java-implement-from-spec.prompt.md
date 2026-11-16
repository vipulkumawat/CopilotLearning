---
description: 'Implement a self-contained method or utility from a precise specification with examples'
agent: agent
argument-hint: '[what the method must do]'
---
<!-- 010 | B. Core Java | build -->
# 010 · Implement a method from a specification

Act as a senior Java engineer writing small, correct, well-tested code.

## Context
- Where it belongs: [CLASS_OR_PACKAGE]
- Java version: [JAVA_VERSION]
- What it must do: [BEHAVIOUR]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Implement the method exactly as specified, with tests that prove each example.

## Constraints
- No new dependencies. Pure function if possible: no I/O, no static mutable state.
- Signature: [SIGNATURE, or propose one first]
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Normal cases: [NORMAL_CASES]
- Edge cases: null, empty, single element, duplicates, maximum size, boundary values.
- Failure cases: which inputs throw, and which exception type and message.

## Code examples
Fill this table before sending; it is the contract:

| Input | Expected output |
|---|---|
| [INPUT_1] | [OUTPUT_1] |
| [INPUT_2] | [OUTPUT_2] |
| [INVALID_INPUT] | throws [EXCEPTION] |

## Confirmation
- One parameterised JUnit 5 test row per line of the table, plus the edge cases.
- State the time and space complexity and any case where the specification was ambiguous.
