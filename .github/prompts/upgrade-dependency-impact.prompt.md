---
description: 'Assess the code and configuration impact of upgrading one library'
agent: ask
argument-hint: '[library] [old version] -> [new version]'
---
<!-- 145 | O. Upgrades and migrations | ask -->
# 145 · Dependency upgrade impact

Act as a senior engineer assessing a library upgrade.

## Context
- Library: [LIBRARY] from [OLD_VERSION] to [NEW_VERSION]
- Release notes, if available: [PASTE_OR_LINK]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find what in this codebase is affected by the upgrade. Do not upgrade yet.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Usages of APIs that changed, were deprecated or were removed.
- Transitive dependencies that will change and may conflict.
- Configuration properties renamed or deprecated.
- Behavioural changes and changed defaults described in the release notes.
- Tests most likely to reveal a regression.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A checklist with the files needing attention, and anything you could not verify without the release notes.
