---
description: 'Triage SonarQube, SpotBugs or Checkstyle findings into real bugs, debt and noise'
agent: ask
argument-hint: '[paste findings]'
---
<!-- 143 | N. Build, CI and deployment | ask -->
# 143 · Static analysis findings triage

Act as a senior engineer triaging static analysis output.

## Context
- Findings: [PASTE_FINDINGS]; tool: [TOOL]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Sort the findings by whether they represent a real defect, and propose how to deal with each group.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Real bugs and vulnerabilities, each with the scenario in which it fails.
- Maintainability issues worth fixing when the code is next touched.
- False positives, with the reason, and whether to suppress locally or adjust the rule.
- Findings in generated code.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: finding, classification, reason, action. No blanket suppressions.
