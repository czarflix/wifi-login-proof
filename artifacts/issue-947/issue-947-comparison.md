# issue-947 comparison report

Generated: 2026-03-16T15:59:18.695810+00:00

## Existing issue guidance

- The issue is marked as not suited for beginner contributors and explicitly says more discussion is required.
- The accepted constraints are already narrow:
  - optional feature
  - short configurable timeout
  - configurable URL per organization
  - documentation required

## Overlap with open PRs

- No active overlap PR is currently tracked in the matrix.
- The archaeology does show one earlier PR attempt was closed, which means prior implementation direction needs to be recovered from discussion before coding starts.

## Comparison against own PRs

- My existing PRs `#1061` and `#1062` do not overlap with captive-portal API support.
- This workstream is independent from current public WiFi PR evidence.

## Chosen direction

- Comparison-first and proof-bounded.
- Treat this as an opt-in prototype only after unresolved product assumptions are written down.
- If the design contract cannot be clarified from current discussion, the right output may be a comparison/report plus configuration sketch rather than code.

## Why this direction

- This is the most open-ended and mentor-dependent WiFi workstream.
- A bounded proof is useful only if it shows discipline around fallback behavior and configuration scope; otherwise it risks looking like speculative feature work.
