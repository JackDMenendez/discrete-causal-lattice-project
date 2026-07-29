---
handoff: 2026-07-29-dpmin-geometric-fitted-branch-input
from: PM (dcl-website session)
to: dcl-delta-p-min (focused)
repo: JackDMenendez/dcl-delta-p-min
branch: main
commits: []
pr: none
status: open
state: ready
semver: n/a (research input to the open derive-or-fit gate)
flags:
  - "This is NEW evidence for the FITTED branch of the open δp_min derive-or-fit gate (2026-07-16-dpmin-derived-or-fitted-gate, board #24 / internal 022). It does not close the gate by itself — it is one branch's supporting argument, sourced from the geometry side."
decisions:
  - "Routed, not adjudicated. The gate (is δp_min = 1/4 derived or fitted?) is dcl-delta-p-min's to resolve."
consumed_by:
consumed_at:
---

## Summary

Routing a geometry-side finding that bears directly on the open **δp_min
derive-or-fit gate**. Source: `dcl-mathematics` successor-geometries note §6
(the simplex face lattice thread), relayed via
`2026-07-30-dcl-data-shared-repo-proposal.md`.

## The finding — a geometric quarter is the FITTED branch

If the facet index is selected with **equal weight over the d+1 facets** of the
simplex face lattice, then by construction

- δp_min = 1/(d+1), and therefore
- 1/δp_min − 1 = d **identically** — true for **every** d.

Because it holds for every dimension d, this construction **selects nothing**:
it cannot be doing the dimensional-selection work that Paper IV §9 needs. That
is precisely the signature of the gate's **fitted** branch — the quarter falls
out of an equal-weight convention rather than being *derived* by a constraint
that singles out a dimension.

## Why it matters to the gate

The δp_min gate is CRITICAL because Paper IV §9's dimensional-selection novelty
is **circular if δp_min = 1/4 is fitted**. This geometry-side result is
independent evidence that at least one natural construction of the quarter is
fitted (equal-weight facet selection). The gate should weigh it against any
candidate *derivation* that breaks the every-d degeneracy.

## → Consumer actions

- [ ] Fold this into the open δp_min derive-or-fit analysis as the geometry-side
      argument for the FITTED branch (equal-weight facet selection ⇒ δp_min =
      1/(d+1), degenerate in d ⇒ selects nothing).
- [ ] If a *derivation* is proposed, check whether it breaks the every-d
      degeneracy (i.e. does something other than equal-weight facet averaging).
- [ ] Cross-reference `dcl-mathematics/notes/successor_geometries_simplex_face_lattice.md`
      §6 for the full construction.
