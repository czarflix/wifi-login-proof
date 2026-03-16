# overlap-matrix

Generated: 2026-03-16T16:05:26.598382+00:00

## Workstream overlap summary

### React 19 + RTL migration proof
- Issue: #870 - [deps] Upgrade to latest version of react
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/870
- Comparison seed: Existing upstream direction already splits the work at React 18.3 before React 19. Treat this as an extension/comparison-first workstream unless the open PR stalls or diverges.
- Active overlap PRs:
- PR #1006: [deps] Upgraded React to 18.3 #870
  - URL: https://github.com/openwisp/openwisp-wifi-login-pages/pull/1006
  - State: OPEN | mergeState=DIRTY
  - Head: `fix-reactversion-migration` -> Base: `master`
  - Files: .eslintrc.json, .github/workflows/ci.yml, babel.config.js, browser-test/create-mobile-configuration.js, browser-test/initialize_data.py, browser-test/js-file-inject.test.js, ...
  - Reviews: review-bot=COMMENTED, review-bot=COMMENTED, review-bot=COMMENTED, review-bot=COMMENTED, review-bot=COMMENTED
  - Checks: QA-Checks: SUCCESS, Tests and Coverage: SUCCESS, review bot: SUCCESS

### Redirect decomposition from OrganizationWrapper
- Issue: #272 - [change] Move redirect logic from OrganizationWrapper to each component
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/272
- Comparison seed: Current issue discussion already points toward moving redirects into owning components. Compare any local implementation against the proposals already discussed on the issue before widening scope.
- Active overlap PRs: none configured in current scaffold

### Header HTML unification
- Issue: #314 - [change] Eliminate redundancy of header HTML
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/314
- Comparison seed: An active PR already targets this issue. Default posture is comparison-first, then narrower-slice or extension only if upstream work leaves clear gaps.
- Active overlap PRs:
- PR #1048: Issues/314 enhanchment title unify header
  - URL: https://github.com/openwisp/openwisp-wifi-login-pages/pull/1048
  - State: OPEN | mergeState=DIRTY
  - Head: `issues/314-enhanchment-title-unify-header` -> Base: `master`
  - Files: client/components/header/__snapshots__/header.test.js.snap, client/components/header/header.js, client/components/header/header.test.js, client/components/header/index.css, client/utils/needs-verify.js, package-lock.json, ...
  - Reviews: review-bot=CHANGES_REQUESTED, review-bot=CHANGES_REQUESTED, review-bot=CHANGES_REQUESTED, review-bot=COMMENTED, review-bot=APPROVED
  - Checks: QA-Checks: SUCCESS, Tests and Coverage: FAILURE, review bot: SUCCESS

### Surgical Status refactor
- Issue: #918 - [change] Refactor status component to simplify logic and improve maintainability
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/918
- Comparison seed: Maintainers explicitly want surgical iterations, not a full rewrite. Use the issue discussion and the open PR to define a narrowly provable slice before changing code.
- Active overlap PRs:
- PR #1056: [change] Refactored componentDidMount logic for better maintainability
  - URL: https://github.com/openwisp/openwisp-wifi-login-pages/pull/1056
  - State: OPEN | mergeState=BLOCKED
  - Head: `change-status.js` -> Base: `master`
  - Files: client/components/status/status.js
  - Reviews: review-bot=CHANGES_REQUESTED, review-bot=CHANGES_REQUESTED, review-bot=CHANGES_REQUESTED, review-bot=CHANGES_REQUESTED, review-bot=CHANGES_REQUESTED
  - Checks: QA-Checks: SUCCESS, Tests and Coverage: FAILURE, review bot: SUCCESS

### RFC 8908 captive portal API support
- Issue: #947 - [feature] Add support for captive-portal API
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/947
- Comparison seed: The issue is explicitly marked as not suited for beginners and calls for more discussion. Keep the proof branch opt-in and bounded, and document any unresolved product questions before implementation.
- Active overlap PRs: none configured in current scaffold

## Existing own PRs

- PR #1061: [tests] Make add-org interactive test catch config creation regressions
  - URL: https://github.com/openwisp/openwisp-wifi-login-pages/pull/1061
  - State: OPEN | mergeState=BLOCKED
  - Head: `issue-880-add-org-interactive-test` -> Base: `master`
  - Files: config/__tests__/add-org.test.js
  - Reviews: No formal reviews captured
  - Checks: QA-Checks: SUCCESS, Tests and Coverage: SUCCESS, review bot: SUCCESS, coverage/coveralls: SUCCESS

- PR #1062: [deps] Upgrade dompurify to ^3.3.3 #986
  - URL: https://github.com/openwisp/openwisp-wifi-login-pages/pull/1062
  - State: OPEN | mergeState=BLOCKED
  - Head: `deps-dompurify-986` -> Base: `master`
  - Files: package.json, server/controllers/modal-content-controller.test.js, yarn.lock
  - Reviews: No formal reviews captured
  - Checks: QA-Checks: SUCCESS, QA-Checks: SUCCESS, Tests and Coverage: SUCCESS, Tests and Coverage: SUCCESS, review bot: SUCCESS, coverage/coveralls: SUCCESS

## Initial classification defaults

- `react19-rtl`: extension/comparison-first because issue discussion already expects a staged React 18.3 -> 19 path and PR #1006 exists.
- `issue-272`: same-direction local proof is acceptable because the current overlap is discussion-level, not an active PR in the matrix.
- `issue-314`: comparison-first because PR #1048 already targets the issue.
- `issue-918`: comparison-first and surgical-only because PR #1056 exists and maintainer comments explicitly reject a broad rewrite.
- `issue-947`: bounded feature proof only; treat unresolved product questions as blockers, not silent assumptions.

## Current local proof outcome

- `react19-rtl`: comparison/gap-report complete; implementation intentionally deferred behind PR `#1006`
- `issue-272`: implemented and verified locally on `proof-272-registration-redirect`, including browser validation for the registration redirect path
- `issue-314`: implemented and verified locally on `proof-314-header-unification` as a cleaner/narrower comparison branch
- `issue-918`: implemented and verified locally on `proof-918-status-surgical-slice` as a narrower surgical slice than PR `#1056`
- `issue-947`: blocker-aware comparison/design report complete; implementation intentionally deferred
