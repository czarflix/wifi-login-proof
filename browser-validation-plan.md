# browser-validation-plan

This runbook records the local steps used to move from the initial proof repo to a working browser-validation setup, plus the current classification of what passed.

## Local paths

- WiFi app checkout: `<local WiFi checkout>`
- Radius checkout: `<local Radius checkout>`

## Current prerequisite state

- Docker daemon: reachable
- Geckodriver: installed
- Firefox: available as macOS app bundle and exported into `PATH` for validation runs
- openwisp-radius: cloned, installed in a Python 3.11 virtual environment, migrated, and started locally for validation

## Local environment preparation used

1. Export Firefox binary directory into `PATH` for this shell:
   - `export PATH="/Applications/Firefox.app/Contents/MacOS:$PATH"`
2. Export the Radius path:
   - `export OPENWISP_RADIUS_PATH=<local Radius checkout>`
3. From the Radius checkout:
   - install Python dependencies in a dedicated virtual environment
   - run migrations using the repo's test management entrypoint
   - start the local Redis container required by the test setup
4. From the WiFi checkout:
   - run `node browser-test/create-mobile-configuration.js`
   - run `npm run setup`
   - start the WiFi server and webpack dev server separately
5. Start OpenWISP Radius locally using the test configuration expected by the browser tests.
6. Run browser tests against both:
   - fresh `master`
   - the integration proof branch

## Current classification

- Fresh `master` baseline:
  - 9 / 10 suites passed
  - `browser-test/password-expired.test.js` failed
  - this failure is treated as a baseline issue, not as proof-branch fallout
- Proof-branch browser validation:
  - `browser-test/registration.test.js`: PASS
  - `browser-test/login.test.js`: PASS
  - `browser-test/language-change.test.js`: PASS
  - `browser-test/password-change.test.js`: PASS
- These four suites cover the implemented proof surface for:
  - registration redirect ownership (`#272`)
  - header rendering / language-switch behavior (`#314`)
  - status landing after auth and password change (`#918`)

## Important classification rule

- Do not attribute browser-test failures to a proof branch until this baseline flow has been executed successfully or the baseline blocker has been clearly classified.
