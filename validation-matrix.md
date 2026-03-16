# validation-matrix

Generated: 2026-03-16

## Validation matrix

| Surface | Fresh `master` | `issue-272` proof branch | Integration proof branch | Classification |
| --- | --- | --- | --- | --- |
| `yarn install` | PASS | inherited baseline | inherited baseline | healthy baseline |
| `./run-qa-checks` | PASS | PASS | PASS | branch code healthy |
| `yarn build-dev` / app startup | PASS | inherited baseline | PASS via split server + webpack startup | healthy baseline |
| `yarn coverage` | FAIL | not used as branch gate | not used as branch gate | environment-sensitive baseline red on local Node `v25.2.1` |
| `browser-test/password-expired.test.js` | FAIL | not part of proof gate | not part of proof gate | pre-existing baseline failure |
| `browser-test/registration.test.js` | PASS | PASS | PASS | `#272` redirect slice validated |
| `browser-test/login.test.js` | PASS | not rerun separately | PASS | auth/status landing still healthy |
| `browser-test/language-change.test.js` | PASS | not rerun separately | PASS | header/language behavior still healthy |
| `browser-test/password-change.test.js` | PASS | not rerun separately | PASS | status/password flow still healthy |
| `client/components/registration/registration.test.js` | baseline red run not trusted | PASS | PASS | branch-specific validation healthy |
| `client/components/organization-wrapper/organization-wrapper.test.js` | baseline red run not trusted | PASS | PASS | redirect ownership change remains stable |
| `client/components/header/header.test.js` | baseline red run not trusted | inherited baseline | PASS | `#314` slice stable in integration |
| `client/components/status/status.test.js` | baseline red run not trusted | inherited baseline | PASS | `#918` slice stable in integration |

## Read this matrix carefully

- `Fresh master` is the branch-comparison baseline, not a claim that every local command is green.
- The full `yarn coverage` run is red locally on fresh `master`, so branch integrity is judged primarily through targeted suites plus browser validation.
- The strongest evidence is:
  - `#272` proof branch has direct unit + browser validation
  - the integration branch passes the targeted unit suites plus the focused browser slice that covers the implemented proof surface
