## New subproject

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

> *Retroactive draft:* this fills out the `new-subproject` template
> for `dcl-delta-p-min`, which was provisioned on 2026-05-21.
> Filing this issue *documents* an already-scaffolded subproject;
> the companion research-investigation issue
> (`005-research-investigation-dp-min.md`) captures the research-thread
> shape.  Both stand on their own and cross-reference.

> *Updated 2026-05-24:* refreshed to reflect that `dcl-core v0.1.0`
> shipped on 2026-05-22 (DOI 10.5281/zenodo.20350952) with `core3d`
> at functional release maturity.  Right-hand column of the 4-cell
> grid is unblocked; the investigation's `dcl_core` pin moved from
> `@main` to `@v0.1.0`.  Remaining `dcl-core` gate for Phase~2 is
> the `prob_floor` parameter on `dcl_core.core`, planned for
> `dcl-core v0.2.0`.  Phase~1 is still not started (the original
> draft accidentally checked it).

> *Updated 2026-05-24 (post-Phase-1 + Phase-2-first-cut):*
>
> - Phase~1 (theoretical pass) landed in
>   `paper/sections/theoretical_foundations.tex`.  Three Phase~1
>   audit rows flipped: definition `STUB -> PASS`; cross-engine
>   equivalence `STUB -> PART`; consistency with Paper~I PASS rows
>   `STUB -> PART`.
> - Phase~2 first-cut calibration on the right column of the
>   4-cell grid landed in
>   `src/experiments/exp_12_dp_min_sweep.py`: 9-point $N$-sweep
>   ($10^2 \to 10^{10}$) on `core3d` at $33^3$, single-particle
>   hydrogen in fixed Coulomb well.  Found a stable continuum-$N$
>   baseline at $r_\text{peak} = 19.63$ for $N \geq 10^7$;
>   empirical bound $\delta p_\min \leq 10^{-7}$ preserves the
>   baseline at 5\% tolerance.  Wall-clock 40~s; $\mathcal{A}=1$
>   holds at every tick.
> - `dcl-core v0.2.0` requirements expanded: in addition to
>   `prob_floor` on `dcl_core.core`, Phase~2 first-cut surfaced that
>   **pairwise interactions on `dcl_core.core3d.TickScheduler`**
>   (also deferred to v0.2.0 per the v0.1.0 release notes) are
>   load-bearing for `exp_09` (two-session frequency locking) and
>   `exp_18` (joint resonance with proton + tidal gradient).  Both
>   experiments deferred at this iteration -- no useful right-column
>   data without pairwise interactions.
> - Phase~1 paper-text refined to make the cross-engine
>   equivalence's *double* limit ($a \to 0$ AND $N \to \infty$)
>   explicit; at fixed lattice spacing the engines pin
>   different observables (`core3d` $r_\text{peak} = 19.63$ vs
>   Paper~I `exp_10` $R_1 = 10.3$ at $33^3$), reflecting an
>   engine-protocol difference (uniform vs directed hop kernel;
>   alternating vs both-chirality-per-tick) -- not a $\delta p_\min$
>   effect, but a documentation requirement for `dcl-core v0.2.0`'s
>   release notes.

**Subproject title**

*Minimum Probability Quantum ($\delta p_\min$) in the A=1 Discrete
Causal Lattice: a Cross-Engine Investigation as Paper~III
Prerequisite* -- the δp_min investigation hub of the A=1 DCL
series.  Repo: `dcl-delta-p-min`.

**Primary deliverable type** (single-select -- frames the subproject)

- [x] paper -- a new paper in the series (Zenodo deposit type:
      paper).  *Publication decision deferred to Phase~4 stance
      decision; the paper-shape is load-bearing regardless of
      external publication because the series needs a canonical
      internal reference for the $\delta p_\min$ question.*
- [ ] software package
- [ ] dataset
- [ ] research-artefact
- [ ] formalism module
- [ ] other

**Deliverables**

*Citable artefacts (each may earn its own Zenodo DOI):*

- [x] paper PDF + source  *(publication TBD; see Phase~4 stance
      decision in `paper/sections/paper_iii_stance.tex`)*
- [ ] software package + tagged release  *(the `prob_floor`
      parameter on `dcl_core.core` ships in `dcl-core v0.2.0`, not
      here)*
- [ ] dataset  *(`data/exp_NN_*.npy` files from Phase~2 runs are
      candidate dataset artefacts; not committed at v0.1)*
- [ ] research-artefact
- [ ] animation
- [x] audit-table CSV snapshot at release (per
      `project-zenodo-dataset-deposits` slot 2)  *(conditional on
      external publication)*

*In-repo artefacts (no separate DOI, co-released with the primary):*

- [x] new repo (template + junction setup)  *(`dcl-delta-p-min`;
      provisioned 2026-05-21 from `dcl-paper-experiment-template` via
      `project-dcl-project-repo-provisioning`)*
- [ ] new subdirectory in an existing repo
- [x] new audit table (`paper/sections/audit_table.tex`)  *(seeded
      with 10 rows: 2 inherited guardrails from Paper~I + 8 STUB
      rows for the investigation phases)*
- [x] `CITATION.cff`
- [x] `notes/<topic>.md` file(s)  *(6 working notes; see "Notes"
      below)*
- [x] `release_notes/README.md`
- [x] `external/<name>` junction in dependent repos  *(junctions
      from this repo into upstream: `external/dcl` (Paper~I source
      for exp_09, exp_12), `external/dcl-core` (engines),
      `external/dcl-paper-03-tidal-ionization` (the blocked
      consumer), `external/dcl-mathematics` (downstream consumer),
      `external/research` (formalisation notes))*

*Project planning state (lives in Claude memory, not the repo):*

- [x] new memory entry: `project-delta-p-min-investigation`  *(now
      pointing at the canonical repo)*
- [x] update existing memory entry:
      `project-dcl-project-repo-provisioning` is the workflow this
      provisioning exercised; no edit needed.

*Coordination outputs:*

- [x] cross-repo pin bump in downstream papers  *(this hub already
      bumped `dcl_core @main -> @v0.1.0` on 2026-05-22 after
      `dcl-core v0.1.0` shipped; Paper~III bumps
      `dcl_core @v0.1.x -> @v0.2.0` once the `prob_floor` parameter
      ships and Phase~1-2 outcomes are in)*
- [ ] new Zenodo Community listing / cross-listing  *(if Phase~4
      decides external publication, cross-list to existing
      series + foundations communities)*

**Slot in the framework** (where this subproject fits in the planned
series; pick from existing memory entries or propose a new slot)

- [ ] Proton internals
- [ ] Discrete-probability paper  *(but: if Outcome~D fires, this
      paper is the natural place δp_min's natural value gets pinned
      -- this investigation surfaces δp_min as load-bearing; the
      discrete-probability paper resolves the value)*
- [ ] `dcl-formalism` package + paper
- [ ] Hilbert-6th axiomatization
- [ ] Paper~I follow-on slot (cite #__):
- [x] new slot, not in any catalogue yet: **δp_min investigation
      hub -- Paper~III v1.0 prerequisite**.  Distinct from the
      research thread in `005` because *this* slot is the vehicle
      (repo + audit table from day one).  Lives alongside Paper~III
      until Phase~4 resolves into one of Outcomes A/B/C/D.

**Motivation / load-bearing rationale**

Same as `005-research-investigation-dp-min.md`.  In short: Paper~III
v1.0's central derivation has multiple load-bearing places where a
non-zero $\delta p_\min$ could enter materially; publishing Paper~III
v1.0 with $\delta p_\min$ implicit risks a $\delta p_\min$-aware
correction afterwards.  Resolving the question in advance, in a
dedicated investigation hub, avoids the worst case.

Worth being its own subproject (rather than scattered notes in
Paper~III) because:

- The investigation has its own audit table (10 rows) and three
  custom experiment scripts (`exp_09_dp_min_floor`,
  `exp_12_dp_min_sweep`, `exp_18_dp_min_grid`) -- belongs in a
  paper-experiment repo, not in Paper~III's notes.
- Multiple downstream consumers (Paper~III, `dcl-mathematics`, the
  planned discrete-probability paper) need a single citable home for
  the findings.
- Cross-repo coordination (the `prob_floor` parameter on `dcl-core`)
  is one of the deliverables; the coordination spec lives in
  `notes/dcl_core_coordination.md`.

**Eventual Zenodo deposit type**

- [x] paper  *(conditional on Phase~4 decision; cross-list to
      *Geometric Foundations of Quantum Theory and Gravity*, A=1
      DCL series community)*
- [ ] software
- [ ] dataset
- [ ] other

Zenodo relation metadata (if deposit happens):

- `is supplement to`: Paper~III (this investigation resolves a
  prerequisite of Paper~III)
- `is part of`: A=1 Discrete Causal Lattice series community
- `is documented by`: (primary; nothing documents it upstream)

**Repo / location plan**

- [x] new repo (name): `dcl-delta-p-min`
- [ ] new subdirectory in existing repo
- [ ] lives entirely in an existing paper repo
- Created from template?  `dcl-paper-experiment-template` (same as
  Paper~III).
- Junction setup needed in dependent repos?  Junctions *into* this
  repo are set up locally (gitignored):
  `external/dcl`, `external/dcl-paper-03-tidal-ionization`,
  `external/dcl-core`, `external/dcl-mathematics`,
  `external/research`.  Junctions *from* this repo into downstream
  consumers (Paper~III, `dcl-mathematics`) lands when they pick up
  cite-targets.

**License plan** (default: series convention)

- [x] series default (MIT for code, CC BY 4.0 for prose)
- [ ] override

**Audit-table plan**

- [x] audit table from day one (paper / dataset)
- [ ] no audit table needed
- Initial seeded rows:
  - *Inherited guardrails from Paper~I (PASS):*
    Hydrogen as joint two-session Arnold-tongue lock-in;
    gradient detuning breaks joint resonance.
  - *Investigation-internal (STUB):*
    Operational meaning of $\delta p_\min$ pinned (Phase~1);
    Consistency with Paper~I PASS rows under non-zero $\delta p_\min$
    (Phase~1);
    Cross-engine equivalence: `core` clamp $\leftrightarrow$
    `core3d` $1/N$ (Phase~1);
    4-cell grid on $g_\text{crit}$ (Phase~2);
    4-cell grid on $T_\text{escape}(g)$ (Phase~2);
    Arnold-tongue width floor (Phase~2);
    Observational signature paths for $\delta p_\min$ (Phase~3,
    non-blocking);
    Paper~III stance decision (Phase~4).

**Cross-repo dependencies**

- Requires a `dcl-core` release first?
  - **`core3d` engine maturity -- DONE.**  `dcl-core v0.1.0`
    (2026-05-22, DOI 10.5281/zenodo.20350952) ships `core3d` at
    functional release maturity (`DiscreteCausalSession.wavepacket(...)`
    is explicitly the min-$\Delta p$ generator per the v0.1.0 release
    notes; 88/88 `tests/core3d/*` pass).  Single-session right-column
    experiments (`exp_12` calibration) run against this pin.
  - **`dcl-core v0.2.0` requirements (jointly gate Phase~2
    completion):**
    1. **`prob_floor` parameter on `dcl_core.core.CausalSession`**
       (additive; minor bump if shipped alone).  Gates the **left**
       column of the 4-cell grid; per
       `dcl-delta-p-min/notes/dcl_core_coordination.md` for the
       API spec.
    2. **Pairwise interactions on `dcl_core.core3d.TickScheduler`**
       (explicitly deferred from v0.1.0 per its release notes;
       v0.1.0 `TickScheduler.step()` advances sessions
       independently with no mutual coupling).  Gates the
       *two-body physics* on **both** columns -- `exp_09`
       (two-session frequency locking giving the Arnold-tongue
       width) and `exp_18` (joint electron-proton resonance with
       tidal gradient).  Without it, the right column produces
       only single-body experiments (`exp_12` did so successfully;
       `exp_09`/`exp_18` have no useful single-body proxy).
    3. **Release-notes documentation (recommended):** record that
       the two engines converge in the *double* limit
       ($a \to 0$ AND $N \to \infty$), not in $N \to \infty$ alone.
       At fixed lattice spacing, `core` and `core3d` pin different
       ground-state observables because of hop-kernel and
       chirality-update protocol differences.  This is a
       documentation requirement on v0.2.0's release notes, not a
       code change.
- Requires another paper / package / dataset to land first?  Paper~I
  at v1.0 (done; doi:10.5281/zenodo.20078529) is the only upstream
  prerequisite for Phase~1 (theoretical pass).
- Triggers a downstream bump?  Yes -- Paper~III's `dcl_core` pin
  bumps to `@v0.2.0` after Phase~4 stance decision; Paper~III v1.0
  deposit then follows.

A new finding-target surfaced by `dcl-core v0.1.0`: the
`BresenhamResidual` carry in `core3d` is **real** in v0.1.0; the
v0.1.0 release notes park the hypothesis that it should be
**complex** (representing virtual-particle amplitude) and name
*this investigation's* min-$\Delta p$ experiments as the intended
discriminator.  Phase~2 protocols (`exp_09` / `exp_12` / `exp_18`)
should flag observables that would distinguish real- vs
complex-carry behaviour; any such signature in the `core3d`
column is load-bearing for `dcl-core`'s next release decision.

(See `project-cross-repo-release-coordination` for the bump-and-
rebuild workflow.)

**Phased program**

- [x] Phase~1: theoretical pass (~1-2 days)  *(landed 2026-05-24 in
      `paper/sections/theoretical_foundations.tex`; three Phase~1
      audit rows flipped -- see "Outcomes so far" below)*
- [ ] Phase~2: numerical probe (4-cell grid; ~3-5 days)  *(first
      cut on right column done 2026-05-24 (`exp_12_dp_min_sweep`,
      single-body hydrogen on `core3d`); `exp_09` + `exp_18`
      deferred pending pairwise interactions in `dcl-core v0.2.0`;
      left column waits on `prob_floor` in the same release)*
- [ ] Phase~3: observational signatures (parallel, non-blocking)
- [ ] Phase~4: Paper~III stance decision and revision

**Outcomes so far** (2026-05-24)

*Phase~1 (theoretical pass) -- closed:*

- **Operational meaning of $\delta p_\min$ pinned.**  Audit row
  `STUB -> PASS`.  Candidates~A+B committed together: probability
  floor on continuous amplitudes in `core`, identified with $1/N$
  in `core3d`.  Three concomitant choices recorded (per-site floor
  + global renormalisation; per-tick not at extraction; no separate
  phase quantum).
- **Cross-engine equivalence.**  Audit row `STUB -> PART`.
  Non-equivalent at finite $N$ (the embedding's image is the
  $1/N$-quantised sublattice; `core`'s dynamics does not preserve
  that sublattice).  Sufficient condition for asymptotic equivalence:
  the *double* limit $N \to \infty$ AND $a \to 0$ (lattice spacing),
  with the $N$-dependent piece bounded $O(1/N)$ per tick by
  rounding-error argument and the $a$-dependent piece asserted by
  construction of both kernels.
- **Consistency with Paper~I PASS rows under non-zero $\delta p_\min$.**
  Audit row `STUB -> PART`.  Analytical upper bounds derived for
  both Paper~I guardrails: hydrogen Bohr recovery requires
  $\epsilon \lesssim 10^{-10}$ to $10^{-12}$ (order-of-magnitude
  from the wavefunction's box-edge amplitude); Arnold-tongue
  lock-in requires $\epsilon \lesssim \Delta\omega_\text{tongue}^2$.
- **Joint-tick rule lifts unchanged.**  No new tick-scheduling
  primitive needed; two candidate $\delta p_\min$-couplings
  considered and rejected on $\mathcal{A}=1$ and locality grounds.
- **New finding-target surfaced**: the Bresenham residual carry's
  real-vs-complex choice (parked in `dcl-core v0.1.0`'s release
  notes; this investigation is the intended discriminator).

*Phase~2 first cut (right column only) -- partial:*

- **`exp_12` calibration.**  Single-particle hydrogen in fixed
  Coulomb well on `core3d` (33$^3$, 400 ticks, $N$-sweep
  $10^2 \to 10^{10}$).  Engine baseline $r_\text{peak} = 19.63$
  stable for $N \geq 10^7$ (flat across 4 decades).  Empirical
  bound: $\delta p_\min \leq 10^{-7}$ preserves the baseline at
  5\% tolerance -- *less* restrictive than the Phase~1 analytical
  estimate $\epsilon \lesssim 10^{-10}$--$10^{-12}$ (the
  integer-quantisation noise is smoothed by the engine's diffusive
  dynamics faster than the worst-case wavefunction-tail estimate
  predicted).  Audit row stays `PART` (left column still pending).
- **`exp_09`, `exp_18` deferred.**  Both require pairwise
  interactions in `core3d` (the two-session frequency locking
  giving Arnold-tongue width; the two-body joint resonance with
  tidal gradient).  No useful single-body proxy.  Audit rows stay
  `STUB`; revisited after `dcl-core v0.2.0`.
- **Engine-protocol observation.**  `core3d`'s $r_\text{peak} = 19.63$
  vs Paper~I `exp_10`'s $R_1 = 10.3$ at the same $33^3$ lattice.
  Documents the double-limit framing of the Phase~1 cross-engine
  equivalence finding; flagged in `dcl-core v0.2.0` requirements
  (above) for the release notes.

**Notes that may be created or updated**

`notes/<topic>.md` files in `dcl-delta-p-min/notes/`:

- *Existing (v0.1):* `dp_min_definition.md`,
  `dp_min_impact_channels.md`, `cross_engine_equivalence.md`,
  `four_cell_grid_methodology.md`,
  `paper_iii_blocking_relationship.md`,
  `dcl_core_coordination.md`.
- *Planned (Phase~3):* `dp_min_observational.md` -- candidates for
  pinning δp_min from external (non-DCL) physics data.

`project_*` or `feedback_*` memory entries:

- *Existing:* `project-delta-p-min-investigation` (updated 2026-05-21
  to point at the canonical repo).
- *Future (if Outcome~D):* the planned
  `project-discrete-probability-paper` memory entry, when written,
  would cite this investigation as the upstream surfacer of
  δp_min's role.

**Tools / resources needed**

- [ ] better CPU / GPU / memory / disk
- [x] longer wall-clock budget (estimate): ~5-7 days total for
      Phases~1-2 (theoretical + numerical); Phase~3 is parallel and
      non-blocking
- [ ] dataset access / paid software
- [ ] collaborator with specific expertise
- [x] `dcl_core` primitives that don't exist yet -- two `dcl-core
      v0.2.0` deliverables jointly gate Phase~2 completion:
      1. `prob_floor` parameter on `dcl_core.core.CausalSession`
         (left column of the 4-cell grid).
      2. Pairwise interactions on `dcl_core.core3d.TickScheduler`
         (two-body physics on `exp_09` + `exp_18`; deferred from
         v0.1.0 per its release notes).

      *Already shipped (no longer blockers):* `core3d` engine
      maturity (`dcl-core v0.1.0`, 2026-05-22).
- [x] new GitHub repo creation / template *(already done; repo
      exists)*
- [ ] new Zenodo Community

**Dependencies / blockers**

- *Phase~1 (theoretical):* DONE 2026-05-24.  No blocker; the
  `dcl_core @v0.1.0` pin sufficed for reading both engines and
  framing the cross-engine equivalence question.
- *Phase~2 first cut (right column, single-body):* DONE 2026-05-24
  via `exp_12_dp_min_sweep` on `core3d` (engine baseline at
  $r_\text{peak} = 19.63$; empirical $\delta p_\min \leq 10^{-7}$
  preserves the baseline at 5\% tolerance).
- *Phase~2 completion:* gated on `dcl-core v0.2.0` -- both
  `prob_floor` (for the left column of all three experiments) and
  pairwise interactions in `core3d.TickScheduler` (for the
  two-body physics of `exp_09` and `exp_18`).  Right column
  single-body data is as exercised as it can be at v0.1.0; no
  useful single-body proxies exist for the two-body experiments.
- *Phase~3 (observational signatures):* parallel and non-blocking;
  not yet started.
- *Phase~4 stance decision:* requires Phase~1--2 outcomes.

**Status**

- [x] proposed (idea-stage)
- [x] scoped (this template filled in fully)
- [x] repo / location created  *(provisioning landed
      2026-05-21; commit e37b581)*
- [x] first deliverable drafted  *(Phase~1 theoretical pass landed
      2026-05-24 in `paper/sections/theoretical_foundations.tex`,
      commit a082763; Phase~2 first cut on the right column
      followed in commit 76177b1)*
- [ ] first deposit live on Zenodo  *(conditional on Phase~4
      publication decision)*
- [ ] mature  *(Phase~2 completion and Phase~4 stance decision
      pending `dcl-core v0.2.0`; see "Dependencies / blockers")*

*(Status note: subproject is past `first deliverable drafted` as of
2026-05-24.  Next gate is Phase~2 completion, which waits on
`dcl-core v0.2.0` (`prob_floor` on `core` + pairwise interactions
on `core3d`).  Phase~4 graduation is when Paper~III v1.0 deposit
lands with the δp_min stance committed.)*

**Additional context**

- *Why a separate subproject from Paper~III.*  See "Motivation"
  above.  In short: audit table + experiment scripts + multiple
  downstream consumers + cross-repo coordination output all argue
  for a dedicated repo.
- *Why a paper-shaped writeup if publication is uncertain.*  Same
  reasoning as `dcl-mathematics`'s issue draft 004: paper format is
  load-bearing as the series' canonical internal reference
  regardless of external peer review.  Theorems, derivations, and
  sectioned exposition are the right shape for the role.
- *Naming.*  Originally provisioned on GitHub as
  `project-delta-p-min-investigation` (matching the memory entry
  slug); renamed to `dcl-delta-p-min` on 2026-05-21 to match the
  series naming pattern (`dcl-*` prefix).  Local directory
  renamed accordingly.  Memory entry slug retained as
  `project-delta-p-min-investigation` per the convention that
  memory slugs describe the *thread* rather than the *repo*.
- *Parallel pair with `005-research-investigation-dp-min.md`.*  This
  draft (006) is the vehicle shape; 005 is the thread shape.  Both
  stay valid and cross-reference each other.
