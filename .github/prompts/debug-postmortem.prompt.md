---
description: 'Draft a blameless post-mortem from the facts supplied'
agent: agent
argument-hint: '[timeline, impact, cause, response]'
---
<!-- 119 | K. Production debugging | write -->
# 119 · Incident post-mortem draft

Act as an engineering lead writing a blameless post-mortem.

## Context
- Timeline: [TIMELINE]
- Impact: [IMPACT]
- Root cause hypothesis: [ROOT_CAUSE_HYPOTHESIS]
- Detection and response: [DETECTION_AND_RESPONSE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Draft the post-mortem document.

## Constraints
- Blameless: describe systems and decisions, not individuals. Mark anything I have not confirmed as "to verify".
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Summary, impact, timeline, root cause, contributing factors.
- What went well and what went poorly, including detection and communication.
- Why existing safeguards (tests, alerts, reviews) did not catch it.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- Action items that are specific, with an owner and priority placeholder, each tied to a contributing factor.
