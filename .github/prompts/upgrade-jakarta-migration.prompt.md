---
description: 'Migrate a module from javax.* to jakarta.* with the related Spring Security and Hibernate changes'
agent: agent
argument-hint: '[module]'
---
<!-- 146 | O. Upgrades and migrations | build -->
# 146 · javax to jakarta and Spring Boot 3 migration

Act as a senior engineer who has migrated services to Spring Boot 3.

## Context
- Module: [MODULE]; current versions: [VERSIONS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Plan and perform the migration of this module in mechanical, verifiable steps.

## Constraints
- Mechanical changes (imports, renamed properties) are separated from behavioural changes, which need my review.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- javax.persistence, validation, servlet and annotation imports; javax packages that do not move.
- Security configuration without WebSecurityConfigurerAdapter; changed matcher methods.
- Hibernate 6 behaviour changes: id generation, type mappings, query strictness.
- Third-party libraries still compiled against javax.
- Trailing-slash matching, property renames and actuator changes.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- The build compiles and all tests pass after each step; a list of behavioural changes requiring manual testing.
