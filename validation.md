# Validation

## Fresh master

- `yarn install`: passed
- `./run-qa-checks`: passed
- `yarn build-dev`: passed
- `yarn browser-test`: 9 of 10 suites passed
- reproduced baseline failure: `browser-test/password-expired.test.js`

I used `master` as the comparison point for the prototype branches. I do not treat the remaining browser failure as branch-caused because it reproduces before any of the prototype work is applied.

The full local `yarn coverage` run on `master` is still not a reliable branch gate in my environment. It fails early in several suites that do not line up with the branch-level checks below, so I used targeted tests plus browser runs for the implemented branches instead.

## Implemented branch checks

| Branch | What I checked | Result |
| --- | --- | --- |
| `proof-272-registration-redirect` | `registration.test.js`, `organization-wrapper.test.js`, `browser-test/registration.test.js`, `./run-qa-checks` | passed |
| `proof-314-header-unification` | `header.test.js`, changed-file lint, `./run-qa-checks` | passed |
| `proof-918-status-surgical-slice` | `status.test.js`, changed-file lint, `./run-qa-checks` | passed |
| `proof-integration-smoke` | targeted unit suites for registration, wrapper, header, and status; focused browser slice for registration, login, language change, and password change; `./run-qa-checks` | passed |

## Browser checks

The browser runs I rely on are:

- baseline on fresh `master`
- `browser-test/registration.test.js` on the `#272` branch
- focused integration run on:
  - `browser-test/registration.test.js`
  - `browser-test/login.test.js`
  - `browser-test/language-change.test.js`
  - `browser-test/password-change.test.js`

That is enough for me to say the implemented surface is locally validated without pretending the whole repo is green.

## Caveats

- The `password-expired` browser failure still exists on fresh `master`.
- The full local coverage run is still too noisy to use as the main decision point.
- The React 19 and RFC 8908 tracks are analysis-only in this repo, so there is no implementation validation for them here.
