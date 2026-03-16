# react19-rtl archaeology

Generated: 2026-03-16T16:05:26.594564+00:00

## Issue identity
- Repo: `openwisp/openwisp-wifi-login-pages`
- Issue: #870 - [deps] Upgrade to latest version of react
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/870
- State: OPEN
- Author: nemesifier
- Labels: dependencies
- Assignees: None

## Issue statement

## Recommended Upgrade Path

Upgrade to React 18.3 First: React 18.3 includes deprecation warnings for features removed in React 19, helping identify necessary code changes.​

## Run Codemods:

Utilize the official React 19 codemods to automate common refactorings, eg:

    npx codemod@latest react/19/migration-recipe

## Update Dependencies

Ensure all dependencies are compatible with React 19.

Check for updates or replacements for packages that are no longer maintained.​

Dependencies depending on react:
- [enzyme is dead](https://dev.to/wojtekmaj/enzyme-is-dead-now-what-ekl), we'll need to migrate away from it. It seems that the most widely used and maintained alternative is React Testing Library (RTL), but it's not a drop in replacement.
- react-dom: `{ react: '^19.1.0' }`
- react-cookie: `{ react: '>= 16.3.0' }`
- react-countdown: `{ react: '>= 15', 'react-dom': '>= 15' }`
- react-helmet: { react: '>=16.3.0' }
- react-side-effect: `{ react: '^16.3.0 || ^17.0.0 || ^18.0.0' }`
- react-infinite-scroll-component: `{ react: '>=16.0.0' }`
- react-phone-input: `{ lodash: '^4.11.1', react: '^0.14.8 || ^15.0.1' }`
- react-redux:
  ```
  {
    '@types/react': '^18.2.25 || ^19',
    react: '^18.0 || ^19',
    redux: '^5.0.0'
  }
  ```
- react-router-dom: `{ react: '>=18', 'react-dom': '>=18' }`
- react-router: `{ react: '>=18', 'react-dom': '>=18' }`
- react-select:
  ```
  {
    react: '^16.8.0 || ^17.0.0 || ^18.0.0 || ^19.0.0',
    'react-dom': '^16.8.0 || ^17.0.0 || ^18.0.0 || ^19.0.0'
  }
  ```
- react-transition-group: `{ react: '>=16.6.0', 'react-dom': '>=16.6.0' }`
- use-isomorphic-layout-effect: `{ react: '^16.8.0 || ^17.0.0 || ^18.0.0 || ^19.0.0' }`
- react-test-renderer: `{ react: '^19.1.0' }`
- react-toastify: `{ react: '^18 || ^19', 'react-dom': '^18 || ^19' }`

## Test Thoroughly

After making the necessary changes, run your test suite to catch any regressions or issues introduced during the upgrade.​

## Maintainer and discussion highlights

### PRoIISHAAN on 2025-12-18T18:52:30Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/870#issuecomment-3671742032
- Association: CONTRIBUTOR

hi @nemesifier , i would like to work on this issue

### nemesifier on 2025-12-22T17:08:16Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/870#issuecomment-3682960097
- Association: MEMBER

@PRoIISHAAN I recommend that you should start with easier issues before trying with this issue, which is not easy at all.

### PRoIISHAAN on 2025-12-23T07:43:26Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/870#issuecomment-3685576704
- Association: CONTRIBUTOR

hi @nemesifier  I  had started working on this issue, i havd migrated the tests to use RTL, only one test suite is left for migration, and i have successfully upgraded to react 18.3, starting upgrade to 19 now

### nemesifier on 2025-12-23T13:14:08Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/870#issuecomment-3686601034
- Association: MEMBER

@PRoIISHAAN before you do further work, please open a PR for 18.3 so we can verify,

See also other dependabot PRs which need manual intervention, eg: https://github.com/openwisp/openwisp-wifi-login-pages/pull/963.

### vikram-2101 on 2026-03-05T06:11:20Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/870#issuecomment-4002496832
- Association: NONE

I've reviewed PR #1006 and the RTL migration work. I'd like to help move this forward by:

Reviewing the open PR and testing it locally
Once React 18.3 is merged, I can pick up the React 19 upgrade path (running npx codemod@latest react/19/migration-recipe and fixing regressions)
@nemesifier  would you like me to start on the React 18.3 → 19 step as a follow-up PR after #1006 merges?


## Overlap with current PR activity

- PR #1006: [deps] Upgraded React to 18.3 #870 (OPEN, mergeState=DIRTY)
  - URL: https://github.com/openwisp/openwisp-wifi-login-pages/pull/1006
  - Head: `fix-reactversion-migration` -> Base: `master`
  - Files touched: 88
  - Checks: QA-Checks: SUCCESS, Tests and Coverage: SUCCESS, review bot: SUCCESS

## Comparison seed

Existing upstream direction already splits the work at React 18.3 before React 19. Treat this as an extension/comparison-first workstream unless the open PR stalls or diverges.

## Local proof posture

- Start with archaeology and RCA before touching code.
- Keep the local proof branch independent from the overlapping PR unless comparison shows a clean extension path.
- Record exactly which parts of the issue remain open after comparing against active work.

## Next artifacts

- `react19-rtl-rca.md`
- `react19-rtl-fix-verification.md`
- `react19-rtl-comparison.md`
- `react19-rtl-complete-report.md`
