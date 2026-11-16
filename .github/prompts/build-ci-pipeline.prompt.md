---
description: 'Write or review a CI workflow with caching, test stages, quality gates and artefact publishing'
agent: agent
argument-hint: '[repository and CI system]'
---
<!-- 142 | N. Build, CI and deployment | write -->
# 142 · CI pipeline for a Java service

Act as a senior engineer designing continuous integration.

## Context
- CI system: [GITHUB_ACTIONS_OR_OTHER]; build tool: [MAVEN_OR_GRADLE]; Java version: [JAVA_VERSION]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write (or review) the pipeline so it is fast, reproducible and blocks bad changes.

## Constraints
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Dependency caching; unit tests before integration tests; Testcontainers support on the runner.
- Static analysis, dependency vulnerability scan and coverage gate.
- Secrets handled by the CI secret store; least-privilege tokens; pinned action versions.
- Build once, promote the same artefact; image tagging by commit.
- Flaky-test reporting rather than blanket retries.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- The workflow file with comments, and an estimate of run time per stage.
