## Core software change

**Affected submodule** (check one)

- [x] `dcl_core.core3d` (integer-token engine; new design)

> `dcl_core.core` is **legacy-only** here — kept to reproduce existing
> experiments, not extended for this physics (design doc §1.1).

**Module / file affected**

- `src/dcl_core/core3d/hop.py` — `_hop_average` (Peierls documented, not
  implemented) and `step()` (mirror the `external_potential` threading)
- `src/dcl_core/core3d/lattice.py` — `BipartiteLattice` (keep frozen /
  stateless)
- `tests/test_peierls.py` (new)
- `src/dcl_core/_version.py`, `CITATION.cff`, `release_notes/v0.3.0.md`

**Current limitation**

core3d has no **U(1) gauge field coupled to the hop via the Peierls
substitution**. `_hop_average` does plain periodic shifts; the
`exp(i A·v)`-per-hop coupling is named in the docstring but not
implemented, and `BipartiteLattice` carries no gauge field. Without it,
the gauge analogue of `exp_01` cannot be run.

**Proposed change**

Implement the requirements in
[`docs/design/04_gauge_field_and_vacuum_response.md`](https://github.com/JackDMenendez/dcl-core/blob/main/docs/design/04_gauge_field_and_vacuum_response.md)
(REQUIREMENTS, target **v0.3.0**):

- **R1** — `vector_potential` arg on `HopOperator.step` (shape
  `(3, *lattice.shape)`), mirroring `external_potential`; `None` ⇒
  current behaviour bit-for-bit.
- **R2** — Peierls link phase `exp(i · A_mid · v)` in `_hop_average`,
  mid-point convention `A_mid = ½(A(x)+A(x+v))` (Paper I App. B); CPU
  **and** GPU RawKernel.
- **R3** — `uniform_B_potential(shape, B_vec, origin)` helper
  (symmetric gauge `A(r)=½ B×(r−origin)`), to orient `B` along
  `(1,1,-1)`, perpendicular, and oblique.
- **R4** — vacuum-averaged induced-response (A=1 magnetic
  susceptibility) readout, token-exact; estimator may live in the
  experiment (open definitional choice flagged in the doc).
- **R5** — orientation sweep at scale: embarrassingly parallel across
  orientations × large `N` × lattices to `129^3`; GPU Peierls path is
  required because the central isotropy precision is `N`-bound.

**Motivation**

Drives **Paper IV** gauge-sector channel, experiment `exp_03`. Note the
gauge-sector audit row is already **PASS as a structural result** (see
Paper IV `notes/gauge_sector_structural_conclusion.md`): the
operator-level `Q` anisotropy `{4,4,16}` is removed from observables by
the `O_h` symmetry the framework requires. `exp_03` is therefore the
**confirmatory dynamical demonstration** — that the A=1 token vacuum
actually averages `Q` to `8·I` — not a gate on the paper's claim.

**API / interface impact**

- [x] **Public API addition** (minor version bump required) — new
  optional `vector_potential` arg + `uniform_B_potential` helper.
- All new arguments default to `None`/off; `core` untouched; no break.

**Performance / correctness impact**

A=1 exactness must be preserved with the Peierls phase present (the
phase is carried on `ψ_new` *before* the `|ψ|^2` reduction, compatible
with the current real-target `TokenResidual`; document the interaction).
CPU/GPU parity to float tolerance. Determinism preserved (needed for the
orientation sweep to be comparable).

**Test invariants touched**

- [x] `test_conservation.py` — A=1 integer equality under gauge field
- [x] `test_hop.py` — hop-operator symmetries
- [x] other: **`test_peierls.py` (new)** — acceptance tests #1–#6 from
  the design doc:
  1. zero-field regression (bit-for-bit)
  2. gauge covariance / U(1) Ward identity (pure-gauge `A=∇Λ` leaves
     `|ψ|²` invariant)
  3. continuum `B→0` (quadratic vanishing)
  4. single-probe reproduces `Q` eigenstructure `{4,4,16}`, axis
     `(1,1,-1)`
  5. **vacuum average → isotropy** (`8·I`) — load-bearing physics test
  6. A=1 exactness under gauge field

**Dependencies / related issues**

- Parent subproject: **#9** (dcl-core 3D upgrade).
- **Blocks** Paper IV `exp_03` (**#18**) — confirmatory, not a gate on
  the gauge-sector PASS.
- **Infrastructure dependency:** GPU runtime + multi-process/-device
  fan-out (R5); offered/provisioned 2026-06-16. Code can land CPU-first,
  but acceptance test #5's precision scales with GPU-bound `N`.
- Out of scope (deferred): dynamical gauge propagation, the `1/g²`
  prefactor, non-abelian fields.

**Success criteria**

core3d **v0.3.0** released (additive, no break): `test_peierls.py`
acceptance tests #1–#6 pass, GPU Peierls path implemented, `_version.py`
/ `CITATION.cff` / `release_notes/v0.3.0.md` bumped. `exp_03` can then
run the orientation sweep and produce the single-probe-`Q`
vs vacuum-isotropy contrast that numerically witnesses the gauge-sector
structural conclusion.

**Additional context**

Upstream physics: Paper I App. B (`Q`-tensor `{4,4,16}`, `O_h`
averaging to Maxwell, optical axis `(1,1,-1)`); Paper II (gauge coupling
ratio `g_3²/g_2² = 3/2`). Design doc authored 2026-06-16 (currently
uncommitted in dcl-core).
