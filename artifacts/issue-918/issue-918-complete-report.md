# issue-918 complete report

Generated: 2026-03-16T15:59:18.695055+00:00

## Archaeology summary

- Maintainers explicitly rejected a broad rewrite and pointed to the login/logout/macaddr decision block as the right starting point.
- Upstream overlap exists in PR `#1056`, which already demonstrates that large `Status` diffs attract review friction and test fallout.
- The local proof therefore stayed comparison-first and intentionally narrower than the open PR.

## Root cause

- `componentDidMount` mixed user-info preparation, stored-state resolution, logout handling, login submission, and fallback to `finalOperations()` in one linear block.
- The block was hard to reason about because the branch conditions were correct but densely interleaved.

## Implementation summary

- Extracted stored-state resolution into `resolvePendingPortalState()`.
- Extracted user-info shaping into `prepareUserInfo()`.
- Extracted the pending login/logout/final-operations branch into `handlePendingPortalAction()`.
- Left the rest of `Status` intact.

## Verification summary

- `status.test.js` passed in isolation on the proof branch with 74 passing tests.
- `./run-qa-checks` passed on the proof branch.
- This is strong local proof for a surgical `Status` slice and aligns with the maintainer’s preferred iteration style.

## Proposal impact

- The proposal can now point to a real local prototype for issue `#918`, but it should still describe the `Status` work as iterative and surgical.
- Safe wording:
  - one bounded `Status` refactor slice has been locally prototyped and validated
  - the slice was deliberately chosen to avoid duplicating the broader open PR
