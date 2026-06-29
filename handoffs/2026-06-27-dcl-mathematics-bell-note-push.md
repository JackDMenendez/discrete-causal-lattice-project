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
  - "SERIALIZATION (updated 2026-06-28): dcl-mathematics local main is ahead 1 (commit 3ed082a, the Bell note, committed-unpushed) and has THREE uncommitted NOTE files for the PM to commit: (a) notes/dcl_mathematics_scope_and_outline.md (one-line roster edit), (b) notes/type_theoretic_foundations_directed_cubical.md (foundations note), (c) notes/manifesto_two_transcendentals.md (the A=1 + Observational Univariance manifesto). ALSO present: an untracked src/ — this is JACK'S ACTIVE AGDA WORK. Do NOT commit src/. Commit ONLY the three notes files, then push."
  - "Cross-subproject content: notes/bell_chsh_separability_on_lattice.md is the nonlocality backbone for Paper VI (dcl-paper-06-Bell-test), NOT Paper IV (dcl-mathematics' own paper). It is housed here as shared mathematics. Do not mistake it for Paper IV scope or wire it into paper/sections/."
  - "Internal-only until derived: the note makes a (conditional, open) Bell claim. Per the falsifiability-framing rule, nothing here goes public / onto the claim map until a result is derived. No push to any public-facing surface beyond the private dcl-mathematics origin."
decisions:
  - "The note (3ed082a) was committed directly by the focused session rather than serialized through the PM — accepted exception this time (user's call). The roster one-liner was deliberately left uncommitted so the PM performs the commit+push, keeping the serialization discipline for the remaining change."
consumed_by:
consumed_at:
---

## Summary
A batch of `dcl-mathematics/notes/` work is pending a commit+push by the PM:
(1) the Bell/CHSH separability note (committed as `3ed082a`, unpushed); plus
THREE UNCOMMITTED files — (2) a one-line roster entry in
`notes/dcl_mathematics_scope_and_outline.md`; (3) `notes/type_theoretic_foundations_directed_cubical.md`
(whether HoTT is the right math for the lattice; conclusion: directed+cubical+
univalent type theory as a *foundational layer*, non-blocking); and
(4) `notes/manifesto_two_transcendentals.md` (the program manifesto: A=1 as the
ontological transcendental and Observational Univariance as the epistemological
one, with a conjectured Noether-duality between them). The PM commits the three
uncommitted notes and pushes `dcl-mathematics`, observing cross-repo
serialization — and must NOT touch the untracked `src/`, Jack's active Agda work.

## Shipped
- `3ed082a` — `notes/bell_chsh_separability_on_lattice.md` (new, 275 lines):
  separable models (per-session A=1, shared classical variables, local random
  walks) are LHV-bounded at S≤2 (Fine's theorem covers the stochastic case);
  the violation requires a non-separable joint amplitude + joint collapse;
  adjacency-without-metric identified as where the joint object lives
  (ER=EPR-flavored; matches distance-independent entanglement); two edge
  conditions (non-separable amplitude + non-signalling); δp_min as the candidate
  entangling nonlinearity. **Committed locally, NOT pushed.**
- Uncommitted (PM to commit): `notes/dcl_mathematics_scope_and_outline.md`
  (one-line roster cross-ref), `notes/type_theoretic_foundations_directed_cubical.md`
  (foundations note), and `notes/manifesto_two_transcendentals.md` (the A=1 +
  Observational Univariance manifesto).
- Untracked, DO NOT COMMIT: `src/` — Jack's active Agda work.

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
- [ ] Repo `dcl-mathematics`: `git status` / `git diff` first. Pending notes:
      `notes/dcl_mathematics_scope_and_outline.md` (roster one-liner),
      `notes/type_theoretic_foundations_directed_cubical.md`, and
      `notes/manifesto_two_transcendentals.md`. Untracked `src/` is **Jack's
      active Agda work — leave it untracked, do NOT commit it.**
- [ ] Commit ONLY those three notes files (e.g. `notes: two-transcendentals
      manifesto + type-theory foundations + scope-outline cross-refs`). Confirm
      `src/` is not staged.
- [ ] Push `dcl-mathematics` `main` to origin (brings `3ed082a` + the new notes
      commit; was ahead 1, will be ahead 2 before push).
- [ ] Board (optional): no change required; the Bell work is already tracked by
      issue #21 (project 6). Mention the math backbone there only if useful.
- [ ] No public surface: do not push/derive any claim onto the claim map or any
      public-facing repo (falsifiability-framing rule).
