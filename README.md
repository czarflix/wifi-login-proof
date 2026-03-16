# WiFi Login Pages proof repo

This repo is the evidence layer for a fact-based OpenWISP GSoC 2026 application focused on `openwisp-wifi-login-pages`.

## Purpose

- keep archaeology, RCA, verification, comparison, and complete reports per workstream
- track overlap with active upstream PRs and existing own PRs
- attach screenshots, GIFs, and validation logs once code proof branches exist
- strengthen the final proposal with public, inspectable prototype evidence

## Workstreams

- `react19-rtl` -> issue `#870`
- `issue-272` -> redirect decomposition from `OrganizationWrapper`
- `issue-314` -> header HTML unification
- `issue-918` -> surgical `Status` refactor
- `issue-947` -> RFC 8908 captive portal API support

## Prior evidence already available

- openwisp-wifi-login-pages PR `#1061`
- openwisp-wifi-login-pages PR `#1062`
- openwisp-utils PR `#620`
- openwisp-users PR `#492`

These are referenced as prior evidence, not as the base for the whole proof effort.

## Structure

- `artifacts/<workstream>/` -> archaeology and verification packets
- `branch-map.md` -> local proof branch layout and intended ownership
- `baseline-validation-summary.md` -> current install/build/test classification on fresh `master`
- `browser-validation-plan.md` -> runbook for the full browser-test baseline
- `integration-validation-summary.md` -> stacked proof-branch coexistence notes
- `overlap-matrix.md` -> issue/PR overlap status



## Current environment notes

- Node / Python: collected separately during baseline validation
- Firefox: present as macOS app bundle, not on PATH (`/Applications/Firefox.app/Contents/MacOS/firefox`)
- Geckodriver: present (`/opt/homebrew/bin/geckodriver`)
- Docker for browser-test stack: ready - daemon reachable
- openwisp-radius checkout: present - <local Radius checkout>

Current browser-test status:

- fresh `master` baseline: 9 / 10 browser suites passed
- reproduced baseline failure: `browser-test/password-expired.test.js`
- implemented proof surface on the integration branch:
  - `browser-test/registration.test.js`: PASS
  - `browser-test/login.test.js`: PASS
  - `browser-test/language-change.test.js`: PASS
  - `browser-test/password-change.test.js`: PASS

Browser validation is now strong enough to support the implemented proof slices. Remaining browser coverage outside these flows should still be treated as broader repo baseline work, not as proof-branch fallout.

## Current proof status

- `issue-272`: implemented and locally verified on `proof-272-registration-redirect` @ `d03c86b3873d1526bf14ca13fd618ae657e38979`
- `issue-314`: implemented and locally verified on `proof-314-header-unification` @ `3c13d499e8c6053e2679f9ff0de5a8b194e8af0e`
- `issue-918`: implemented and locally verified on `proof-918-status-surgical-slice` @ `17e0a904cae43cce3f3614eb6df21f3fc0fcc9a1`
- `react19-rtl`: comparison/gap report completed; no duplicate local migration branch started beyond baseline
- `issue-947`: blocker-aware comparison/design report completed; no speculative code branch started beyond baseline
- `proof-integration`: stacked local coexistence proof recorded in `integration-validation-summary.md` @ `42a73e4808196a418968400906602cab7cf9e294`
