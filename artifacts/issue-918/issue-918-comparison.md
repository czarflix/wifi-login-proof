# issue-918 comparison report

Generated: 2026-03-16T15:59:18.694855+00:00

## Existing issue guidance

- Maintainers explicitly rejected a broad rewrite and instead asked for surgical readability improvements in iterations.
- The discussion highlights a specific control-flow block as the highest-value starting point and questions duplicated branches around login/macaddr behavior.

## Overlap with open PRs

- Active overlap exists in PR `#1056`.
- Current known characteristics from the overlap matrix:
  - touches only `client/components/status/status.js`
  - `QA-Checks` passes
  - `Tests and Coverage` currently fails
  - review history is changes-request-heavy
- This is a signal that the area is both important and review-sensitive.

## Comparison against own PRs

- PR `#1061` and `#1062` do not touch `Status`.
- They provide prior evidence of repo familiarity, but this workstream should stay independent.

## Chosen direction

- Comparison-first and surgical-only.
- Start from the maintainer-highlighted control-flow block or an adjacent branch of comparable risk.
- Keep the local proof branch small enough that it can be evaluated against `#1056` instead of becoming a competing rewrite.

## Why this direction

- `Status` is the largest hotspot in the repo and the easiest place to overclaim.
- The open PR already shows that even a targeted refactor in this file can trigger failing tests and repeated review objections.
- A narrow, well-argued comparison is more valuable here than a large parallel diff.
