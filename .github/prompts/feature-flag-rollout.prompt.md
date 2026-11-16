---
description: 'Put new behaviour behind a flag so old and new paths run side by side'
agent: agent
argument-hint: '[new behaviour]'
---
<!-- 026 | C. Feature development | build -->
# 026 · Feature flag rollout

Act as a senior Java engineer planning a safe rollout.

## Context
- New behaviour: [NEW_BEHAVIOUR]
- Flag mechanism in this project: [MECHANISM, or "find it"]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Wrap the new behaviour behind a feature flag that defaults to the old path.

## Constraints
- Use the project's existing flag mechanism; if none exists, propose one and wait.
- One decision point, not flag checks scattered through the code.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Flag off, flag on, flag changed while requests are in flight.
- Data written by the new path and then read by the old path after a rollback.
- Flag service unavailable.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- Tests for both paths; a log line or metric showing which path ran, with no sensitive data.
- A cleanup checklist for removing the flag.
