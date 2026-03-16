# react19-rtl RCA

Generated: 2026-03-16T15:59:18.690223+00:00

## Observed problem

- The current dependency and test stack is still anchored to React 17:
  - `package.json` uses `react` / `react-dom` `^17.0.2`
  - `react-test-renderer` is also on the React 17 line
  - Enzyme and `@wojtekmaj/enzyme-adapter-react-17` are wired into the current test setup (`config/jest.config.js:1-2`, `package.json`)
- The issue discussion and PR `#1006` show that maintainers already expect a staged path:
  - React 18.3 first
  - then React 19 as a follow-up once deprecations and test migration are under control
- This means the proof branch cannot honestly start from “upgrade directly to React 19 and fix whatever breaks.”

## Hypotheses

- The blocking factor is not only React itself; the bigger migration cost is the Enzyme-based test stack and adjacent libraries that assume the older React testing model.
- A useful proof branch for this workstream is comparison-first: validate how far PR `#1006` already gets, then measure the remaining React 19 delta rather than duplicating all of that migration work.
- The local baseline coverage failure also needs to be normalized before React migration fallout can be classified cleanly.

## Rejected hypotheses

- This is not a one-commit dependency bump.
- It should not be treated as independent from the testing stack.
- It is not responsible to claim a clean React 19 path without comparing against the already-open React 18.3 work.

## Root cause

- The repository’s runtime and test layers are coupled to the React 17 ecosystem.
- Enzyme is effectively legacy tooling here, so the migration burden includes both dependency compatibility and test paradigm migration.
- Because upstream work is already in flight on the staged upgrade path, the first proof obligation is comparison and gap identification, not blind reimplementation.

## Fix-shaping constraints

- Keep this workstream comparison-first against PR `#1006`.
- Separate:
  - what `#1006` already proves locally
  - what still blocks React 19
  - what becomes a true follow-up proof branch
- Do not merge React upgrade proof with unrelated refactor goals.
- Any local proof must preserve test readability and leave a concrete migration note, not just a dependency diff.
