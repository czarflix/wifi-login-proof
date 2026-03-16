# Issue 314 notes

## Context

Issue `#314` asks for the duplicated desktop and mobile header markup to be replaced with one structure handled by CSS. There is already an open PR in this area, so I kept this branch narrow and used it as a cleaner local pass on the same problem.

I kept this branch focused on the duplicated header HTML itself. I did not use it to mix in unrelated cleanup.

## What I changed

I replaced the two parallel header render trees with one responsive structure.

The branch keeps:

- one branding block
- one navigation block
- one language button group
- the existing hamburger/menu behavior

I also updated the browser language-change selector so it matches the unified header buttons.

## How I checked it

I checked the branch with:

- `header.test.js`
- changed-file lint
- `./run-qa-checks`

I also used the later integration browser run as an extra sanity check for header behavior through the language-change flow.

## Open notes

- This is in the same direction as PR `#1048`, but the branch is narrower.
- I did not try to redesign the header.
- If the upstream PR lands cleanly, this branch becomes background context, not something I would insist on opening as a competing PR.
