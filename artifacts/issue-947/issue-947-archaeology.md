# issue-947 archaeology

Generated: 2026-03-16T16:05:26.597763+00:00

## Issue identity
- Repo: `openwisp/openwisp-wifi-login-pages`
- Issue: #947 - [feature] Add support for captive-portal API
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/947
- State: OPEN
- Author: nemesifier
- Labels: enhancement
- Assignees: None

## Issue statement

⚠️ **Warning**: not suited for beginner contributors. Requires more discussion.

Modern captive portals have [RFC 8908 Captive Portal API](https://www.rfc-editor.org/rfc/rfc8908.html).

A few useful ways we could use this API right now:

- Check if captive portal login is required.
- Check if we are in "internet-mode".

Constraints:

- The timeout should be short, eg: 2 seconds, but configurable, to avoid waiting for a long time in case something goes wrong.
- It shouldn't be required.
- The URL should be configurable per org.
- It should be documented.

## Maintainer and discussion highlights

### saurabh24thakur on 2025-12-31T02:42:37Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/947#issuecomment-3701299742
- Association: NONE

@nemesifier I have raise PR for that issue.

### nemesifier on 2025-12-31T08:30:14Z
- URL: https://github.com/openwisp/openwisp-wifi-login-pages/issues/947#issuecomment-3701728083
- Association: MEMBER

@saurabh24thakur your PR is closed.


## Overlap with current PR activity

- No active overlap PR was configured for this workstream in the current scaffold.

## Comparison seed

The issue is explicitly marked as not suited for beginners and calls for more discussion. Keep the proof branch opt-in and bounded, and document any unresolved product questions before implementation.

## Local proof posture

- Start with archaeology and RCA before touching code.
- Keep the local proof branch independent from the overlapping PR unless comparison shows a clean extension path.
- Record exactly which parts of the issue remain open after comparing against active work.

## Next artifacts

- `issue-947-rca.md`
- `issue-947-fix-verification.md`
- `issue-947-comparison.md`
- `issue-947-complete-report.md`
