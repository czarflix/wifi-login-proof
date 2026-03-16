# issue-272 comparison report

Generated: 2026-03-16T15:59:18.692612+00:00

## Existing issue guidance

- Maintainer guidance from `codesankalp` supports moving redirect handling into the owning components so `OrganizationWrapper` becomes cleaner.
- Recent contributor discussion from `vikram-2101` already proposed a component-by-component split:
  - verification redirect into verification-related components
  - payment redirect into payment/registration flow
  - auth redirect into `Status`
- My own issue comment on 2026-03-16 already commits to a narrow redirect-ownership fix plus focused regression tests.

## Overlap with open PRs

- No active upstream PR was captured for issue `#272` in the current overlap matrix.
- This means the workstream is comparison-against-discussion rather than comparison-against-code for now.

## Comparison against own PRs

- PR `#1061` only touches `config/__tests__/add-org.test.js`; it is evidence of test discipline but not a code dependency for this workstream.
- PR `#1062` only touches `dompurify` and a server-side modal-content controller test; it is also not a direct dependency for redirect work.
- Result: treat this proof branch as independent from both existing WiFi PRs.

## Chosen direction

- Same direction as maintainer guidance and recent contributor discussion, but deliberately narrower.
- Start with one or two high-risk redirect flows instead of trying to migrate every wrapper-level redirect in one pass.
- Use focused regression tests to prove that redirect ownership moves without introducing duplicate navigation.

## Why this direction

- There is no active competing PR to displace.
- The issue discussion already validates the architectural direction, so a local proof branch can spend effort on bounded implementation rather than reopening the design debate.
- This is the cleanest workstream to turn into a fact-based public proof because overlap risk is lower than for `#314`, `#918`, or React.
