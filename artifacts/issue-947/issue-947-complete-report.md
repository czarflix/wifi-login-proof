# issue-947 complete report

Generated: 2026-03-16T15:59:18.695976+00:00

## Archaeology summary

- Issue `#947` is explicitly marked as not suited for beginner contributors and says more discussion is required.
- The maintainer constraints are already specific: optional feature, short timeout, configurable URL, documented behavior.
- A prior PR attempt was closed, which is a signal that the design contract matters as much as the code.

## Root cause

- The repository has no bounded abstraction yet for RFC 8908 probing.
- The unresolved product contract is itself part of the problem: query location, timeout, fallback, and consumer flows are not yet fixed.

## Implementation summary

- No speculative code branch was created.
- The completed deliverable for this workstream is a blocker-aware design and comparison report that narrows the safe shape of a future prototype.

## Verification summary

- Verified constraints:
  - optional feature
  - short configurable timeout
  - configurable per-org URL
  - documented behavior required
- Result:
  - comparison/design proof completed
  - implementation intentionally deferred pending clarified maintainer direction

## Proposal impact

- The proposal should treat RFC 8908 as mentor-confirmed stretch work only.
- Safe wording:
  - RFC 8908 has been studied enough to define safe constraints
  - it should not be promised as guaranteed scope without mentor confirmation
