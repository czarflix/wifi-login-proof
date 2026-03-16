# issue-947 fix verification

Generated: 2026-03-16T15:59:18.695649+00:00

## Issue-to-change map

- A real implementation would need to define:
  - where the RFC 8908 endpoint URL lives in org config
  - where the API probe is executed
  - timeout and fallback behavior
  - which flows consume the result (`status`, login/internet-mode logic, or both)
- Current proof outcome:
  - comparison/design proof only
  - no code diff was started because the issue still requires more product discussion and the previous upstream attempt was closed

## Pass 1 candidate

- No code candidate was started.
- The first completed candidate here is a bounded design contract:
  - optional feature
  - short configurable timeout
  - configurable URL per org
  - no behavior change when disabled or unreachable

## Pass 2 rethink

- Re-asked whether a local code prototype would be honest without clarifying the unresolved product contract.
- Answer: no.
- The pass-2-approved outcome is a blocker-aware design/gap report instead of speculative code.

## Red-green proof

- No red-green implementation cycle was started because the design contract is still incomplete.
- Verified evidence used instead:
  - issue text and maintainer constraints
  - closed prior attempt
  - current repo surfaces that would be affected (`status.js`, captive-portal config, docs)

## Validation outcomes

- Local proof branch: `proof-947-rfc8908-prototype`
- Current local branch head: `c2813c5a72214fb465d42e5c3e2e757931274a85` (baseline only)
- Classification:
  - blocker-aware comparison/design proof complete
  - implementation intentionally deferred until the unresolved product contract is clarified
