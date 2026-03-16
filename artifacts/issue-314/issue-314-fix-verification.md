# issue-314 fix verification

Generated: 2026-03-16T15:59:18.693276+00:00

## Issue-to-change map

- Targeted surface:
  - `client/components/header/header.js`
  - `client/components/header/index.css`
  - `client/components/header/header.test.js`
  - `browser-test/language-change.test.js`
- Required outcome:
  - remove duplicated desktop/mobile header markup
  - keep the header responsive through CSS and menu state
  - preserve link visibility, internal/external handling, logo rendering, language switching, and hamburger behavior
- Explicitly out of scope for this proof slice:
  - broader header redesign
  - unrelated dependency/script changes present in PR `#1048`
  - broader captive-portal or auth logic changes outside the header surface

## Pass 1 candidate

- Replaced the separate desktop and mobile render trees with one responsive header structure:
  - one branding block
  - one navigation block
  - one language-button group
  - hamburger state only controls mobile visibility
- Normalized link rendering through a single `renderHeaderLinks()` path and language rendering through a single `renderLanguageButtons()` path.
- Updated the browser language-change selector to use the unified language-button classes.

## Pass 2 rethink

- Re-asked the issue from scratch after pass 1: is the right proof a helper-based refactor or a single DOM structure?
- Conclusion: the single DOM structure is the cleaner proof because the issue is specifically about eliminating duplicated HTML, not only duplicated helper logic.
- Kept the final shape narrower than PR `#1048` by avoiding unrelated script/build changes and preserving the existing hamburger/menu interaction model.

## Red-green proof

- Focused regression check after `yarn setup`:
  - `./node_modules/.bin/jest --runTestsByPath client/components/header/header.test.js --runInBand -u`
  - result: PASS, 18 tests / 4 snapshots
- Changed-files lint check:
  - `./node_modules/.bin/eslint client/components/header/header.js client/components/header/header.test.js browser-test/language-change.test.js`
  - result: PASS
- Repo QA wrapper:
  - `./run-qa-checks`
  - result: PASS

## Validation outcomes

- Local proof branch: `proof-314-header-unification`
- Verified local commit: `3c13d499e8c6053e2679f9ff0de5a8b194e8af0e`
- Comparison outcome versus PR `#1048`:
  - same direction, cleaner/narrower implementation
  - no unrelated `package.json` or `needs-verify` changes
- Remaining limit:
  - browser-level validation for the unified header is still pending full `openwisp-radius` runtime setup, so this branch is strong local proof but not yet a full browser-verified PR candidate.
