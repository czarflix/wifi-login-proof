# issue-314 RCA

Generated: 2026-03-16T15:59:18.693152+00:00

## Observed problem

- `client/components/header/header.js` currently renders two largely parallel structures:
  - desktop branch (`header.js:81-167`)
  - mobile branch (`header.js:168-263`)
- Both branches duplicate:
  - logo handling
  - second logo handling
  - link mapping logic
  - active-link calculation
  - language button rendering
- CSS already contains separate desktop/mobile selectors in `client/components/header/index.css`, which suggests presentation differences can largely stay in CSS even if markup is unified.

## Hypotheses

- The core maintainability problem is duplicated structure, not missing styling primitives.
- The highest-value refactor is to unify shared markup and keep mobile-only behavior limited to hamburger/menu state and responsive CSS.
- If link rendering and language rendering are extracted or normalized, the header can stay behaviorally identical while cutting customization burden.

## Rejected hypotheses

- This issue does not require a visual redesign; the maintainer request is specifically to remove redundant HTML.
- A full header rewrite is unnecessary; the existing link/auth logic is already shared conceptually and can be preserved.

## Root cause

- The component evolved into two separate render branches for desktop and mobile instead of one responsive structure.
- Shared behavior is copied rather than abstracted, so any customization or bug fix risks diverging between desktop and mobile paths.
- The duplicated branching also increases test surface because the same logic is asserted through two different markup trees.

## Fix-shaping constraints

- Preserve:
  - authenticated vs unauthenticated link visibility
  - internal vs external link handling
  - language switcher behavior
  - sticky message behavior
  - hamburger interaction for smaller screens
- Keep the proof branch comparison-first because PR `#1048` already touches this exact area.
- If the local proof proceeds, it should stay narrow enough that screenshot comparison and header tests can show parity across desktop and mobile states.
