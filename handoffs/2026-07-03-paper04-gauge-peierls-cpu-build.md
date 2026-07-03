---
handoff: 2026-07-03-paper04-gauge-peierls-cpu-build
from: dcl-core (focused)
to: PM
repo: JackDMenendez/dcl-core
branch: main
commits: [UNCOMMITTED-WORKING-TREE]   # not yet committed; see flags + Consumer actions
pr: none
status: open
state: in-progress          # CPU-first slice complete but uncommitted; GPU + release remain
semver: 0.2.2 -> 0.3.0 (MINOR, unreleased, NOT yet bumped in files)
flags:
  - "Work is UNCOMMITTED in dcl-core's working tree (branch main) — no SHA exists. Must be committed (ideally on a feature branch) before anything downstream pins it."
  - "Version files deliberately NOT bumped (still 0.2.2); the 0.3.0 bump + Zenodo DOI + release_notes/v0.3.0.md are the gated release step, owner-only."
  - "Ward-identity test (#2) is a BULK, float-tolerance check — NOT the bit-exact 'token densities invariant tick-for-tick' the doc phrases. Deliberate: a linear gauge Lambda=g.x is not single-valued on the periodic torus, and a rotated complex's magnitude is not ULP-invariant. Interior (margin-1) covariance is exact to 1e-12."
  - "Peierls mid-point re-indexed to the actual shift direction: doc R2 writes A_mid=1/2(A(x)+A(x+v)) for a +v hop; code uses A_mid=1/2(A(x)+A(x-v)) because backend.shift brings amplitude x-v -> x. Same rule, correct index for the engine's convention; verified by the Ward test."
  - "Exact Q-tensor magnitude {4,4,16} is an xfail (deferred to exp_03 / doc test #5, N-limited/GPU-bound). Single-hop CPU probe gives axial/planar ~= 2.06, NOT 4 — uniaxial SYMMETRY about (1,1,-1) is confirmed (perp-plane degenerate to 0.3%), magnitude is not."
  - "dcl-core working tree also carries a PRE-EXISTING, not-mine wording edit to docs/design/04 ('isotropy result' -> 'birefringence-order result'). Whoever commits should treat it separately from the gauge-code change."
  - "CuPy setup fork-bombs this shared machine if installed wrong (MinGW/UCRT64 source build) — do NOT `pip install -e .[gpu]` there. Use stock CPython + cupy-cuda12x wheel (.venv-gpu). GPU is the owner's env project."
decisions:
  - "R4 readout = experiment-side default (susceptibility estimator = symmetric second difference rho(+B)+rho(-B)-2rho(0), lives in tests), NOT an in-engine chi() API. This resolves the doc's open definitional choice (R4) toward the lightweight option; confirm."
  - "Electric sector delivered via the EXISTING external_potential (temporal A_0 -> E = -grad A_0), not a new argument. Magnetic via new vector_potential (spatial A -> B). Both threaded through TickScheduler as optional fields."
consumed_by:
consumed_at:
---

## Summary
CPU-first implementation of the v0.3.0 U(1) Peierls gauge coupling in
`dcl_core.core3d`, per `docs/design/04_gauge_field_and_vacuum_response.md`
(R1–R4 + acceptance tests #1–#4, #6). This is the engine capability Paper IV
(`dcl-paper-04-optical-axis-birefringence`) `exp_03` needs to measure the
induced photon-response order in the gauge sector. The build is complete,
green (270 passed / 27 xfail, zero regressions), and reviewed clean — but
**uncommitted** and intentionally **not released**. It unblocks the
CPU-scale `exp_03` scaffold and the eventual v0.3.0 cut; the birefringence
**order verdict itself** stays gated on GPU/large-N (doc test #5).

## Shipped (working-tree changes — NOT yet committed)
- `src/dcl_core/core3d/hop.py` — R1: `vector_potential` kwarg on `HopOperator.step`; R2: Peierls link phase `exp(i·A_mid·v)` (mid-point) in `_hop_average`; new `_link_phase` helper. `None` ⇒ pre-v0.3.0 hop bit-for-bit.
- `src/dcl_core/core3d/gauge.py` (NEW) — R3: `uniform_B_potential(shape, B_vec, origin=None)`, symmetric gauge `A=½B×(r−origin)`, any orientation.
- `src/dcl_core/core3d/scheduler.py` — new optional `external_potential` (A₀/electric) + `vector_potential` (A/magnetic) fields threaded into every session's hop. None/None ⇒ unchanged.
- `src/dcl_core/core3d/__init__.py` — re-export `uniform_B_potential`.
- `tests/test_peierls.py` (NEW) — acceptance tests #1 (zero-field regression, bitwise), #2 (bulk Ward identity), #3 (quadratic B→0), #4 (uniaxial about (1,1,-1)) + xfail for exact {4,4,16}, #6 (A=1 exact under E+B), plus `uniform_B_potential` curl check + shape guards.
- `docs/reference/api.md` — gauge-coupling section + re-export row.

## Verification
- **Suite:** 270 passed, 1 skipped, 27 xfailed (baseline v0.2.2 was 257/1/26; +13 new Peierls passes, +1 documented xfail). Zero failures, zero regressions. Run with `.venv-gpu` CPython 3.13 (CPU backend only).
- **api-stability-reviewer:** all 5 changes additive → MINOR (0.3.0). No removals/renames/breaking signatures; top-level `dcl_core` surface unchanged. Flagged version-not-bumped (expected — release-gated).
- **physics-naming-reviewer:** clean; one Low finding (inline `# physics:` comment on `A=½B×r`) — **fixed**.
- **Physics sanity:** induced magnetic response uniaxial about (1,1,-1): χ_axis=3.88 vs χ_perp≈1.88 (perp-plane degenerate to 0.3%). Matches doc §1.1 (O_h not restored; lattice is uniaxial).

## Remaining
- **Commit** the working tree (gate for everything below).
- **GPU RawKernel Peierls path** (R2-GPU / R5) — still a stub in `backends/gpu.py`; owner's env project.
- **Doc test #5** — the birefringence-**order** verdict (O(1) dim-4 vs (ka)²-suppressed vs null) and exact {4,4,16}; N-limited/GPU-bound.
- **`exp_03` experiment** (orientation sweep computing χ(n̂)) — CPU scaffold offered, not yet built.
- **Release cut** — bump `_version.py`+`CITATION.cff` to 0.3.0, `release_notes/v0.3.0.md`, Zenodo DOI, then bump Paper IV's `dcl_core` pin.

## Decisions & flags
See frontmatter `flags` (all load-bearing) and `decisions`. The two most
likely to bite a careless reader:
1. **Ward test is bulk/float-tolerance, by necessity** — not the doc's literal
   "invariant tick-for-tick" bit-exactness. The bit-exact reading is
   physically impossible across a gauge rotation on a torus (non-single-valued
   linear gauge + IEEE magnitude non-invariance). The engine's A=1 integer
   exactness is preserved and separately tested (#6).
2. **{4,4,16} magnitude is NOT reproduced by the CPU probe (ratio ~2.06, not 4)** —
   only the uniaxial symmetry is. This is expected and xfail-documented; the
   magnitude is the `exp_03`/test-#5 physics result, not a wiring check. Do not
   read the passing #4 as "Q-tensor confirmed."

## → Consumer actions
- [ ] **Commit gate:** ensure the dcl-core working-tree gauge changes get committed (prefer a `feature/v0.3.0-peierls` branch, not bare `main`). Keep the pre-existing `docs/design/04` wording edit as a separate concern — it is not part of this gauge-code change.
- [ ] **Board:** on project 6, locate the Paper IV / v0.3.0 gauge-sector (`exp_03`) issue (the successor to issue 007's core3d roadmap; open one if absent) and mark: R1–R3 + R4-default + tests #1–4,#6 landed (CPU-first, uncommitted); R2-GPU/R5, test #5, and release deferred.
- [ ] **Memory:** record in the consuming session's memory that dcl-core v0.3.0 Peierls gauge coupling is CPU-complete-but-uncommitted on the working tree, release-gated, with R4 resolved to the experiment-side estimator. Cross-link the existing CuPy fork-bomb hazard note.
- [ ] **Gate — do NOT release:** do not tag/deposit v0.3.0 or bump Paper IV's `dcl_core` pin to `@v0.3.0` until the work is committed AND (GPU decision made OR explicitly scoped out) AND version bump + Zenodo done, in that order (per dcl-core release flow).
- [ ] **Gate — do NOT read #4 as the physics verdict:** the birefringence-order result (dim-4 vs (ka)²-suppressed) is the exp_03 deliverable, still open.
- [ ] **Decision to confirm:** R4 experiment-side readout (no in-engine χ API). If an in-engine canonical readout is wanted, that reshapes the v0.3.0 API surface — decide before the release freeze.
