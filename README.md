# WiFi login pages prototype notes

## What this repo contains

This repo collects the notes and validation for my OpenWISP WiFi modernization prototype branches.

## Implemented branches

- `proof-272-registration-redirect`: first redirect-ownership slice for [issue `#272`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/272)
- `proof-314-header-unification`: header HTML cleanup for [issue `#314`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/314)
- `proof-918-status-surgical-slice`: small `Status` refactor for [issue `#918`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/918)
- `proof-947-captive-portal-api-followup`: opt-in RFC 8908 client-side follow-up for [issue `#947`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/947)
- `proof-integration-smoke`: stacked branch used to check that the three implemented slices still work together

## Analysis-only tracks

- `react19-rtl`: notes around the React 18.3 -> 19 path after [PR `#1006`](https://github.com/openwisp/openwisp-wifi-login-pages/pull/1006)

## Validation

- fresh `master` browser baseline: 9 of 10 suites passed
- reproduced baseline failure on `master`: `browser-test/password-expired.test.js`
- [Issue `#272`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/272) has direct unit and browser validation
- [Issue `#947`](https://github.com/openwisp/openwisp-wifi-login-pages/issues/947) has targeted `Status` tests and repo QA validation
- the integration branch passes the targeted unit suites plus the focused browser slice I used for the implemented work
- details are in [validation.md](validation.md)

## Files

- [published-branches.md](published-branches.md): public branch names and short descriptions
- [validation.md](validation.md): what I ran and what I trust
- [overlap-notes.md](overlap-notes.md): how these branches relate to active upstream work
- [artifacts/issue-272/notes.md](artifacts/issue-272/notes.md): redirect slice notes
- [artifacts/issue-314/notes.md](artifacts/issue-314/notes.md): header notes
- [artifacts/issue-918/notes.md](artifacts/issue-918/notes.md): `Status` slice notes
- [artifacts/issue-947/notes.md](artifacts/issue-947/notes.md): RFC 8908 follow-up notes
- [artifacts/react19-rtl/notes.md](artifacts/react19-rtl/notes.md): React follow-up notes
