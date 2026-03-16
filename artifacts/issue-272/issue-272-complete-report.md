# issue-272 complete report

Generated: 2026-03-16T15:59:18.692766+00:00

## Archaeology summary

- Issue `#272` and maintainer discussion support moving redirect logic into owning components to avoid repeated redirect evaluation in `OrganizationWrapper`.
- There is no active overlap PR in the current matrix, but recent contributor discussion already pointed toward moving one component at a time.

## Root cause

- `OrganizationWrapper` encoded redirect policy inside render-time route elements, so rerenders can reevaluate ownership that belongs to route components.
- The registration route was a clean first candidate because it only needed auth and verification state that already exist in Redux.

## Implementation summary

- Moved authenticated registration-route redirects into `Registration.componentDidMount()`.
- Added Redux state wiring for `isAuthenticated` and `userData`.
- Simplified `OrganizationWrapper` so the `registration/*` route always renders `Registration`.
- Added direct component tests plus updated wrapper route expectations.

## Verification summary

- `registration.test.js`: green on exact-path run
- `organization-wrapper.test.js`: green on exact-path run with updated snapshots
- `./run-qa-checks`: green
- Remaining baseline caveat: full coverage on fresh `master` is still not fully classified, so branch cleanliness is proven through focused exact-path verification plus repo QA, not through a full green coverage run yet.

## Proposal impact

- This gives the proposal a defensible public claim of local prototype work for one `#272` slice.
- It also gives a concrete example of building on issue discussion rather than solving blindly.
- If pushed publicly, this branch can support wording such as:
  - `I have already prototyped and locally validated a first redirect-ownership slice for issue #272.`
