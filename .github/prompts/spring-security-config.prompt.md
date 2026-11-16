---
description: 'Review the SecurityFilterChain, token validation, CORS, CSRF and method security'
agent: ask
argument-hint: '[security config class]'
---
<!-- 045 | D. Spring Boot and APIs | ask -->
# 045 · Spring Security configuration review

Act as an application security engineer who knows Spring Security.

## Context
- Target: [SECURITY_CONFIG_CLASS]
- Authentication model: [MODEL, e.g. JWT resource server, session, API key]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review the security configuration and tell me what is reachable that should not be.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Matcher order; permitAll patterns broader than intended; the default rule for unmatched paths.
- Actuator, Swagger and error endpoints exposed.
- JWT validation: signature, issuer, audience, expiry, clock skew, role mapping.
- CSRF disabled where sessions or cookies are used; CORS with wildcard origins plus credentials.
- Method security enabled and actually applied; object-level checks missing.
- Session fixation, stateless configuration and security headers.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- Findings by severity, each with the request that demonstrates it and the configuration fix.
- An endpoint-by-role access matrix derived from the configuration.
