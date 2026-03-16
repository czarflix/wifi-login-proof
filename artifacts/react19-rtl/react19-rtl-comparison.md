# react19-rtl comparison report

Generated: 2026-03-16T15:59:18.690988+00:00

## Existing issue guidance

- The issue discussion and maintainer comments already define the staged direction:
  - first land React 18.3
  - then evaluate React 19
- The maintainer explicitly asked the contributor behind the current work to open the React 18.3 PR before going further.

## Overlap with open PRs

- Active overlap exists in PR `#1006`.
- Current known characteristics from the overlap matrix:
  - large diff touching 88 files
  - `QA-Checks` and `Tests and Coverage` are green
  - merge state is currently `DIRTY`
- This means the right local posture is to compare against that branch and identify remaining React 19 work, not to recreate the full 18.3 migration locally from scratch.

## Comparison against own PRs

- My existing WiFi PRs `#1061` and `#1062` are unrelated to the React migration path.
- They stay as prior repo evidence only.

## Chosen direction

- Extension/comparison-first.
- Treat `#1006` as the current best upstream baseline for this workstream, then measure:
  - what it already solves
  - what React 19 still breaks
  - what test-stack changes remain after the staged upgrade
- Keep any local branch scoped as a follow-up proof, not as a replacement for `#1006`.

## Why this direction

- The overlap is too large and too active to justify a blind parallel migration branch.
- This workstream is still valuable for proposal evidence if it produces a precise gap analysis and a bounded follow-up prototype rather than duplicated migration churn.
