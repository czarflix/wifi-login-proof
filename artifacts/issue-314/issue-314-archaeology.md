# issue-314 archaeology

Generated: 2026-03-16T16:05:26.597087+00:00

## Issue identity
- Repo: `openwisp/openwisp-wifi-login-pages`
- Issue: #314 - [change] Eliminate redundancy of header HTML
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/314
- State: OPEN
- Author: nemesifier
- Labels: enhancement
- Assignees: None

## Issue statement

The header HTML is kind of duplicated, once is a desktop version and one is a mobile version.

I wonder if we can avoid this and handle everything with CSS.

It's kind of painful to customize this part because of this duplication (double amount of work).

## Maintainer and discussion highlights

### Red-0111 on 2021-07-28T10:42:46Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/314#issuecomment-888208448
- Association: NONE

Hi, I would like to work on this issue, please tell me how to proceed :)

### codesankalp on 2021-07-28T15:48:49Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/314#issuecomment-888419849
- Association: MEMBER

Hi @Red-0111, Please check `client/components/header/`.
In this headers are defined for mobile and desktop separately.
**mobile**:
https://github.com/openwisp/openwisp-wifi-login-pages/blob/f2af7f1940aa6f41d2b2d2b35567c016382396b2/client/components/header/header.js#L145-L148
**desktop**:
https://github.com/openwisp/openwisp-wifi-login-pages/blob/f2af7f1940aa6f41d2b2d2b35567c016382396b2/client/components/header/header.js#L59-L62

In this issue, it is mentioned to get rid of one header using CSS.

### codesankalp on 2021-08-12T16:06:47Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/314#issuecomment-897764673
- Association: MEMBER

Hello @Red-0111, Are you working on this?

### Red-0111 on 2021-08-12T16:08:13Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/314#issuecomment-897765722
- Association: NONE

Yes please give me some time I am trying to figure it out.

### codesankalp on 2021-08-12T16:30:15Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/314#issuecomment-897786778
- Association: MEMBER

> Yes please give me some time I am trying to figure it out.

Great, If you need any help feel free to ask :+1:

### totallynotvaishnav on 2021-08-24T09:40:23Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/314#issuecomment-904487574
- Association: CONTRIBUTOR

Is anyone working on this?

### Red-0111 on 2021-08-24T10:10:49Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/314#issuecomment-904508619
- Association: NONE

> Is anyone working on this?

Yes, it would be great to have some help :)

### codesankalp on 2021-08-24T11:27:36Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/314#issuecomment-904555949
- Association: MEMBER

> > Is anyone working on this?
>
> Yes, it would be great to have some help :)

What issues are you facing @Red-0111?


## Overlap with current PR activity

- PR #1048: Issues/314 enhanchment title unify header (OPEN, mergeState=DIRTY)
  - URL: https://github.com/openwisp/openwisp-wifi-login-pages/pull/1048
  - Head: `issues/314-enhanchment-title-unify-header` -> Base: `master`
  - Files touched: 8
  - Checks: QA-Checks: SUCCESS, Tests and Coverage: FAILURE, review bot: SUCCESS

## Comparison seed

An active PR already targets this issue. Default posture is comparison-first, then narrower-slice or extension only if upstream work leaves clear gaps.

## Local proof posture

- Start with archaeology and RCA before touching code.
- Keep the local proof branch independent from the overlapping PR unless comparison shows a clean extension path.
- Record exactly which parts of the issue remain open after comparing against active work.

## Next artifacts

- `issue-314-rca.md`
- `issue-314-fix-verification.md`
- `issue-314-comparison.md`
- `issue-314-complete-report.md`
