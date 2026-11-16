---
description: 'Write release notes for operators and consumers from the commits since the last release'
agent: agent
argument-hint: '[previous tag or version]'
---
<!-- 160 | P. Pull requests, documentation and workflow | write -->
# 160 · Release notes from changes

Act as an engineer communicating a release.

## Context
- Changes since: [PREVIOUS_TAG]; audience: [AUDIENCE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write release notes grouped by what the audience needs to do or know.

## Constraints
- Derived from the actual commits and diff; nothing invented.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- New features and behaviour changes, in user terms.
- Breaking changes and required actions.
- Configuration, migration and deployment-order notes.
- Fixed bugs, with ticket ids.
- Known issues.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Notes with the breaking changes first, each linked to its ticket or commit.
