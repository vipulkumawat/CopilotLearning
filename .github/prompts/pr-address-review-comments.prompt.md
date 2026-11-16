---
description: 'Work through review comments, fixing what is right and drafting replies where I disagree'
agent: agent
argument-hint: '[paste review comments]'
---
<!-- 153 | P. Pull requests, documentation and workflow | build -->
# 153 · Address review comments

Act as an engineer responding to code review professionally.

## Context
- Review comments: [PASTE_COMMENTS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
For each comment decide whether it is correct, then propose the change or the reply.

## Constraints
- Do not agree automatically: if a comment is wrong, explain why with evidence from the code.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Comments pointing at real defects.
- Comments that are preferences.
- Comments that reveal a misunderstanding the code or description should prevent.
- Comments that widen scope and belong in a follow-up ticket.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A table: comment, verdict, action or drafted reply. Changes made only after I approve the table.
