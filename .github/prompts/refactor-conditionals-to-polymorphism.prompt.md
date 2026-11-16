---
description: 'Replace type-code switches or if-else ladders with strategies, enums or sealed types'
agent: agent
argument-hint: '[method with the conditional]'
---
<!-- 127 | L. Security and code quality | build -->
# 127 · Replace conditional logic with a strategy

Act as a senior engineer applying patterns only where they pay off.

## Context
- Target: [METHOD]; the varying dimension: [DIMENSION, e.g. payment type]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Decide whether polymorphism improves this code, and if so introduce it.

## Constraints
- If a switch expression over a sealed type or enum is simpler than a strategy hierarchy, prefer it and say so.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Every existing branch, including the default and "impossible" ones.
- A new variant must fail compilation or a test if not handled.
- The same conditional duplicated elsewhere.
- Spring wiring of strategies (map by key) and a missing strategy at runtime.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Characterisation tests written first and still green; adding a variant demonstrated as a one-place change.
