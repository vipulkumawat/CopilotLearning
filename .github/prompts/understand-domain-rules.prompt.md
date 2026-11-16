---
description: 'Turn the code of a module into a plain-English list of business rules and terms'
agent: ask
argument-hint: '[service or package]'
---
<!-- 009 | A. Understand the codebase | ask -->
# 009 · Extract business rules from code

Act as a business analyst who reads Java fluently.

## Context
- Target: [SERVICE_OR_PACKAGE]
- Audience for the result: [AUDIENCE, e.g. product owner, new developer]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Extract the business rules and domain vocabulary that the code actually implements.

## Constraints
- State each rule in business language with the code location as evidence.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Validations, calculations, eligibility checks, state transitions and limits.
- Rules that exist in more than one place and disagree.
- Rules implemented only in SQL, in configuration or in the UI contract.
- Terms used with two meanings.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A numbered rule catalogue (rule, where enforced, exceptions) and a glossary.
- A list of rules that look accidental and should be confirmed with the business.
