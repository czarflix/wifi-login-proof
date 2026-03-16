# proposal-proof-upgrade-notes

Use this note only after the proof branches or proof repo are public under the applicant's GitHub account.

## Exact dating to use

- Replace vague phrasing such as "for a month or so" with exact language such as:
  - `Since March 2026, I have been building local prototype branches and evidence packets for the main WiFi modernization workstreams.`

## Safe proposal wording

- `To reduce execution risk, I set up a fresh local proof repo for openwisp-wifi-login-pages and documented issue archaeology, overlap analysis, and local validation notes for the main WiFi workstreams.`
- `I also created prototype branches for the main workstreams so the proposal is based on locally validated implementation planning rather than scope guesses.`
- `These prototypes are not presented as merged work; they are public proof artifacts used to refine feasibility, testing scope, and backward-compatibility constraints.`
- `For issue #272, issue #314, and a surgical issue #918 slice, I already have locally validated proof branches with focused test evidence.`
- `For React 19 and RFC 8908, I completed comparison and gap analysis so the proposal does not overpromise work that still depends on upstream staging or maintainer clarification.`

## Links to add once public

- proof repo README
- branch map
- public branch map
- archaeology / RCA / comparison reports per workstream
- screenshots or GIFs
- validation logs or short summaries

## Expected public URLs if the proof repo is created as `czarflix/wifi-login-proof`

- Proof repo README:
  - `https://github.com/czarflix/wifi-login-proof`
- Proof branch map:
  - `https://github.com/czarflix/wifi-login-proof/blob/main/branch-map.md`
- Validation matrix:
  - `https://github.com/czarflix/wifi-login-proof/blob/main/validation-matrix.md`
- Integration summary:
  - `https://github.com/czarflix/wifi-login-proof/blob/main/integration-validation-summary.md`
- Proof branches in the WiFi fork:
  - `https://github.com/czarflix/openwisp-wifi-login-pages/tree/proof-272-registration-redirect`
  - `https://github.com/czarflix/openwisp-wifi-login-pages/tree/proof-314-header-unification`
  - `https://github.com/czarflix/openwisp-wifi-login-pages/tree/proof-918-status-surgical-slice`
  - `https://github.com/czarflix/openwisp-wifi-login-pages/tree/proof-integration-smoke`

## Suggested evidence paragraph

`Since March 2026, I have been building local prototype branches and evidence packets for the main WiFi modernization workstreams. I documented issue archaeology, overlap analysis, and local validation in a public proof repo, and I also published prototype branches for the implemented #272, #314, and #918 slices. These are not presented as merged work; they are public proof artifacts used to refine feasibility, testing scope, and backward-compatibility constraints.`

## Public branch naming

- Keep local private working branches branch names private.
- Push public proof branches using the clean names in `public-branch-map.md`.

## Claims to avoid even after publication

- Do not say the whole WiFi roadmap is finished.
- Do not say the prototypes are already ready to merge unless a specific branch truly is PR-ready.
- Do not describe local proof branches as accepted upstream work.
