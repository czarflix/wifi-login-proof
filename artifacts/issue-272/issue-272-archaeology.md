# issue-272 archaeology

Generated: 2026-03-16T16:05:26.596681+00:00

## Issue identity
- Repo: `openwisp/openwisp-wifi-login-pages`
- Issue: #272 - [change] Move redirect logic from OrganizationWrapper to each component
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/272
- State: OPEN
- Author: nemesifier
- Labels: enhancement
- Assignees: None

## Issue statement

I suspected that it was wrong to define the redirection logic in `OrganizationWrapper` but now I think I had the confirmation.
Basically the organization wrapper files decides if the user should be redirected to verification or not and so on.
But that component is re-rendered everytime `setLoading()` is called.

I found out while working on #170 because I need to redirect the user to the credit card verification which is an external link, and in the automated tests I found out the redirection was called twice.

In reality I found out that multiple HTTP requests were being made to the payment URL, which would have very bad consequences in production because it would initiate multiple payments to the payment gateway.

I think we will have to change this part and move most of that logic in each individual component, this also makes it easier to test it.

Making OrganizationWrapper leaner should also have a beneficial effect on rendering performance because less logic will be executed each time `setLoading()` is called.

@codesankalp what do you think about this? Do you agree? Or is the current way of doing things right?
We can work on this if there's still time as last thing.

## Maintainer and discussion highlights

### codesankalp on 2021-06-16T13:47:34Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/272#issuecomment-862395653
- Association: MEMBER

I agree with this, redirection must be handled from the component so that routes defined in the organization wrapper will be more cleaner. Because currently, we check for some conditions and then redirect.
I also face multiple redirections when doing mobile verification, which can also be solved using this.
- I will also implement proper routings such as AuthRoute and simple Route which will make it better.

I will start working on this.

### vikram-2101 on 2026-03-05T06:16:41Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/272#issuecomment-4002523311
- Association: NONE

Hi @nemesifier ,

I've been studying this issue and the OrganizationWrapper source. I can see the redirect logic in organization-wrapper/index.js triggers on every setLoading() call, which is the root of the multiple-redirect bug you described.

I'd like to propose and implement moving these redirects:

- Verification redirect → into mobile-phone-verification and password-confirm components
- Payment/credit card redirect → into payment-process and registration components
- General auth redirect → into status component's componentDidMount

Each moved redirect would also get its own test. Is this the right direction? If so, I can open a draft PR showing the move for one component first so you can validate the approach before I do all of them.

### czarflix on 2026-03-16T00:50:12Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/272#issuecomment-4064364627
- Association: NONE

Hi @nemesifier,

I rechecked this issue and confirmed that the main problem is redirect ownership in `OrganizationWrapper`: those route redirects are re-evaluated whenever `setLoading()` causes a rerender, which can trigger duplicate redirects. I also confirmed the external payment flow needs a one-time guard to avoid repeated payment redirects. I’m working on a PR that moves the affected redirects into their route components and adds focused regression tests.


## Overlap with current PR activity

- No active overlap PR was configured for this workstream in the current scaffold.

## Comparison seed

Current issue discussion already points toward moving redirects into owning components. Compare any local implementation against the proposals already discussed on the issue before widening scope.

## Local proof posture

- Start with archaeology and RCA before touching code.
- Keep the local proof branch independent from the overlapping PR unless comparison shows a clean extension path.
- Record exactly which parts of the issue remain open after comparing against active work.

## Next artifacts

- `issue-272-rca.md`
- `issue-272-fix-verification.md`
- `issue-272-comparison.md`
- `issue-272-complete-report.md`
