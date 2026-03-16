# public-branch-map

Use these names when pushing proof branches publicly from the local worktree. The private local branch names can stay unchanged.

## Public branch names

- React follow-up comparison track -> `proof-react19-followup`
- `#272` redirect slice -> `proof-272-registration-redirect`
- `#314` header slice -> `proof-314-header-unification`
- `#918` status slice -> `proof-918-status-surgical-slice`
- RFC 8908 comparison track -> `proof-947-rfc8908-prototype`
- stacked smoke proof -> `proof-integration-smoke`

## Push rule

- Do not rename the private local branch if you do not want to.
- Push each local branch to the matching public branch name on the remote instead.
- This keeps the private workflow intact while ensuring the public branch names are clean.
