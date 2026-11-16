---
description: 'Find why the Maven or Gradle build is slow and rank the fixes'
agent: ask
argument-hint: '[build file, plus timing output if available]'
---
<!-- 139 | N. Build, CI and deployment | ask -->
# 139 · Build time review

Act as a build engineer improving feedback time.

## Context
- Build tool: [MAVEN_OR_GRADLE]; total time: [DURATION]; timing output: [PASTE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Identify where build time goes and what to change.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Test time versus compile time versus packaging.
- Parallel and incremental build settings; build cache usage locally and in CI.
- Annotation processors and code generation; plugins running in every phase.
- Module structure forcing full rebuilds.
- Dependency resolution: snapshots, slow repositories, no CI cache.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A ranked list: cause, fix, expected saving, risk.
