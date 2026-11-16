---
description: 'Diagnose version conflicts, duplicate classes and NoSuchMethodError from the dependency tree'
agent: ask
argument-hint: '[error or dependency tree]'
---
<!-- 138 | N. Build, CI and deployment | ask -->
# 138 · Dependency conflict resolution

Act as a senior engineer who manages Maven or Gradle builds.

## Context
- Build tool: [MAVEN_OR_GRADLE]; error: [ERROR]
- Dependency tree extract: [PASTE_TREE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find which dependency brings the conflicting version and the cleanest way to resolve it.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- The winning version and why it won (nearest, BOM, constraint).
- Whether the Spring Boot BOM manages this library, and whether overriding it is safe.
- Exclusion versus dependency management versus upgrading the parent library.
- Duplicate classes from relocated or renamed artefacts.
- Test-scope and runtime-scope differences.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- The root cause, the smallest build-file change and the command that proves the resolved version.
