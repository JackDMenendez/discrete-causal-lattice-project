---
handoff: 2026-07-16-dcl-mathematics-lean-formalism-and-dpmin-gate
from: dcl-mathematics (focused)
to: PM
repo: dcl-mathematics
branch: main
commits: [1926264, 7ea4410, 051adeb, 41ab08f]
pr: none
status: consumed
state: in-progress
semver: n/a (paper repo; the new src/dcl_formalism Lake project is 0.1.0, unreleased)
flags:
  - "GATE: δp_min = 1/4 derived-or-fitted is UNRESOLVED. The whole dimensional-selection novelty claim (d_max = 1/δp_min − 1) is CIRCULAR if δp_min is reverse-engineered to yield d=3. Must be answered in dcl-delta-p-min before Paper IV Section 9 publishes the claim."
  - "Novelty verdict is NEGATIVE evidence (absence across surveyed reviews), not exhaustive — the holographic / entropy-bound literature was NOT fully swept and is the likeliest place a closer precedent hides."
  - "wcde commit 7b4c15a is committed LOCALLY and NOT pushed."
  - "Scope change: dcl-mathematics is now paper + Lean formalisation (was paper-only). Lean/Mathlib supersedes the planned sympy dcl-formalism package; CLAUDE.md updated."
decisions:
  - "Formalism layer = Lean 4 + Mathlib, co-located in src/dcl_formalism/ (not a separate sympy dcl-formalism repo)."
  - "The d-of-(d+1) offset set and projection are carried as DATA (Orientation / Geometry), not pinned — the open modelling choice stays open."
  - "Dimensional-selection slot count = the d+1 simplex AXES (resolves Open Question 4 on the d+1 side; the 2d+1 topology is the closed-neighbourhood size, not a slot count)."
consumed_by: PM (dcl-website session)
consumed_at: 2026-07-16
---

## Summary
The dcl-mathematics session stood up a machine-checked Lean 4 + Mathlib
formalisation in-repo, added a leanblueprint that verifiably links the paper's
theorems to their Lean declarations, developed the per-node
topology/adjacency/orientation structure (with a new global-gauge-vs-gauge-field
research thread), and ran an adversarially-verified deep-research literature
sweep on novelty. The sweep's headline: the *geometry* and *dimension-from-
adjacency* are well-trodden, but the **δp_min dimensional-selection mechanism
appears genuinely novel** — CONDITIONAL on δp_min being derived, not fitted.
That condition is the load-bearing gate this handoff exists to route to
`dcl-delta-p-min`.

## Shipped
- `1926264` — Lean 4 + Mathlib (v4.32.0) Lake project at `src/dcl_formalism/`.
  Geometry-agnostic base `DclFormalism.Lattice`: `Site = ℤ^d`, parity
  bipartition, `Geometry` = arbitrary finite offset set (coordination NOT fixed
  to 2d); general lemmas `coordination_eq_card`, `neighbour_parity`.
  Specialisation `Lattice.DiamondProgression`: the 2d / √d / (d+1)^((d−1)/2)
  targets + `IsDiamondProgression`.
- `7ea4410` — `Geometry.topology` (closed neighbourhood, `topology_card = 2d+1`)
  and `Orientation` (axes V₁..V_d → offsets {±Vᵢ}); notes: local
  topology/adjacency/orientation, three-count disambiguation table, "axes =
  slots", global-gauge-vs-gauge-field progression fork, Open Questions 1 & 4
  resolved.
- `051adeb` — leanblueprint scaffold (`src/dcl_formalism/blueprint/`) linking 8
  results to Lean decls; `checkdecls` machine-verifies the links.
- `41ab08f` — `notes/prior_work_dimension_from_adjacency.md`: the deep-research
  verdict with verified citations.
- (separate repo) `wcde` `7b4c15a` — `lean` profile now puts python (.venv-win)
  + graphviz on PATH; new `graphviz-env.cmd`. **Local only, not pushed.**

## Verification
- `lake build` green across all modules (base + specialisation + topology +
  Orientation); Mathlib smoke test passes.
- `checkdecls`: all 8 blueprint Lean names resolve (exit 0); negative control
  (a bogus name) correctly fails (exit 1) — the link check genuinely bites.
- deep-research: 5 angles, 21 sources, 75 claims → 25 adversarially verified
  (2-of-3-refute), 23 confirmed, 2 refuted. Verdict captured with citations.

## Remaining
- Phase 2: prove the three result-density theorems in `src/dcl_formalism/`
  (each blueprint `\notready` flips to `\leanok` and joins `blueprint/lean_decls`
  when proved).
- The δp_min gate (below) must clear before the selection-novelty claim can be
  written into the paper.

## Decisions & flags
- **δp_min derived-or-fitted GATE (critical).** The deep-research sweep found no
  prior work deriving `d_max = 1/δp_min − 1` or tying dimension to a minimum
  probability quantum / per-node slot / coordination bound — so the mechanism
  looks new. But the novelty (and the physics) collapses to a tautology if
  δp_min = 1/4 was chosen to make d_max = 3. **Refuted/confirmed by:** whether
  `dcl-delta-p-min` pins δp_min *independently* (empirically / from first
  principles) rather than back-solving it.
- **Novelty rests on negative evidence.** Absence across surveyed reviews is
  never exhaustive. Confirm/tighten by sweeping the holographic / entropy-bound
  literature (information-per-site counts) — the one adjacent area not covered.
- **wcde 7b4c15a not pushed** — decide whether to push the wcde infra repo.
- **Scope change recorded in CLAUDE.md** — Lean formalism now lives in
  dcl-mathematics; the sympy `dcl-formalism` plan is superseded for the
  theorem-checking role.

## → Consumer actions
- [ ] **GATE (route onward):** hand the question *"is δp_min = 1/4 derived or
      fitted?"* to the `dcl-delta-p-min` session/repo. Do NOT allow Paper IV's
      dimensional-selection section to publish its novelty claim until
      `dcl-delta-p-min` confirms δp_min is pinned independently. If fitted,
      `d_max = 1/δp_min − 1` is circular.
- [ ] Board: open an issue in `discrete-causal-lattice-project` (project 6):
      *"dcl-delta-p-min: is δp_min = 1/4 derived or fitted? (blocks Paper IV §9
      dimensional-selection novelty)"* — link this handoff.
- [ ] Board: open a Paper IV related-work follow-up issue: *"sweep holographic /
      entropy-bound literature for a per-node information/probability-slot
      dimension argument (closest possible precedent to δp_min selection)."*
- [ ] Board: open a Paper IV geometry follow-up issue: *"find prior art naming
      the full both-coset parity bipartition (D_d is only the even coset;
      Λ_d uses both)."*
- [ ] Memory: record the δp_min derived-vs-fitted gate as a `project` memory in
      the PM's memory dir, cross-linked to `dcl-delta-p-min`.
- [ ] Decide: push wcde commit `7b4c15a` (local-only) — the `lean` profile
      PATH fix (python + graphviz) and `graphviz-env.cmd`.
- [ ] Awareness: dcl-mathematics is now paper + Lean formalism; Phase 2 is
      proving the three theorems in `src/dcl_formalism/` (blueprint tracks
      coverage via `\leanok` + `checkdecls`).
