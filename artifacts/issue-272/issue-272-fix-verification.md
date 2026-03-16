# issue-272 fix verification

Generated: 2026-03-16T15:59:18.692250+00:00

## Issue-to-change map

- Goal of this proof slice: move the `registration/*` redirect ownership out of `OrganizationWrapper` and into `Registration`.
- Changed files:
  - `client/components/organization-wrapper/organization-wrapper.js`
  - `client/components/organization-wrapper/organization-wrapper.test.js`
  - `client/components/organization-wrapper/__snapshots__/organization-wrapper.test.js.snap`
  - `client/components/registration/index.js`
  - `client/components/registration/registration.js`
  - `client/components/registration/registration.test.js`
- Explicitly out of scope for this slice:
  - moving every other wrapper redirect
  - touching `Status`
  - changing payment flow ownership
  - router-wide refactors

## Pass 1 candidate

- Pass-1 implementation:
  - wire `isAuthenticated` and `userData` into `Registration` from Redux
  - redirect from `Registration.componentDidMount()` to either:
    - `/${orgSlug}/status`, or
    - `/${orgSlug}/mobile-phone-verification`
  - simplify the wrapper route so `registration/*` always renders `Registration`
- Added focused regression tests in `registration.test.js` for:
  - authenticated user redirect to status
  - authenticated user redirect to mobile verification when phone verification is needed

## Pass 2 rethink

- Rethink question: should this slice also move `mobile-phone-verification` route ownership at the same time?
- Decision: no.
- Reason:
  - the registration route already proves the ownership pattern with a bounded diff
  - extending the same branch into verification or status would widen the surface and make failure classification harder
  - the issue discussion itself suggests validating one component move first

## Red-green proof

- Focused test run:
  - `./node_modules/.bin/jest --runTestsByPath client/components/registration/registration.test.js --runInBand`
  - Result: pass
- Focused wrapper route run with snapshot update:
  - `./node_modules/.bin/jest --runTestsByPath client/components/organization-wrapper/organization-wrapper.test.js --runInBand -u`
  - Result: pass
- Repo QA wrapper:
  - `./run-qa-checks`
  - Result: pass
- Notes:
  - a broader `yarn test client/components/...` invocation pulled in unrelated suites including a pre-existing `config/__tests__/add-org.test.js` failure, so exact-path Jest runs were used for branch-caused verification instead of pattern-based runs.

## Validation outcomes

- The smallest clean proof for `#272` is viable: `registration/*` no longer requires wrapper-owned redirect logic for the authenticated cases covered here.
- Wrapper complexity is reduced without changing the visible registration route contract.
- The branch is not presented as a full solution to `#272`; it is a verified first ownership move consistent with the issue discussion.
