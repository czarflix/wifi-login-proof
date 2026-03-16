# issue-918 archaeology

Generated: 2026-03-16T16:05:26.597406+00:00

## Issue identity
- Repo: `openwisp/openwisp-wifi-login-pages`
- Issue: #918 - [change] Refactor status component to simplify logic and improve maintainability
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/918
- State: OPEN
- Author: pandafy
- Labels: enhancement
- Assignees: None

## Issue statement

The current status component in `client/components/status/status.js` has grown to be very large and complex. It handles multiple responsibilities, including authentication, verification, payment, session management, captive portal logic, and UI rendering. This makes the codebase difficult to understand and maintain. The complexity also increases the risk of bugs and makes testing more difficult.

I opened this issue to gather information. **We need to discuss the changes before doing any changes.**

## Maintainer and discussion highlights

### nemesifier on 2025-10-07T20:21:15Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/918#issuecomment-3378577849
- Association: MEMBER

Refactoring the entire component may be very risky. As discussed today, we can aim for surgical operations to make the code more readable in different iterations.

The following block of code is a good candidate for being rewritten:

https://github.com/openwisp/openwisp-wifi-login-pages/blob/a2b63985bd79b5f002ab725ff82546cfbb0712dc/client/components/status/status.js#L219-L268

Here's the key questions I have for this block:

- Does actually getting & setting the mac address, filtering the open sessions by mac address give us any real advantage?
- Even if we keep the logic which makes the mac address available for filtering, why do we have to have 2 different branches doing mostly the same operations? I bet that we can get rid of that branching and execute the captive portal login if `mustLogin` is true, in the future we can add support for https://github.com/openwisp/openwisp-wifi-login-
... [truncated in archaeology summary; see raw JSON for full text]

### Ayush4958 on 2026-03-02T10:43:21Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/918#issuecomment-3983575750
- Association: NONE

Hi @pandafy @pandafy ,

I’ve been reviewing client/components/status/status.js and I agree that it currently handles multiple responsibilities (authentication flow, captive portal logic, session management, usage tracking, payment upgrade, and postMessage handling), which makes it difficult to reason about and maintain.

Considering the previous discussion about keeping the refactor “surgical” and minimizing risk, I wanted to clarify the preferred direction :-

- Should we keep the class component and incrementally extract logic into dedicated services.

I’d love to align on the approach before starting work
Share your insights and Initial though with me

### vikram-2101 on 2026-03-05T06:14:40Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/918#issuecomment-4002513383
- Association: NONE

Hi @nemesifier @pandafy ,

I've read the discussion carefully and studied status.js lines 219–268. Based on nemesifier's Oct 8 comments, I'd like to propose a  fix for the macaddr block:

Current problem:

Two branches (with/without macaddr) that both end up calling notifyCpLogin + loginFormRef.current.submit() — duplicated logic
getUserActiveRadiusSessions and getUserRadiusUsage are called in the macaddr branch AND again in finalOperations() — redundant API calls
Sync auth return path isn't clean — code after loginFormRef.current.submit() can still execute
Proposed refactor of lines 219–268:

<img width="876" height="528" alt="Image" src="https://github.com/user-attachments/assets/894ffca8-decc-43a9-aa45-e8ff5b309e2a" />

This eliminates the if (macaddr) / else branching, removes the duplicate getUserActiveRadiusSessions call in finalOperations(), and makes the sync auth early-exit expl
... [truncated in archaeology summary; see raw JSON for full text]


## Overlap with current PR activity

- PR #1056: [change] Refactored componentDidMount logic for better maintainability (OPEN, mergeState=BLOCKED)
  - URL: https://github.com/openwisp/openwisp-wifi-login-pages/pull/1056
  - Head: `change-status.js` -> Base: `master`
  - Files touched: 1
  - Checks: QA-Checks: SUCCESS, Tests and Coverage: FAILURE, review bot: SUCCESS

## Comparison seed

Maintainers explicitly want surgical iterations, not a full rewrite. Use the issue discussion and the open PR to define a narrowly provable slice before changing code.

## Local proof posture

- Start with archaeology and RCA before touching code.
- Keep the local proof branch independent from the overlapping PR unless comparison shows a clean extension path.
- Record exactly which parts of the issue remain open after comparing against active work.

## Next artifacts

- `issue-918-rca.md`
- `issue-918-fix-verification.md`
- `issue-918-comparison.md`
- `issue-918-complete-report.md`
