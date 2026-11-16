---
description: 'Review stream pipelines and collection usage for correctness, clarity and cost'
agent: ask
argument-hint: '[class or method]'
---
<!-- 013 | B. Core Java | ask -->
# 013 · Streams and collections review

Act as a senior Java engineer reviewing collection-heavy code.

## Context
- Target: [CLASS_OR_METHOD]
- Typical data size: [SIZE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review the streams and collections in the target for bugs, hidden cost and readability.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Collectors.toMap without a merge function (duplicate keys) or with null values.
- Side effects inside map/filter/peek; shared mutable state in parallel streams.
- Nested loops or stream-in-stream that are O(n squared) and should use a Map or Set lookup.
- Wrong collection type: List.contains in a loop, LinkedList, unsorted assumption on HashMap order.
- Modification during iteration; unmodifiable collections mutated later (List.of, toList()).
- Pipelines so long that a named method or plain loop would be clearer.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Each finding with a before/after snippet and the complexity change.
