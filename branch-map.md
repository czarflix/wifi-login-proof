# branch-map

Generated: 2026-03-16T16:05:27.155722+00:00

## Clean proof worktree

- Path: `<local WiFi checkout>`
- Baseline branch: `master` @ `c2813c5a72214fb465d42e5c3e2e757931274a85`
- Strategy: keep proof branches independent by default, then use a later integration smoke branch to test coexistence.

## Planned proof branches

- `proof-react19-followup`
  - Base: `master`
  - Scope: compare against issue `#870` and PR `#1006`, then validate whether a React 18.3 -> 19 follow-up is locally feasible.
- `proof-272-registration-redirect`
  - Base: `master`
  - Scope: redirect decomposition from `OrganizationWrapper` for the highest-value flows in issue `#272`.
- `proof-314-header-unification`
  - Base: `master`
  - Scope: header markup unification for issue `#314`, with direct comparison against PR `#1048`.
- `proof-918-status-surgical-slice`
  - Base: `master`
  - Scope: surgical `Status` refactor slices only, consistent with issue `#918` maintainer guidance and PR `#1056` overlap.
- `proof-947-rfc8908-prototype`
  - Base: `master`
  - Scope: bounded RFC 8908 support prototype, documented as comparison-first because product questions remain open.
- `proof-integration-smoke`
  - Base: `master`
  - Scope: smoke integration branch created only to test whether independently-proven workstreams still coexist.

## Current local branch state

- `proof-272-registration-redirect` -> `d03c86b3873d1526bf14ca13fd618ae657e38979` (implemented / verified, browser-validated)
- `proof-314-header-unification` -> `3c13d499e8c6053e2679f9ff0de5a8b194e8af0e` (implemented / verified)
- `proof-918-status-surgical-slice` -> `17e0a904cae43cce3f3614eb6df21f3fc0fcc9a1` (implemented / verified)
- `proof-947-rfc8908-prototype` -> `c2813c5a72214fb465d42e5c3e2e757931274a85` (comparison/design only)
- `proof-integration-smoke` -> `42a73e4808196a418968400906602cab7cf9e294` (stacked coexistence proof)
- `proof-react19-followup` -> `c2813c5a72214fb465d42e5c3e2e757931274a85` (comparison/gap report only)

## Branch usage rules

- Keep issue archaeology, RCA, comparison notes, and validation logs in this proof repo.
- Do not stack unrelated proof branches on top of each other by default.
- Reuse commits from existing PRs only when the dependency is exact and documented in the comparison report.
- Treat `proof-integration-smoke` as a smoke branch, not as the canonical implementation branch for any one issue.
