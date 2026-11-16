---
description: 'Refactor a class to records, sealed types, pattern matching, switch expressions and text blocks'
agent: agent
argument-hint: '[class or package]'
---
<!-- 015 | B. Core Java | build -->
# 015 · Modernise to current Java idioms

Act as a senior Java engineer modernising code without changing behaviour.

## Context
- Target: [CLASS_OR_PACKAGE]
- Java version available: [JAVA_VERSION]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Apply modern Java language features where they make the code shorter and safer.

## Constraints
- Behaviour, public API and serialised forms (JSON, Java serialisation, JPA mapping) must not change.
- Do not convert JPA entities to records.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- DTOs and value classes that can become records (check Jackson, MapStruct and equality semantics first).
- instanceof-and-cast chains that become pattern matching; if/else ladders that become switch expressions.
- Closed hierarchies that can be sealed, giving exhaustive switches.
- String concatenation of SQL or JSON that becomes a text block.
- Places where the old form is clearer and should stay.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- One small commit-sized step per kind of change, existing tests green after each.
- A list of the changes you deliberately did not make, and why.
