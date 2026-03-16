# issue-918 RCA

Generated: 2026-03-16T15:59:18.694279+00:00

## Observed problem

- `client/components/status/status.js` is a very large class component that mixes:
  - token validation and auth gating (`status.js:93-149`)
  - password-expiry redirect handling (`status.js:169-178`)
  - captive portal login/logout control (`status.js:212-245`, `607-814`)
  - payment verification redirects (`status.js:271-287`, `468-503`)
  - session and usage polling (`status.js:306-319`)
  - UI rendering and form/iframe orchestration (`status.js:995-1480`)
- Maintainers explicitly called out the block around current auth / macaddr / login handling as a candidate for surgical refactoring rather than a full rewrite.
- The open PR `#1056` already shows that broad changes in this file are easy to overlap with and easy to break.

## Hypotheses

- The main maintainability problem is not just file size; it is that side effects, redirects, polling, and render concerns are interleaved inside the same lifecycle-driven control flow.
- The safest first slice is around the status initialization / final-operations path, where verification, payment redirects, and session bootstrap are chained together.
- A surgical extraction can reduce duplication and make the early-exit paths explicit without converting the component architecture wholesale.

## Rejected hypotheses

- A full component rewrite is not aligned with maintainer guidance.
- Converting the file to hooks first would enlarge scope and mix architectural migration with logic refactoring.
- The issue is not only stylistic; duplicated side-effect branches and intertwined redirect rules materially raise regression risk.

## Root cause

- `componentDidMount` and `finalOperations()` currently act as a central control hub for unrelated responsibilities.
- Early-return paths for invalid tokens, password expiry, logout, captive portal login, bank-card verification, and session bootstrap are stacked in one lifecycle path.
- Because the same stateful flow touches cookies, navigation, captive-portal forms, loading context, and API polling, even small changes are difficult to isolate and verify.

## Fix-shaping constraints

- Keep the proof branch surgical and class-component-based unless a later comparison shows otherwise.
- Start with the maintainer-highlighted block or one adjacent branch of equivalent risk; do not attempt a file-wide refactor.
- Preserve:
  - password-expiry redirect behavior
  - bank-card verification redirects
  - captive portal sync/async behavior
  - session / usage refresh cadence
  - loading overlay semantics
- Any extracted helper or branch simplification must be backed by targeted tests because `#1056` already demonstrates that this area is review-sensitive.
