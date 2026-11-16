---
description: 'Migrate tests from JUnit 4 to JUnit 5 without weakening them'
agent: agent
argument-hint: '[test package]'
---
<!-- 147 | O. Upgrades and migrations | build -->
# 147 · JUnit 4 to JUnit 5 migration

Act as a senior engineer modernising a test suite.

## Context
- Target: tests under [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Migrate the tests to JUnit 5 and AssertJ idioms, preserving what each test verifies.

## Constraints
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Runners and rules replaced by extensions (Mockito, Spring, temporary folders).
- expected= and ExpectedException replaced by assertThrows or assertThatThrownBy.
- Lifecycle annotations, static requirements and assumptions.
- Parameterised tests rewritten with @ParameterizedTest.
- Ignored tests: report them instead of migrating silently.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- The same number of tests run before and after, and none became weaker; the vintage engine is removed when the last test is migrated.
