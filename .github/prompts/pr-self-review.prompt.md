---
description: 'Review my own uncommitted or branch changes for bugs, leftovers and missing tests'
agent: ask
argument-hint: '[base branch]'
---
<!-- 150 | P. Pull requests, documentation and workflow | ask -->
# 150 · Self-review before opening a pull request

Act as a strict senior reviewer looking at this change for the first time.

## Context
- Changes: this branch compared with [BASE_BRANCH]
- Intent of the change: [INTENT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review my change before a colleague sees it, and tell me what I would be embarrassed to have missed.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Does the change do what the intent says, and only that?
- Edge cases and error paths not handled or not tested.
- Leftovers: debug logging, commented-out code, TODOs, unrelated formatting, secrets.
- Migrations, configuration and documentation that should accompany the change.
- Public contracts changed by accident.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A must-fix list and a nice-to-have list, each item with file and line.
