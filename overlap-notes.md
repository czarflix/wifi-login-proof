# Overlap notes

## Why these branches are narrow

I did not want these prototype branches to duplicate active upstream work or claim ownership over parts of the WiFi roadmap that already have open PRs. The implemented branches are meant to show that I can study the ongoing work, choose a safe slice, and validate it.

## Active overlap I accounted for

### React follow-up

- issue `#870`
- active PR: `#1006`

I treated this as analysis-only because `#1006` is already the staged React 18.3 branch. Re-implementing that work in parallel would add noise, not signal.

### Header cleanup

- issue `#314`
- active PR: `#1048`

My local branch follows the same general direction but keeps the change tighter. I avoided the unrelated cleanup mixed into the open PR and focused only on the duplicated header structure.

### Status refactor

- issue `#918`
- active PR: `#1056`

This area is clearly review-sensitive. I kept my branch smaller than the open PR and stayed inside the maintainer guidance about surgical iterations.

### Redirect ownership

- issue `#272`

There was no active PR in this area when I prepared these notes, so I used it as the cleanest place to build a first implemented slice.

## Existing PRs I already had open

- `#1061`
- `#1062`

Those PRs are part of my repo-specific OpenWISP history, but they are not dependencies for the branches in this repo.
