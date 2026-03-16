# baseline-validation-summary

Generated: 2026-03-16T16:00:00+05:30

## Fresh master baseline

- Repo path: `<local WiFi checkout>`
- Branch / SHA: `master` @ `c2813c5a72214fb465d42e5c3e2e757931274a85`
- Goal: classify what is already healthy on a fresh checkout before any proof branches diverge.

## Command results

- `yarn install`
  - Result: success
  - Log: `logs/baseline-yarn-install.log`
- `./run-qa-checks`
  - Result: success
  - Log: `logs/baseline-run-qa-checks.log`
- `yarn build-dev`
  - Result: success
  - Log: `logs/baseline-yarn-build-dev.log`
- `yarn coverage`
  - Result: failed locally
  - Log: `logs/baseline-yarn-coverage.log`
- `yarn browser-test`
  - Result: baseline reproduced with 9 / 10 suites passing
  - Failure: `browser-test/password-expired.test.js`
  - Classification: pre-existing baseline failure on fresh `master`, not caused by proof branches

## Current classification

- Install / setup / lint / build baseline is healthy on fresh `master`.
- Local Jest coverage is currently red on fresh `master` under local Node `v25.2.1`.
- The failure pattern is environment-sensitive / baseline-only:
  - it reproduces on fresh `master`
  - the implemented proof branches still pass the targeted Jest suites that cover the touched surfaces
  - the browser baseline and integration browser slice do not point to the same component breakage as branch-caused fallout
- Browser validation is no longer missing. The fresh `master` baseline is partially green and gives a usable comparison point for the proof branches.

## Coverage failure pattern observed

- Many failing suites crash early while reading `defaultConfig.components.<name>` in component tests.
- Representative examples from the log:
  - `payment-status.test.js`
  - `login.test.js`
  - `footer.test.js`
  - `404.test.js`
  - `contact.test.js`
  - `organization-wrapper.test.js`
- Additional signal:
  - the run was executed under local Node `v25.2.1`, which is outside the version normally expected by older React/Jest setups in this repo
  - targeted suites invoked directly after `npm run setup` do not reproduce the same failure pattern
- Summary from the baseline log:
  - `Test Suites: 13 failed, 10 passed, 23 total`
  - `Tests: 13 failed, 231 passed, 244 total`

## What this means for proof branches

- Future branch validation must compare against this baseline instead of assuming every red test is branch-caused.
- The current red coverage run should be treated as a baseline environment-sensitive signal until it is reproduced under a project-aligned Node version.
