---
description: 'Add a business rule in the right place with parameterised edge-case tests'
agent: agent
argument-hint: '[service class] : [rule in plain English]'
---
<!-- 023 | C. Feature development | build -->
# 023 · Business rule with tests

Act as a senior Java engineer who protects domain logic.

## Context
- Service or domain class: [SERVICE_CLASS]
- Rule: [RULE_IN_PLAIN_ENGLISH]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Decide where the rule belongs (service, domain object or policy class), justify it, then implement it.

## Constraints
- The rule lives in exactly one place; existing public method signatures stay unchanged.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Null and missing inputs; boundary values on both sides of every threshold.
- Concurrent updates that could bypass the rule.
- Time zones and "today" if the rule involves dates.
- Existing records that already violate the rule.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A parameterised JUnit 5 test with one row per edge case, named in business language.
- A clear, specific exception or result when the rule is violated.
