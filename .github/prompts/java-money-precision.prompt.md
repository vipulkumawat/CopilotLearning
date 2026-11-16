---
description: 'Find rounding, overflow and floating-point errors in calculations'
agent: ask
argument-hint: '[class or method]'
---
<!-- 017 | B. Core Java | ask -->
# 017 · Money and numeric precision review

Act as a senior Java engineer reviewing financial calculations.

## Context
- Target: [CLASS_OR_METHOD]
- Currency and rounding rules: [RULES, e.g. 2 decimals, HALF_EVEN, round per line not per total]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Verify the calculations are exact, round as the business expects and cannot overflow.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- double or float used for money; new BigDecimal(double).
- BigDecimal.equals versus compareTo; scale mismatches; divide without scale and RoundingMode.
- Rounding applied at the wrong step (per item versus on the total) and penny-allocation remainders.
- int or long overflow in sums and multiplications; integer division.
- Currency ignored when adding amounts; database column precision smaller than the Java value.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Each finding with a numeric example showing the wrong and the right result.
- A set of parameterised test cases covering the rounding rules.
