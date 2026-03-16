# Overlap notes

## Why these branches are narrow

I did not want these prototype branches to duplicate active upstream work or claim ownership over parts of the WiFi roadmap that already have open PRs. The implemented branches are meant to show that I can study the ongoing work, choose a safe slice, and validate it.

## Active overlap I accounted for

### React follow-up

- [issue `#870`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/870)
- active PR: [#1006](https://github.com/openwisp/openwisp-wifi-login-pages/pull/1006)

I treated this as analysis-only because `#1006` is already the staged React 18.3 branch. Re-implementing that work in parallel would add noise, not signal.

### Header cleanup

- [issue `#314`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/314)
- active PR: [#1048](https://github.com/openwisp/openwisp-wifi-login-pages/pull/1048)

My local branch follows the same general direction but keeps the change tighter. I avoided the unrelated cleanup mixed into the open PR and focused only on the duplicated header structure.

### Status refactor

- [issue `#918`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/918)
- active PR: [#1056](https://github.com/openwisp/openwisp-wifi-login-pages/pull/1056)

This area is clearly review-sensitive. I kept my branch smaller than the open PR and stayed inside the maintainer guidance about surgical iterations.

### Redirect ownership

- [issue `#272`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/272)

There was no active PR in this area when I prepared these notes, so I used it as the cleanest place to build a first implemented slice.

### RFC 8908 follow-up

- [issue `#947`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/947)
- merged PR: [#945](https://github.com/openwisp/openwisp-wifi-login-pages/pull/945)
- closed PR: [#1004](https://github.com/openwisp/openwisp-wifi-login-pages/pull/1004)

I did not treat `#947` as a blank-slate feature. The repo already had a merged internal endpoint in `#945`, and that endpoint was later removed as unused. My follow-up branch stays narrower than both of those earlier attempts: it only adds the opt-in client-side config and RFC 8908 probe needed by `Status`, and it does not restore the removed server path.

## Existing PRs I already had open

- [#1061](https://github.com/openwisp/openwisp-wifi-login-pages/pull/1061)
- [#1062](https://github.com/openwisp/openwisp-wifi-login-pages/pull/1062)

Those PRs are part of my repo-specific OpenWISP history, but they are not dependencies for the branches in this repo.
