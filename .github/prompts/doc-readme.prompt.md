---
description: 'Write a README that gets a new developer running and oriented quickly'
agent: agent
argument-hint: '[service or module]'
---
<!-- 157 | P. Pull requests, documentation and workflow | write -->
# 157 · README for a service or module

Act as an engineer writing for the next person to join the team.

## Context
- Target: [SERVICE_OR_MODULE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write the README from what the repository actually contains.

## Constraints
- Every command must come from the build files or scripts in this repository; mark anything you could not verify.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- What the service does and what it does not do.
- How to build, run locally and run the tests, including required infrastructure.
- Configuration: the properties a developer must set.
- Architecture in one diagram; entry points, topics, tables and dependencies.
- How to deploy, and where the logs and dashboards are (placeholders if unknown).

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- A README under two screens, with unverified items listed at the end.
