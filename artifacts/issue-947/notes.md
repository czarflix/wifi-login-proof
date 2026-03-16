# Issue 947 notes

## Context

Issue `#947` is the RFC 8908 captive portal API track. While rechecking the upstream history, I found that [PR `#945`](https://github.com/openwisp/openwisp-wifi-login-pages/pull/945) had already added a basic internal captive portal API route and that it was later removed as unused. A later client-side follow-up, [PR `#1004`](https://github.com/openwisp/openwisp-wifi-login-pages/pull/1004), was closed.

That history matters because the right follow-up is not “put the old endpoint back.” The cleaner missing slice is the smaller client-side, opt-in path the issue already describes: per-organization URL, short timeout, explicit fallback, and no behavior change when it is off.

## What I changed

I implemented a bounded follow-up branch for that missing slice:

- added optional `captive_portal_api` config with `enabled`, `url`, and `timeout`
- mapped that config into `Status`
- added a small RFC 8908 probe helper that sends `Accept: application/captive+json`
- when the response says `captive: false`, the page switches to internet mode and skips radius-usage loading in the same pass
- when the feature is disabled, errors, times out, or returns unexpected data, the current behavior stays unchanged
- documented the new config in the settings docs

## How I checked it

- direct `Status` test path: `./node_modules/.bin/jest --runInBand --runTestsByPath client/components/status/status.test.js`
- `./run-qa-checks`

This is still a bounded client-side prototype. I used mocked tests for the RFC 8908 cases and did not turn it into a larger browser-flow project.

## Open notes

- this branch does not restore the removed internal endpoint from `#945`
- it stays smaller than the closed `#1004` attempt by focusing only on the client-side follow-up needed by `Status`
- I still do not present `#947` as guaranteed project scope in the proposal
