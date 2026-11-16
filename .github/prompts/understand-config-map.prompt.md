---
description: 'Map properties, profiles, conditional beans and environment variables for a module'
agent: ask
argument-hint: '[module]'
---
<!-- 005 | A. Understand the codebase | ask -->
# 005 · Spring configuration map

Act as a senior Spring Boot engineer auditing configuration.

## Context
- Module: [MODULE]
- Profiles in use: [PROFILES, e.g. local, dev, uat, prod]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Map every configuration input of the module and how it differs per environment.

## Constraints
- Never print secret values; show the property name and where it is sourced from.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- application*.yml / properties per profile, @ConfigurationProperties classes and @Value usages.
- Conditional beans (@Conditional*, @Profile) and what switches them.
- Environment variables and externalised secrets referenced.
- Properties referenced but never defined; properties defined but never used.
- Defaults that are unsafe for production (timeouts, pool sizes, ddl-auto, debug flags).

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: property, purpose, default, override per profile.
- A list of the gaps and unsafe defaults, ordered by risk.
