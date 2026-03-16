# issue-918 fix verification

Generated: 2026-03-16T15:59:18.694588+00:00

## Issue-to-change map

- Targeted surface:
  - the `componentDidMount` login/logout decision block in `client/components/status/status.js`
- Required outcome:
  - keep the refactor surgical
  - preserve current login, logout, bank-card, and final-operations behavior
  - improve readability by isolating pending captive-portal state resolution and action handling
- Explicitly out of scope:
  - full `Status` rewrite
  - hooks migration
  - broader `finalOperations()` redesign
  - unrelated cleanup from PR `#1056`

## Pass 1 candidate

- Extracted three narrow helpers:
  - `resolvePendingPortalState()`
  - `prepareUserInfo()`
  - `handlePendingPortalAction()`
- Replaced the inline block in `componentDidMount` with those helpers while preserving the same early exits and side effects.

## Pass 2 rethink

- Compared the pass-1 extraction against the maintainer guidance and PR `#1056`.
- Rejected a broader helper split that would have started duplicating the open PR’s larger refactor.
- Kept the final change limited to the exact decision block the maintainers called out, which matches the “surgical iterations” guidance better than a larger reorganization.

## Red-green proof

- Changed-file lint check:
  - `./node_modules/.bin/eslint client/components/status/status.js`
  - result: PASS
- Focused regression check:
  - `./node_modules/.bin/jest --runTestsByPath client/components/status/status.test.js --runInBand`
  - result: PASS, 74 tests
- Repo QA wrapper:
  - `./run-qa-checks`
  - result: PASS

## Validation outcomes

- Local proof branch: `proof-918-status-surgical-slice`
- Verified local commit: `17e0a904cae43cce3f3614eb6df21f3fc0fcc9a1`
- Comparison outcome versus PR `#1056`:
  - same direction, narrower slice
  - focused only on the pending portal decision block instead of broader `componentDidMount` extraction
- Remaining limit:
  - no new browser-level scenario was added in this proof slice because the changed surface is internal control flow inside an already heavily tested component; browser-stack verification remains part of the later full stack proof.
