---
description: 'Find time zone, DST, clock and date arithmetic bugs'
agent: ask
argument-hint: '[class or package]'
---
<!-- 016 | B. Core Java | ask -->
# 016 · Date and time correctness review

Act as a senior Java engineer who has debugged many time zone incidents.

## Context
- Target: [CLASS_OR_PACKAGE]
- Business time zone(s): [ZONES]; database column types: [DB_TYPES]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find every place where dates and times can be wrong by an hour, a day or a time zone.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- LocalDateTime used for instants; implicit system default zone (LocalDate.now(), ZoneId.systemDefault()).
- java.util.Date, Calendar or SimpleDateFormat still in use.
- Start/end of day and "today" computed in the wrong zone; DST gaps and overlaps.
- Inclusive versus exclusive range ends; month-end and leap-year arithmetic.
- Mapping to JDBC/JPA column types and JSON formats; precision loss.
- Clock not injectable, making the logic untestable.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Findings with a concrete input (date, zone) that produces the wrong result, and the fix.
- The tests to add, using a fixed Clock.
