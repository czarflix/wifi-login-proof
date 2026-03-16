# Issue 947 notes

## Context

Issue `#947` is the RFC 8908 captive portal API track. The issue itself says it needs more discussion and is not suited for beginner contributors. That warning matches what I found when I read through it.

This is not a feature I wanted to sketch by guessing.

## What is already in progress upstream

There is no active PR in the current repo state, but there was an earlier attempt that was closed. The issue text already narrows the safe contract quite a lot:

- optional feature
- short timeout
- configurable URL
- documentation required

## What I concluded

I left this as an analysis-only track.

What seems safe so far:

- it should be opt-in
- it should not change current behavior when disabled or unreachable
- the timeout and fallback behavior need to be explicit
- the consuming flows need to be agreed before code is written

## Why I am not presenting this as implemented work

- the product contract is still the hard part here
- a code branch without that contract would look speculative
- for the proposal, this belongs in stretch scope unless mentors explicitly want it in the guaranteed set
