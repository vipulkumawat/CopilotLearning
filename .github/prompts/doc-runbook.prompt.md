---
description: 'Write a runbook for an alert or failure mode, with diagnosis and safe mitigation steps'
agent: agent
argument-hint: '[alert or failure mode]'
---
<!-- 158 | P. Pull requests, documentation and workflow | write -->
# 158 · Operational runbook

Act as an engineer writing for whoever is on call at 3 a.m..

## Context
- Alert or failure mode: [ALERT]; service: [SERVICE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write a runbook that someone unfamiliar with the code can follow.

## Constraints
- Mark destructive or irreversible steps clearly, with their precondition.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- What the alert means and the user impact.
- How to confirm it is real.
- Likely causes in order, with the check for each.
- Mitigations: safe first (restart, scale, pause consumer, disable flag), risky last.
- When and to whom to escalate.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Numbered steps with exact commands or queries taken from this repository where possible; placeholders marked where not.
