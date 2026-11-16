---
description: 'Replace scattered @Value usage with a validated @ConfigurationProperties class'
agent: agent
argument-hint: '[property prefix or feature]'
---
<!-- 044 | D. Spring Boot and APIs | build -->
# 044 · Type-safe configuration properties

Act as a senior Spring Boot engineer.

## Context
- Properties to group: [PREFIX_OR_FEATURE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Introduce an immutable, validated @ConfigurationProperties record and migrate the @Value usages to it.

## Constraints
- Property names and defaults stay the same, so no environment needs changing.
- Secrets are never given defaults and never logged.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Missing required property: the application must fail at startup with a clear message.
- Invalid values: negative timeout, malformed URL, empty list.
- Durations and data sizes typed as Duration and DataSize.
- Profile-specific overrides still bind.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A binding test for valid, missing and invalid configuration.
- Configuration metadata so the IDE autocompletes the properties.
