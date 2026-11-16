---
description: 'Diagnose a context startup failure or slow startup from the log'
agent: ask
argument-hint: '[paste startup log or error]'
---
<!-- 043 | D. Spring Boot and APIs | ask -->
# 043 · Application startup failure or slow startup

Act as a senior Spring Boot engineer debugging application start-up.

## Context
- Startup log or error: [PASTE_LOG]
- What changed recently: [RECENT_CHANGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find why the application context fails to start, or why it starts slowly.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- The root cause at the bottom of the exception chain, not the first BeanCreationException.
- Missing or duplicate beans, failed conditions, missing properties, profile not active.
- Auto-configuration that did or did not apply, and why.
- Slow steps: entity scanning, migrations, eager client initialisation, remote calls at startup.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- The root cause with evidence from the log, the fix, and how to confirm it (for example the condition evaluation report).
