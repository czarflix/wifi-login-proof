# issue-314 complete report

Generated: 2026-03-16T15:59:18.693513+00:00

## Archaeology summary

- Issue `#314` asks for redundant header HTML to be removed, with CSS handling responsive differences instead of separate desktop/mobile markup.
- Upstream overlap exists in PR `#1048`, but that branch also mixed in unrelated cleanup and currently has unresolved review/test history.
- The local proof branch was therefore scoped as a cleaner, comparison-first implementation rather than a blind duplicate.

## Root cause

- `header.js` maintained two largely parallel render trees for desktop and mobile.
- The duplication covered logos, links, active-link logic, and language buttons, which inflated both maintenance cost and test surface.

## Implementation summary

- Implemented a single responsive header structure in `client/components/header/header.js`.
- Moved all link rendering into one path and all language rendering into one path.
- Kept responsiveness in CSS through `header-navigation`, `menu-open`, and `menu-closed` states.
- Updated `browser-test/language-change.test.js` to match the unified button selectors.

## Verification summary

- `header.test.js` passed in isolation on the proof branch with updated snapshots.
- Changed-files eslint passed.
- `./run-qa-checks` passed on the proof branch.
- Browser-level verification is still pending the full local browser-test stack, so the proof is strong at unit/QA level but not yet browser-complete.

## Proposal impact

- This workstream can now be described in the proposal as a locally validated prototype branch rather than a scope guess.
- Safe proposal wording:
  - a bounded header-unification prototype exists locally
  - the prototype was compared against the active upstream PR rather than developed blindly
  - browser validation remains a known final check before PR-readiness
