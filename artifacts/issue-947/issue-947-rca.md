# issue-947 RCA

Generated: 2026-03-16T15:59:18.695467+00:00

## Observed problem

- The repository already has captive-portal configuration support through form-based settings such as `captive_portal_login_form`, `captive_portal_logout_form`, and `captive_portal_sync_auth`.
- The issue proposes support for RFC 8908 so the app can discover whether captive-portal login is required and whether it is operating in internet mode.
- The issue statement defines product constraints up front:
  - short timeout
  - configurable per organization
  - optional, not required
  - documented behavior
- The issue discussion also shows at least one closed prior attempt, which suggests the hard part is not simply adding another HTTP request.

## Hypotheses

- This is primarily a product- and integration-shaping problem before it becomes a code problem.
- The safest proof path is an opt-in fetch layer driven by org config, with explicit failure fallback to current behavior.
- Existing captive-portal logic in `status.js`, login handling, and internet-mode docs must be compared before deciding where the API probe belongs.

## Rejected hypotheses

- This should not be treated as a mandatory dependency for all organizations.
- This is not ready for a broad “just fetch the API on every load” implementation without first defining timeout, fallback, and routing interactions.

## Root cause

- The current application relies on configured captive-portal forms and existing session/auth signals, but it does not have a bounded abstraction for querying RFC 8908 metadata.
- Because the feature touches configuration, runtime network behavior, and user-facing routing decisions, the unresolved design contract is part of the root cause.

## Fix-shaping constraints

- Keep the proof branch opt-in and configuration-driven.
- Document all unresolved questions instead of guessing:
  - where the API is queried
  - how long the timeout is
  - what fallback behavior applies when the endpoint is unavailable
  - which flows consume the result
- Do not let the proof branch silently change existing captive-portal behavior for organizations that do not configure the new API.
