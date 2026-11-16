---
description: 'Write a factual pull request description covering what, why, risk, testing and rollback'
agent: agent
argument-hint: '[base branch]'
---
<!-- 151 | P. Pull requests, documentation and workflow | write -->
# 151 · Pull request description

Act as an engineer writing for a busy reviewer.

## Context
- Changes: this branch compared with [BASE_BRANCH]; ticket: [TICKET]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write the pull request description.

## Constraints
- Factual and brief. Do not claim tests pass unless you ran them.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- One paragraph on what changed and why.
- Notable design decisions and the alternatives rejected.
- Risks: migrations, configuration, API or event contract changes, backward compatibility.
- How to test manually and which automated tests cover it.
- Rollback considerations and deployment order.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- A description a reviewer can read in two minutes, with a suggested review order for the files.
