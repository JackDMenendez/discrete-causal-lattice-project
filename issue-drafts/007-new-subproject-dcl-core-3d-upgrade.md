## New subproject

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

**Subproject title**

*`dcl-core` 3D upgrade -- bringing `dcl_core.core3d` (integer-token
engine) to v1.0 maturity alongside `dcl_core.core` (continuous-amplitude
engine).  Targets `dcl-core v1.0.0` as the joint-engine release tag.*

**Primary deliverable type** (single-select -- frames the subproject)

- [ ] paper
- [x] software package -- a tagged `dcl-core` release in which
      `dcl_core.core3d` is feature-complete, cross-validated against
      `dcl_core.core`, and consumable by downstream subprojects (the
      4-cell grid in `dcl-delta-p-min`, the planned discrete-probability
      paper, Paper~III's numerical confirmation rows).
- [ ] dataset
- [ ] research-artefact
- [ ] formalism module
- [ ] other

**Deliverables**

*Citable artefacts (each may earn its own Zenodo DOI):*

- [ ] paper PDF + source
- [x] software package + tagged release -- `dcl-core v1.0.0` (or
      whatever joint-engine milestone version the repo settles on;
      currently at `v0.1.0-dev`).  Concept-DOI + per-version DOI on
      Zenodo per the repo's existing software-deposit pattern.
- [ ] dataset
- [ ] research-artefact
- [ ] animation
- [ ] audit-table CSV snapshot at release  *(dcl-core is software,
      not a paper -- no audit table.  But it ships the test-suite
      pass record at release time, which is the software analogue.)*

*In-repo artefacts (no separate DOI, co-released with the primary):*

- [ ] new repo (template + junction setup)  *(uses existing
      `dcl-core` repo)*
- [ ] new subdirectory in an existing repo  *(the `core3d/`
      submodule already exists at `src/dcl_core/core3d/`; this
      subproject matures it rather than creating it)*
- [ ] new audit table  *(software repo; no audit table)*
- [x] `CITATION.cff` bump  *(version + date-released fields)*
- [x] `notes/<topic>.md` file(s)  *(see "Notes" below)*
- [x] `release_notes/README.md`  *(per-release entry for the v1.0.0
      cut)*
- [ ] `external/<name>` junction in dependent repos  *(no new
      junctions; existing `external/dcl-core` junctions in Paper~III,
      `dcl-delta-p-min`, etc. pick this up automatically on pin-bump)*

*Project planning state (lives in Claude memory, not the repo):*

- [x] new memory entry: `project-dcl-core-3d-upgrade`  *(captures the
      work-in-progress shape, the cross-validation milestone, and the
      downstream consumers blocked by completion)*
- [x] update existing memory entry: `project-delta-p-min-investigation`
      *(Phase~2 prerequisites currently list only the `prob_floor`
      addition to `dcl_core.core`; must be extended to also list the
      `core3d` upgrade as a gating dcl-core deliverable for the
      right-hand column of the 4-cell grid)*

*Coordination outputs:*

- [x] cross-repo pin bump in downstream papers  *(once `dcl-core
      v1.0.0` lands: pin bumps in `dcl` (Paper~I; consumes `core`
      only), `dcl-paper-03-tidal-ionization` (Paper~III; consumes
      both for the 4-cell grid), `dcl-delta-p-min` (consumes both),
      `dcl-generator-zoo` (consumes `core` as a sanity check on the
      71-dim algebra's continuum-limit predictions))*
- [ ] new Zenodo Community listing / cross-listing  *(uses existing
      A=1 DCL series community)*

**Slot in the framework** (where this subproject fits in the planned
series; pick from existing memory entries or propose a new slot)

- [ ] Proton internals
- [ ] Discrete-probability paper  *(but: this engine upgrade is a
      hard prerequisite for the discrete-probability paper, since
      that paper's centerpiece showcase runs on `core3d`; per the
      `dcl-core` README, `core3d` is the *empirical companion* to
      that paper)*
- [ ] `dcl-formalism` package + paper
- [ ] Hilbert-6th axiomatization  *(downstream: the continuum-limit
      verification at the heart of the capstone consumes `core3d`'s
      cross-validation result)*
- [ ] Paper~I follow-on slot (cite #__):
- [x] new slot, not in any catalogue yet: **`dcl-core` 3D engine
      maturity milestone**.  Lives inside the existing `dcl-core`
      repo; the *slot* is the body of work that takes `core3d` from
      `v0.1.0-dev` scaffolding to a release that downstream consumers
      can pin against.

**Motivation / load-bearing rationale**

`dcl_core.core3d` is already scaffolded inside `dcl-core` at
`src/dcl_core/core3d/` (lattice, session, hop, remainder, scheduler,
backends) with a tests/core3d/ directory carrying tests for clifford,
conservation, continuum_limit, hop, lattice, and remainder.  A
top-level `tests/test_cross_validation.py` captures the design intent:
`core <-> core3d` convergence in the continuum limit.

> **RELEASE UPDATE (2026-06-07) -- shipped as `v0.2.0`, NOT `v1.0.0`;
> v1.0.0 is now gated on `dcl-delta-p-min`.**  The Phase~4 release cut
> happened, but the version-number decision (user call) went to
> **`v0.2.0`**, not the `v1.0.0` this whole draft is framed around.
> Rationale: keep the pre-1.0 "API unstable" signal one more cycle --
> GPU kernels, inter-session coupling, and the complex-carry
> resolution are still ahead and may move the public surface, so a
> formal v1.0 API freeze is premature.
> - **`dcl-core v0.2.0` RELEASED 2026-06-07** -- DOI
>   `10.5281/zenodo.20586191`, commit `2c866a8`, tag `v0.2.0`, GitHub
>   Release published, sdist+wheel deposited.  Content = the Phase~1-2
>   cross-validation (all 4/4) + the Phase~3 two-frame naming retrofit
>   (shims intact) + data-deposit policy doc + reproducibility refresh.
> - **`v1.0.0` is now the NEXT cut**, gated on the `dcl-delta-p-min`
>   study finishing, and **co-releases with Paper~III**.  The formal
>   API freeze AND the downstream pin bumps both move to that cut.  So
>   this issue's "joint-engine v1.0.0" deliverable is **not yet met** --
>   v0.2.0 is an interim release toward it.  (See dcl-core CLAUDE.md
>   CURRENT STATUS and the `v1-release-gating` memory.)
> - **Phase~3 prose-docs sweep still NOT done** -- `docs/reference/
>   api.md`, tutorials, and `README.md` still cite old core3d names.
>   Not a v0.2.0 blocker; carried forward to the v1.0.0 cut.
> - **Downstream pin bumps NOT done** -- deferred to the v1.0.0
>   co-release (Paper~III pin stays parked at its current ref), which
>   makes the "once `dcl-core v1.0.0` lands" framing below literally
>   accurate again.
> - **New sibling tool (out of this issue's scope):**
>   `dcl-lattice-viewer` (github.com/JackDMenendez/dcl-lattice-viewer,
>   tag `v0.1.0`, **no Zenodo**) -- renders core3d `.npy` state to a
>   browser-explorable `.glb` / three.js model.

> **PROGRESS UPDATE (2026-06-03).**  The three maturity gaps below are
> now substantially closed; the engine is at "downstream-consumable"
> maturity for the CPU backend.  Remaining work is the release cut
> (Phase 4) plus a prose-docs sweep (tail of Phase 3).  See the
> per-gap and per-phase annotations.

The original maturity gaps and their current state:

- ~~Tests under `tests/core3d/` are partial or failing in places (or
  marked `xfail` / `skip`).~~  **DONE.**  All `tests/core3d/*` PASS
  (lattice, session, hop, remainder, conservation, continuum_limit,
  clifford, scheduler).  Full suite: **232 passed, 26 xfailed, 0
  skipped** (the 26 xfails are pre-existing Paper~I `core`-port drift,
  inherited verbatim, NOT core3d).
- ~~Cross-validation (`test_cross_validation.py`) is not yet
  consistently PASS at the precision needed for the 4-cell grid.~~
  **DONE.**  All **4/4** cross-validation tests PASS.  The "evolves
  identically" framings were reframed to what is well-posed at fixed
  lattice (the two engines are *different discretisations* and agree
  only in the double limit `a -> 0` AND `N -> infinity`, per the
  delta-p-min Phase~1 finding): conservation (each engine's own A=1),
  free-propagation (core3d self-convergence, `O(1/N)` deterministic
  Bresenham), two-body lock-in (stable-radius, not shared `R_1`), and
  Arnold tongue (single-session orbital resonance; the coupled-session
  Part~D tongue is a v0.2.0 follow-on).
- ~~The public API exposed from `src/dcl_core/core3d/__init__.py` is
  not yet stable enough to pin downstream.~~  **MOSTLY DONE.**  A
  two-frame lattice-intrinsic naming retrofit landed (commit
  `83813fc`): `BresenhamResidual -> TokenResidual`, session state
  `N_R/N_L/phi_R/phi_L -> N_RGB/N_CMY/phi_RGB/phi_CMY`, plus
  `dp_min`/`coordination`, all with backward-compatible deprecation
  shims.  Reviewed by the api-stability + physics-naming agents.  This
  is intended as the **v1.0 API freeze**.  Tail item: prose docs
  (`docs/reference/api.md`, tutorials, `README.md`) still cite the old
  names and need a mechanical sweep.

These gaps directly gate at least four downstream subprojects:

1. **`dcl-delta-p-min`** -- the 4-cell grid (`core / core3d` x
   `+- δp_min`) is the central methodology; the right-hand column
   cannot run without a working `core3d`.  See
   `project-delta-p-min-investigation` memory entry, and `notes/
   four_cell_grid_methodology.md` in `dcl-delta-p-min`.
2. **Paper~III (`dcl-paper-03-tidal-ionization`) v1.0** -- transitively
   blocked, since Paper~III v1.0 is blocked on dcl-delta-p-min Phase
   1-2 (per the README and the δp_min investigation memory).
3. **Discrete-probability paper** (planned) -- per dcl-core's README,
   `core3d` is the *empirical companion* to this paper; it cannot
   land until `core3d` is at v1.0 maturity.
4. **Hilbert-Sixth capstone** (planned) -- the continuum-limit
   verification at the heart of the capstone consumes the `core3d`
   cross-validation result.

Worth being its own subproject (rather than scattered changes inside
`dcl-core`'s ongoing development) because:

- It has a clear single deliverable shape: the next tagged release
  in which all `tests/core3d/` are PASS, `test_cross_validation.py`
  is PASS at downstream-consumable precision, and the public API
  is stable enough to pin.
- It has multiple known downstream consumers waiting on it (above).
- It triggers a coordinated multi-repo pin bump per
  `project-cross-repo-release-coordination`.

**Eventual Zenodo deposit type**

- [ ] paper
- [x] software (release-tag-driven; concept-DOI + per-version DOIs)
      -- a versioned deposit of `dcl-core v1.0.0` (or equivalent
      joint-engine milestone)
- [ ] dataset
- [ ] other

Zenodo relation metadata (if deposit happens):

- `is supplement to`: nothing direct (the engine is the primary;
  papers cite *this* deposit, not the reverse)
- `is part of`: A=1 Discrete Causal Lattice series community
- `is documented by`: `dcl-core/README.md`, `dcl-core/docs/`, the
  per-release `release_notes/` entry, and the test suite

**Repo / location plan**

- [ ] new repo (name):
- [ ] new subdirectory in existing repo  *(`src/dcl_core/core3d/`
      already exists at `v0.1.0-dev`)*
- [x] lives entirely in an existing paper repo  *(strictly: existing
      software repo -- `dcl-core`)*
- Created from template?  N/A; the repo already exists, having been
  scaffolded from the `dcl-core-template`.
- Junction setup needed in dependent repos?  No new junctions; the
  existing `external/dcl-core` junctions in `dcl-paper-03-tidal-
  ionization`, `dcl-delta-p-min`, etc. resolve to this repo
  automatically.

**License plan** (default: series convention)

- [x] series default (MIT for code, CC BY 4.0 for prose)
- [ ] override

**Audit-table plan**

- [ ] audit table from day one (paper / dataset)
- [x] no audit table needed  *(this is a software subproject; the
      audit-row analogue is the test suite, plus any audit rows in
      downstream papers that flip STUB -> PASS once `core3d` lands)*
- Test-suite invariants that must reach PASS for v1.0 *(all PASS as of
  2026-06-03)*:
  - [x] `tests/core3d/test_lattice.py` -- bipartite octahedral lattice
    invariants
  - [x] `tests/core3d/test_hop.py` -- HopOperator (bipartite Dirac)
    symmetries
  - [x] `tests/core3d/test_remainder.py` -- `TokenResidual` (formerly
    `BresenhamResidual`) carry correctness
  - [x] `tests/core3d/test_conservation.py` -- A=1 integer-equality
    conservation
  - [x] `tests/core3d/test_continuum_limit.py` -- `E^2 = m^2 + p^2`
    convergence at large token budget
  - [x] `tests/core3d/test_clifford.py` -- Clifford anticommutator
  - [x] `tests/core3d/test_scheduler.py` -- tick orchestration / A=1
    over many ticks
  - [x] `tests/test_cross_validation.py` -- `core <-> core3d` (all 4/4;
    reframed to the well-posed fixed-lattice claims, see PROGRESS
    UPDATE above)
  - *Not yet present (deferred):* `test_gauge_invariance.py` -- needs
    Peierls / `A_mu` gauge coupling in the hop (v0.2.0), so it is NOT a
    v1.0 gate.

**Cross-repo dependencies**

- Requires a `dcl-core` release first?  *N/A -- this subproject IS
  the next `dcl-core` release.*
- Requires another paper / package / dataset to land first?  Nothing
  external blocks it.  Internal blockers are the test-suite items
  listed above.
- Triggers a downstream bump (`dcl-core` release that forces this
  subproject's consumers to bump)?  Yes -- pin bumps in:
  - `dcl` (Paper~I) -- consumes `core` only; backwards-compat
    expected, soft pin bump
  - `dcl-paper-03-tidal-ionization` (Paper~III) -- consumes both
    engines for the 4-cell grid; hard pin bump
  - `dcl-delta-p-min` -- consumes both engines; hard pin bump
  - `dcl-generator-zoo` -- consumes `core` for sanity checks; soft
    pin bump

(See memory entry `project-cross-repo-release-coordination` for the
bump-and-rebuild workflow.)

**Phased program**

- [x] **Phase~1: test-suite triage** *(done 2026-06-02)* -- found the
      core3d modules already implemented and unit-green (the CLAUDE.md
      "all stubs" status was stale); the sole gap was the 4 skipped
      `tests/test_cross_validation.py` entries.
- [x] **Phase~2: cross-validation precision** *(done 2026-06-03)* --
      all 4/4 cross-validation tests PASS.  Key finding (jointly with
      `dcl-delta-p-min` Phase~1): the two engines are *different
      discretisations* that pin different observables at fixed lattice
      spacing and converge only in the double limit (`a -> 0` AND
      `N -> infinity`), so the tests assert the well-posed claims
      (self-convergence, stable lock-in, per-engine structure), NOT
      naive cross-engine equality.
- [~] **Phase~3: API stabilisation** *(mostly done 2026-06-03)* --
      public API audited + frozen for v1.0 via the two-frame naming
      retrofit (commit `83813fc`), reviewed by the api-stability +
      physics-naming agents; deprecation shims keep old names working.
      **Remaining:** mechanical prose-docs sweep (`docs/reference/
      api.md`, `docs/tutorials/01_first_session.md`, `README.md`,
      design docs 01/02) to the new names, and the v1.0 contract write-
      up in `docs/`.
- [~] **Phase~4: release** *(done for v0.2.0 on 2026-06-07; v1.0.0
      cut still ahead)* -- the version-number decision resolved to
      **0.2.0, NOT 1.0.0** (keep pre-1.0 signal).  `dcl-core v0.2.0`
      shipped: `_version.py` + `CITATION.cff` bumped, `release_notes/
      v0.2.0*` written, Zenodo deposit (DOI `10.5281/zenodo.20586191`,
      DOI-first then back-filled), commit `2c866a8`, tag `v0.2.0`,
      GitHub Release published.  **Still to do for the v1.0.0 cut**
      (gated on `dcl-delta-p-min`): the Phase~3 prose-docs sweep, the
      formal API freeze, the v1.0.0 deposit, and the pin-bump
      release-coordination issue per `project-cross-repo-release-
      coordination` (Paper~III + dcl-delta-p-min hard bumps), all
      co-released with Paper~III.

*Explicitly deferred to v0.2.0 (NOT v1.0 gates):* GPU/CuPy hop kernels
(`backends/gpu.py` stubs), the real-vs-complex `TokenResidual.carry`
resolution (discriminated by `dcl-delta-p-min`'s min-Δp experiments),
the coupled-session Arnold-tongue (Part~D), `prob_floor` on `core`, and
`test_gauge_invariance`.

**Notes that may be created or updated**

`notes/<topic>.md` files in `dcl-core/notes/`:

- *Possibly new:* `notes/core3d_v1_readiness.md` -- the working
  document for Phase~1-3; the test-triage table, the API
  stabilisation list, and the cross-validation precision target.
- *Possibly new:* `notes/cross_validation_tolerance.md` -- the
  agreed precision target for `test_cross_validation.py` (set
  jointly with `dcl-delta-p-min`'s Phase 1 theoretical pass).
- *Cross-cite:* the `dcl-delta-p-min/notes/four_cell_grid_
  methodology.md` and `dcl-delta-p-min/notes/cross_engine_
  equivalence.md` files, which already set expectations on what
  `core3d` must deliver.

`project_*` or `feedback_*` memory entries:

- *New:* `project-dcl-core-3d-upgrade` -- captures this subproject's
  forward-looking design (cross-validation milestone, downstream
  consumers, release coordination).
- *Update:* `project-delta-p-min-investigation` -- the
  "Concrete coordination outputs" section currently lists only the
  `prob_floor` addition to `dcl_core.core` as a `dcl-core`
  deliverable.  It needs a second item: this `core3d` v1.0 upgrade
  is the *other* gating `dcl-core` deliverable for Phase 2 numerics.

**Tools / resources needed**

- [ ] better CPU / GPU / memory / disk
- [x] longer wall-clock budget (estimate): unknown until Phase~1
      triage; expect ~2-4 weeks of focused work depending on the gap
      classification.  This is the largest of the currently-tracked
      `dcl-core` work items.
- [ ] dataset access / paid software
- [ ] collaborator with specific expertise
- [ ] sympy / `dcl_formalism` primitive that doesn't exist yet
- [ ] new GitHub repo creation / template
- [ ] new Zenodo Community

**Dependencies / blockers**

- *Productively start:* nothing blocks Phase~1 triage; the test
  suite already exists and can be run against `core3d` at HEAD.
- *Phase~2 cross-validation precision target:* should be set jointly
  with `dcl-delta-p-min`'s Phase~1 theoretical pass on cross-engine
  equivalence -- otherwise the target is guessed rather than
  derived.
- *Phase~4 release:* no external blocker; uses the existing
  release-coordination workflow.

**Status**

- [ ] proposed (idea-stage)
- [x] scoped (this template filled in)
- [x] repo / location created  *(scaffolding already in place at
      `src/dcl_core/core3d/` and `tests/core3d/`)*
- [x] first deliverable drafted  *(Phases 1-2 done; Phase 3 mostly
      done -- engine is feature-complete + cross-validated on CPU)*
- [x] first deposit live on Zenodo  *(an **interim** one: `dcl-core
      v0.2.0`, DOI `10.5281/zenodo.20586191`, 2026-06-07 -- NOT the
      v1.0.0 this issue defines graduation against)*
- [ ] mature

*(Status note, updated 2026-06-07: `dcl-core v0.2.0` is RELEASED --
all `tests/core3d/*` and all 4 cross-validation tests PASS, the
two-frame naming retrofit shipped with deprecation shims, and the
release is deposited on Zenodo (DOI `10.5281/zenodo.20586191`, tag
`v0.2.0`).  But the cut was deliberately **v0.2.0, not v1.0.0** --
this issue's graduation criterion (`dcl-core v1.0.0`, the formal API
freeze, co-released with Paper~III) is therefore **NOT yet met**.
v1.0.0 is gated on the `dcl-delta-p-min` study finishing.  Remaining
to graduate: finish dcl-delta-p-min, do the Phase~3 prose-docs sweep,
freeze the API, cut + deposit `dcl-core v1.0.0` alongside Paper~III,
and run the downstream pin bumps.  See the `v1-release-gating` memory
and dcl-core's CLAUDE.md CURRENT STATUS.  Supersedes the 2026-06-03
note that read the API as already "frozen for v1.0" -- the freeze is
deferred to the v1.0.0 cut.)*

**Additional context**

- *Why this surfaced as a distinct subproject now.*  The
  `dcl-delta-p-min` provisioning on 2026-05-21 made it explicit that
  the 4-cell grid methodology depends on *both* `core` and `core3d`
  reaching downstream-consumable maturity.  The `prob_floor`
  addition to `core` was already on the books; the `core3d` upgrade
  was implicit and is now being made explicit.
- *Why not file as a `core-software-change` issue instead.*  The
  body of work spans multiple modules, multiple test files, an API
  stabilisation pass, and a coordinated multi-repo release.  The
  `core-software-change` template is shaped for single API changes
  (e.g. "add `prob_floor` parameter on `dcl_core.core`"); the
  `new-subproject` template is the right shape for a multi-phase
  effort with downstream coordination.
- *Naming.*  "3D upgrade" is shorthand for "bring the integer-token
  3D engine up to release maturity"; the canonical name of the
  module is `dcl_core.core3d`, and the canonical name of the
  release-shaped deliverable is whatever version the joint-engine
  milestone lands as (likely `v1.0.0`).
- *Relationship to `005` and `006`.*  Issue `005` (research-
  investigation, δp_min) and `006` (new-subproject, dcl-delta-p-min)
  collectively define the *consumer*; this draft `007` defines the
  *engine*.  The dependency graph is `007 -> 006 -> 005 -> Paper~III
  v1.0`.
