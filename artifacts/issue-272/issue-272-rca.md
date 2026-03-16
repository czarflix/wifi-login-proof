# issue-272 RCA

Generated: 2026-03-16T15:59:18.692031+00:00

## Observed problem

- `client/components/organization-wrapper/organization-wrapper.js` centralizes many route guards and redirect decisions inside render-time inline functions.
- The issue report and maintainer comments point to duplicate redirects and repeated requests when `setLoading()` triggers rerenders.
- In the current code, `setLoading` lives inside `OrganizationWrapper` and is exposed via context; `componentDidUpdate` toggles loading during language changes, which can force rerenders while route elements still contain inline `Navigate` decisions.
- Redirect-sensitive routes currently include:
  - registration (`organization-wrapper.js:153-172`)
  - mobile verification (`organization-wrapper.js:173-192`)
  - login (`organization-wrapper.js:218-229`)
  - status (`organization-wrapper.js:230-254`)
  - logout (`organization-wrapper.js:255-268`)
- Payment routes are also wired at the wrapper level (`organization-wrapper.js:299-313`), which increases the chance that external redirect logic is evaluated outside the owning component.

## Hypotheses

- Duplicate redirects are caused by redirect ownership living in a wrapper component that rerenders for unrelated reasons, including loading toggles and language/config updates.
- The highest-risk flows are those that can trigger external effects or repeated fetches, especially payment redirects and mobile verification.
- Moving redirect ownership into the concrete route components should make tests more local and reduce the chance of wrapper-level reevaluation causing duplicate navigation.

## Rejected hypotheses

- This does not look like a pure React Router bug; the maintainer discussion and current wrapper design both point to route ownership as the architectural problem.
- The issue is not limited to one path such as payment only; the wrapper contains several inline route conditions that duplicate auth/verification decisions.

## Root cause

- `OrganizationWrapper` currently mixes:
  - organization/config loading
  - translation loading
  - loading state ownership
  - route declarations
  - auth/verification redirect policy
- Because redirect policy is encoded inside inline route elements in `render()`, any rerender of the wrapper can reevaluate those navigation decisions.
- That makes the redirect behavior hard to reason about, hard to unit test in isolation, and risky for external-effect flows such as payment or verification.

## Fix-shaping constraints

- Keep the proof branch surgical: start with one or two high-value redirect flows, not a full routing rewrite.
- Preserve user-visible behavior for:
  - unauthenticated access
  - mobile verification enforcement
  - status access
  - logout auto-login path
  - payment/process and payment/status routes
- Add focused regression tests for any flow moved out of the wrapper so duplicate redirects or duplicate requests can be demonstrated, not just inferred.
- Compare the local proof direction against the existing discussion from `vikram-2101` before widening scope.
