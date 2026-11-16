---
description: 'Build a file-based import step with line validation, a reject file and reconciliation counts'
agent: agent
argument-hint: '[file format and target]'
---
<!-- 080 | G. Spring Batch | build -->
# 080 · File import with validation and rejects

Act as a senior engineer who builds file integrations.

## Context
- File: [FORMAT, DELIMITER, ENCODING, HEADER/TRAILER]; sample lines: [SAMPLE]
- Target: [TARGET_TABLE_OR_SERVICE]; validation rules: [RULES]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Implement the import so that good lines load, bad lines are reported, and totals can be reconciled.

## Constraints
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Malformed line, wrong column count, bad encoding, quoted delimiters, empty file.
- Trailer count or checksum that does not match.
- The same file delivered twice; a file still being written when picked up.
- Bad-line threshold above which the whole file is rejected.
- What happens to the file after success and after failure.

## Code examples
Paste three real (anonymised) lines: one valid, one invalid, and the header or trailer.

## Confirmation
- Tests with sample files for each case; a reject file giving line number and reason.
- Read = written + rejected + filtered, asserted in the test and logged per run.
