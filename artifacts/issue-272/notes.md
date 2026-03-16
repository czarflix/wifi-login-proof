# Issue 272 notes

## Context

Issue `#272` is about moving redirect ownership out of `OrganizationWrapper`. The issue discussion already pointed in that direction, and there was no active PR covering it when I started this slice.

I started with the registration path because it is small enough to check properly and risky enough to matter. It also gave me a clean way to prove the direction before touching broader wrapper logic.

## What I changed

I made `Registration` own the authenticated redirect instead of leaving that decision in `OrganizationWrapper`.

That meant:

- `registration/*` now always renders the registration component
- the redirect to `status` or mobile verification happens inside `Registration`
- the branch now also handles the case where the user becomes authenticated after submitting the form, not only the mount-time case

I kept the slice narrow on purpose. I did not try to move every redirect out of the wrapper in one branch.

## How I checked it

I checked the change with:

- `registration.test.js`
- `organization-wrapper.test.js`
- `browser-test/registration.test.js`
- `./run-qa-checks`

During the integration pass I found a real gap: registration succeeded, the user became authenticated, but the page stayed on the registration route. I fixed that by handling the post-submit auth transition in `Registration`, then reran the unit and browser checks.

## Open notes

- This is a first slice, not the whole issue.
- The point of the branch is to show the ownership pattern on one route and validate it properly.
- If I turn this into a public PR later, I would present it as the first redirect move, not as the full `#272` solution.
