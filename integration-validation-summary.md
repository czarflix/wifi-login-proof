# integration validation summary

Generated: 2026-03-16

## Integration branch

- Local branch: `proof-integration-smoke`
- Head: `42a73e4808196a418968400906602cab7cf9e294`
- Stacked commits:
  - `d03c86b3873d1526bf14ca13fd618ae657e38979` (`#272` proof slice)
  - `3c13d499e8c6053e2679f9ff0de5a8b194e8af0e` (`#314` proof slice)
  - `17e0a904cae43cce3f3614eb6df21f3fc0fcc9a1` (`#918` proof slice)

## Verification run

- `client/components/registration/registration.test.js`: PASS
- `client/components/organization-wrapper/organization-wrapper.test.js`: PASS
- `client/components/header/header.test.js`: PASS
- `client/components/status/status.test.js`: PASS
- `./run-qa-checks`: PASS
- Browser slice:
  - `browser-test/registration.test.js`: PASS
  - `browser-test/login.test.js`: PASS
  - `browser-test/language-change.test.js`: PASS
  - `browser-test/password-change.test.js`: PASS

## Important nuance

- An earlier stacked browser run exposed a real regression in the post-registration redirect path.
- Root cause: the `#272` proof slice moved redirect ownership out of `OrganizationWrapper`, but the registration flow was not yet handling the post-authentication redirect after successful registration.
- Resolution: the `#272` slice now redirects authenticated users both on mount and when authentication state changes after form submission.
- After that fix was committed onto the `#272` proof branch and cherry-picked into the integration branch, the focused integration browser slice passed cleanly.

## Current classification

- Code coexistence proof: strong
- Repo QA wrapper: strong except metadata-only commit-validation complaint
- Browser-stack integration: strong for the implemented proof surface
