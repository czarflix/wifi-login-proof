# issue-314 comparison report

Generated: 2026-03-16T15:59:18.693394+00:00

## Existing issue guidance

- The original maintainer guidance is explicit: use CSS to avoid keeping separate desktop and mobile header markup.
- The issue is not about redesigning the header; it is about removing duplication that makes customization painful.

## Overlap with open PRs

- Active overlap exists in PR `#1048`.
- Current known characteristics from the overlap matrix:
  - touches `client/components/header/header.js`
  - touches `client/components/header/header.test.js`
  - touches header CSS and snapshots
  - `Tests and Coverage` is currently failing
- This means any local proof branch must be comparison-first, not a blind parallel implementation.

## Comparison against own PRs

- PRs `#1061` and `#1062` do not touch header code.
- They can remain referenced as prior WiFi evidence but should not be used as branch prerequisites here.

## Chosen direction

- Comparison-first, then narrower-slice or extension-only if the local read shows that `#1048` leaves a clear maintainability or test gap.
- Keep local proof focused on markup duplication and responsive parity, not on broader header cleanup.

## Why this direction

- There is already active code in the exact target area, so the proof needs to demonstrate that it can build on or refine existing work rather than duplicate it.
- If `#1048` already covers the issue adequately, this workstream may downgrade to a comparison report instead of a separate implementation proof.
