---
handoff: 2026-06-27-dcl-mathematics-bell-note-push
from: dcl-mathematics (focused)
to: PM
repo: dcl-mathematics
branch: main
commits: [3ed082a]                  # the note (committed locally, UNPUSHED); one-liner still uncommitted
pr: none
status: open
state: complete
semver: n/a (notes only; no software change)
flags:
  - "SERIALIZATION: dcl-mathematics local main is ahead of origin and has an uncommitted edit. State: commit 3ed082a (the Bell note) is committed but NOT pushed (ahead 1); notes/dcl_mathematics_scope_and_outline.md has a one-line roster edit left UNCOMMITTED on purpose for the PM to commit. Before committing/pushing, confirm no parallel session is mid-edit in dcl-mathematics (cross-repo serialization)."
  - "Cross-subproject content: notes/bell_chsh_separability_on_lattice.md is the nonlocality backbone for Paper VI (dcl-paper-06-Bell-test), NOT Paper IV (dcl-mathematics' own paper). It is housed here as shared mathematics. Do not mistake it for Paper IV scope or wire it into paper/sections/."
  - "Internal-only until derived: the note makes a (conditional, open) Bell claim. Per the falsifiability-framing rule, nothing here goes public / onto the claim map until a result is derived. No push to any public-facing surface beyond the private dcl-mathematics origin."
decisions:
  - "The note (3ed082a) was committed directly by the focused session rather than serialized through the PM — accepted exception this time (user's call). The roster one-liner was deliberately left uncommitted so the PM performs the commit+push, keeping the serialization discipline for the remaining change."
consumed_by:
consumed_at:
---

## Summary
A formal mathematical note settling "can the A=1 lattice violate Bell/CHSH, and
through what structure" was written in `dcl-mathematics/notes/` as the backbone
for Paper VI (`dcl-paper-06-Bell-test`). The note is committed locally but
unpushed; a one-line roster entry pointing to it was added to the scope/outline
note and left uncommitted. The PM is asked to commit the one-liner and push
`dcl-mathematics` to origin, observing cross-repo serialization.

## Shipped
- `3ed082a` — `notes/bell_chsh_separability_on_lattice.md` (new, 275 lines):
  separable models (per-session A=1, shared classical variables, local random
  walks) are LHV-bounded at S≤2 (Fine's theorem covers the stochastic case);
  the violation requires a non-separable joint amplitude + joint collapse;
  adjacency-without-metric identified as where the joint object lives
  (ER=EPR-flavored; matches distance-independent entanglement); two edge
  conditions (non-separable amplitude + non-signalling); δp_min as the candidate
  entangling nonlinearity. **Committed locally, NOT pushed.**
- Uncommitted: `notes/dcl_mathematics_scope_and_outline.md` — one bullet under
  Pointers cross-referencing the new note as the Paper VI backbone.

## Verification
N/A (prose/math notes; no tests). `git status`: branch `main` ahead of
`origin/main` by 1 (the note commit), plus one modified file (the roster
one-liner) staged/unstaged for the PM to commit.

## Remaining
PM commits the one-liner and pushes `dcl-mathematics` main to origin (after the
commit it will be ahead 2 → push brings origin current). Nothing else gates it.

## Decisions & flags
See frontmatter. Load-bearing: (1) serialization — there is an unpushed commit
*and* an uncommitted edit; commit the one-liner only (diff-first, do not bundle
any parallel WIP) then push; (2) the note is Paper VI content parked in the
dcl-mathematics notes dir, not Paper IV; (3) internal-only until a result is
derived.

## → Consumer actions
- [ ] Repo `dcl-mathematics`: `git status` / `git diff` first; confirm the only
      pending change is `notes/dcl_mathematics_scope_and_outline.md` (the roster
      one-liner) and that no parallel session is mid-edit.
- [ ] Commit that one file (e.g. `notes: cross-ref Bell separability note from
      the scope/outline roster`).
- [ ] Push `dcl-mathematics` `main` to origin (brings `3ed082a` + the one-liner
      commit to origin; was ahead 1, will be ahead 2 before push).
- [ ] Board (optional): no change required; the Bell work is already tracked by
      issue #21 (project 6). Mention the math backbone there only if useful.
- [ ] No public surface: do not push/derive any claim onto the claim map or any
      public-facing repo (falsifiability-framing rule).
