## New subproject

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

> *Retroactive draft:* this fills out the `new-subproject` template
> for Paper III, which is already at v0.1.  Filing this issue
> *documents* an in-flight subproject rather than spinning one up
> from scratch.  Status reflects current state ("first deliverable
> drafted"), not "proposed."

A *new subproject* is a new releasable thing in the series.  Releasable
means it eventually earns its own Zenodo DOI, repo, or other stable
handle and is consumed by something downstream (a paper, a reader, a
sibling subproject).

For modifying an existing paper, use `paper-enhancement`.  For an
early-stage research thread whose deliverable shape isn't decided yet,
use `research-investigation`.  For a specific interactive / explorable
artefact, use `research-artefact` directly.

**Subproject title**

*Tidal Ionization of Atomic Hydrogen and the Quantum Roche Limit* --
Paper III of the A=1 Discrete Causal Lattice series.

The central result is the quantum Roche limit
$M_\text{min}(d) = \Delta\omega_\text{tongue} \cdot d^3 / R_1$ -- the
same $d^3$ scaling as the classical Roche limit, derived from the
Arnold-tongue width of the bipartite tick-rule rather than from body
density.  The paper introduces a third ionization channel (gradient
detuning) alongside the standard thermal (Saha) and pressure
(Pauli) channels, and predicts an atomic ISCO with two observational
signatures (21\,cm HI inner-edge morphology, Fe K$\alpha$ line-profile
inner edge).

**Primary deliverable type** (single-select -- frames the subproject)

- [X] paper -- a new paper in the series (Zenodo deposit type: paper)
- [ ] software package -- a new pip-installable / importable package
  (Zenodo deposit type: software)
- [ ] dataset -- structured, machine-readable, citable data
  (Zenodo deposit type: dataset; see memory entry
  `project-zenodo-dataset-deposits`)
- [ ] research-artefact -- standalone interactive / explorable object
  (Zenodo deposit type: software or other; see also
  `research-artefact.md` for artefact-specific scoping)
- [ ] formalism module -- a `dcl_formalism` module (Hilbert-6th-shaped:
  axioms / theorems / continuum-limit primitives; see memory entry
  `project-a1-formalism-package`)
- [ ] other: _______________________

**Deliverables** (full set this subproject will produce -- check all
that apply, including secondary artefacts co-produced with the primary)

*Citable artefacts (each may earn its own Zenodo DOI):*

- [X] paper PDF + source
- [ ] software package + tagged release  *(consumes `dcl-core` as a
  pinned dependency; does not bundle its own package)*
- [ ] dataset (JSON / CSV / Parquet / NPY)  *(`exp_18` trajectory
  data is a candidate -- see `project-zenodo-dataset-deposits`
  "Other dataset candidates"; not committed)*
- [ ] research-artefact (interactive viz, notebook collection, web demo)
- [ ] animation (GIF / MP4 / WebM) -- standalone, not bound to a paper
  figure
- [X] audit-table CSV snapshot at release (per
  `project-zenodo-dataset-deposits` slot 2)

*In-repo artefacts (no separate DOI, co-released with the primary):*

- [X] new repo (template + junction setup)  *(`dcl-paper-03-tidal-ionization`
  already exists; junction at `external/dcl-paper-03-tidal-ionization`)*
- [ ] new subdirectory in an existing repo
- [X] new audit table (`paper/sections/audit_table.tex`)  *(seeded
  with 10 rows: 2 inherited PASS + 8 Paper III-specific STUB/PART)*
- [X] `CITATION.cff`  *(in place)*
- [X] `notes/<topic>.md` file(s)  *(see "Notes / memory entries"
  below; `notes/plasma_as_gravitational_ionization.md` already
  exists as the analytical-derivation note)*
- [X] `release_notes/README.md`  *(in place; reserved-DOI flow per
  `project-cross-repo-release-coordination`)*
- [X] `external/<name>` junction in dependent repos  *(junctions IN
  to this repo: `external/dcl` (Paper I upstream), `external/research`
  (formalisation notes), `external/dcl-core` (pinned dependency))*

*Project planning state (lives in Claude memory, not the repo):*

- [X] new memory entry: `project-paper-03-tidal-ionization`  *(does
  not exist yet; this issue motivates creating it as the
  forward-looking design entry analogous to
  `project-discrete-probability-paper`)*
- [ ] update existing memory entry: _______________________

*Coordination outputs:*

- [X] cross-repo pin bump in downstream papers  *(Paper III pins
  `dcl-core @ git+...@<version>`; the bump from a new dcl-core
  release follows `project-cross-repo-release-coordination`)*
- [X] new Zenodo Community listing / cross-listing  *(propose
  submission to **Geometric Foundations of Quantum Theory and
  Gravity** and **Quantum Gravity Research (Open Source)** at
  v1.0 deposit time, matching Papers I + II)*

**Slot in the framework** (where this subproject fits in the planned
series; pick from existing memory entries or propose a new slot)

- [ ] Proton internals (memory: `project-proton-internals-downstream`)
- [ ] Discrete-probability paper (memory:
  `project-discrete-probability-paper`)
- [ ] `dcl-formalism` package + paper (memory:
  `project-a1-formalism-package`)
- [ ] Hilbert-6th axiomatization (Paper~I follow-on \#18)
- [X] Paper~I follow-on slot (cite #__): \#1 -- *Plasma / gradient
  ionization*.  Paper III is the realisation of this follow-on
  slot; the framework's third ionization channel
  (gradient-detuning Arnold tongue) is what Paper III formalises
  and confirms numerically.  Paper~I follow-on \#10 (*Relativistic
  atoms*) is the natural extension; tracked as future follow-on.
- [ ] new slot, not in any catalogue yet (this is OK -- describe
  below): _______________________

**Motivation / load-bearing rationale**

Paper~I established that hydrogen is a joint two-session Arnold-tongue
lock-in on the bipartite octahedral lattice, and that gravitational
gradients across the bound-state size $R_1$ can break the joint
resonance when the differential detuning exceeds the tongue width
$\Delta\omega_\text{tongue}$.  Paper~III turns that observation into
a sharp, falsifiable claim:

- *Quantum Roche limit.*  The threshold mass at separation $d$ is
  $M_\text{min}(d) = \Delta\omega_\text{tongue} \cdot d^3 / R_1$ --
  the same $d^3$ scaling as the classical Roche limit, derived from a
  completely different mechanism (Arnold-tongue width instead of body
  density).
- *Atomic ISCO.*  The innermost stable atomic orbit
  $r_\text{atomic ISCO}(M)$ is an analogue of the geodesic ISCO at
  $r = 6 GM/c^2$ -- the largest $d$ at which gradient ionization
  always succeeds for the $n=1$ ground state, independent of
  temperature.
- *Two observational signatures.*  21\,cm HI inner-edge morphology
  near compact objects (temperature-independent inner boundary for
  neutral hydrogen); Fe K$\alpha$ line-profile inner edge in accretion
  disks (Fe fully ionized below the atomic ISCO regardless of
  temperature).

Worth being its own paper rather than an appendix to Paper~I
because:

- The $d^3$-scaling result is a *novel structural prediction* that
  parallels a 175-year-old classical result (Roche, 1849) and
  deserves prominent placement.
- The observational signatures are testable against existing
  astronomy data (XMM-Newton / NICER Fe K$\alpha$ profiles; 21\,cm HI
  surveys near compact objects); the comparison is the paper's
  observational hook and warrants its own discussion section.
- The third ionization channel (gradient detuning) is novel in the
  framework and needs structural exposition that Paper~I doesn't have
  room for.

**Eventual Zenodo deposit type**

- [X] paper (will be cross-listed to: *Geometric Foundations of
  Quantum Theory and Gravity*, *Quantum Gravity Research (Open
  Source)*, A=1 DCL series community)
- [ ] software (release-tag-driven; concept-DOI + per-version DOIs)
- [ ] dataset (versioned; relates to a paper deposit via
  `is supplement to`)
- [ ] other (poster / presentation / lesson):
  _______________________

Zenodo relation metadata (how this deposit relates to existing deposits
in the series):

- `is supplement to`: Paper~I (upstream of record; the bipartite
  tick-rule + clock-density mass + Arnold-tongue results)
- `is part of`: A=1 Discrete Causal Lattice series community
- `is documented by`: (primary artefact; nothing documents it
  upstream)

**Repo / location plan**

- [X] new repo (name): `dcl-paper-03-tidal-ionization`  *(already
  exists; not a new-repo provisioning step)*
- [ ] new subdirectory in existing repo:
  _______________________
- [ ] lives entirely in an existing paper repo (no new repo needed)

- Created from template?  Yes, from `dcl-paper-experiment-template`.
- Junction setup needed in dependent repos?  Junctions *into*
  this repo from upstream: `external/dcl` (Paper I), `external/research`
  (physics-research formalisation notes), `external/dcl-core`
  (pinned pip dependency).

**License plan** (default: series convention)

- [X] series default (MIT for code, CC BY 4.0 for prose)
- [ ] override: _______________________ -- reason:
  _______________________

**Audit-table plan**

For paper- and dataset-type subprojects, the audit table is first-class
and should exist from day one.

- [X] audit table from day one (paper / dataset)
- [ ] no audit table needed (artefact / formalism module)

- Initial seeded rows (already in
  `paper/sections/audit_table.tex` at v0.1):

  *Inherited from Paper~I (PASS):*

  - Hydrogen as joint two-session Arnold-tongue lock-in.
  - Gradient detuning breaks the joint resonance.

  *Paper III-specific (STUB / PART at v0.1):*

  - Quantum Roche limit $M_\text{min}(d) \cdot R_1 / d^3 =
    \Delta\omega_\text{tongue}$ (STUB; paper-text derivation
    pending).
  - $d^3$ scaling is the quantum-mechanical analogue of the
    classical Roche limit (STUB; paper-text observation pending).
  - Three ionization channels: thermal (Saha) + pressure (Pauli) +
    gradient (Arnold-tongue) (PART; analytical note exists,
    paper-text consolidation pending).
  - Numerical confirmation: $T_\text{escape}(g)$ monotonically
    decreasing, sharp drop near $g_\text{crit}$ (STUB; exp_18
    script in place from Paper~I, runtime evidence pending first
    run from this repo).
  - Tidal displacement diagnostic: electron and proton move in
    opposite $x$-directions under gradient (STUB; exp_18
    diagnostic columns exist, runtime evidence pending).
  - Atomic ISCO: innermost stable atomic orbit
    $r_\text{atomic ISCO}(M)$ (STUB; paper-text derivation pending).
  - Observational signature: 21\,cm HI inner-edge morphology near
    compact objects (STUB; paper-text comparison to surveys
    pending).
  - Observational signature: Fe K$\alpha$ line-profile inner edge
    in accretion disks (STUB; paper-text comparison to XMM /
    NICER profiles pending).

**Cross-repo dependencies**

- Requires a `dcl-core` release first?  Yes -- Paper III pins
  `dcl-core` at a specific git ref.  First Paper III deposit
  follows the first `dcl-core` deposit; see
  `project-cross-repo-release-coordination` for the reserved-DOI
  workflow (deposit dcl-core first, bump Paper III's pin and
  `CITATION.cff` reference, then deposit Paper III).
- Requires another paper / package / dataset to land first?
  Paper~I at v1.0 (done; doi:10.5281/zenodo.20078529).
- Triggers a downstream bump (`dcl-core` release that forces this
  subproject's consumers to bump)?  No -- Paper III is a leaf
  consumer.

(See memory entry `project-cross-repo-release-coordination` for the
bump-and-rebuild workflow.)

**Phased programme** (expand as the subproject matures)

- [X] Phase 1: scaffold the repo from `dcl-paper-experiment-template`;
  inherit Paper~I `exp_18`; seed audit table; provision
  `dcl-core` dependency.  *(Done at v0.1.)*
- [ ] Phase 2: write paper-text derivations for the four STUB
  "paper-text-pending" rows (quantum Roche limit, $d^3$ scaling
  observation, atomic ISCO derivation, three-channel
  consolidation).
- [ ] Phase 3: run `exp_18` g-scan from this repo; flip the two
  numerical-confirmation STUB rows to PASS / PART based on
  runtime evidence.
- [ ] Phase 4: write the observational-comparison discussion (21\,cm
  HI inner-edge; Fe K$\alpha$ inner edge); flip those STUB rows
  to PART based on whatever level of comparison the survey data
  supports.
- [ ] Phase 5: v1.0 release via reserved-DOI flow; deposit on Zenodo;
  cross-list to curated communities; arXiv submission via
  established endorsement chain.

**Notes that may be created or updated**

`notes/<topic>.md` files this subproject would create or touch -- even
stub notes that just capture the question are useful for upstream flow
to `external/research/Notes/`:

- *Existing:* `notes/plasma_as_gravitational_ionization.md` --
  analytical derivation note (inherited as the upstream-of-record
  for the gradient-detuning mechanism).
- *Planned:* `notes/quantum_roche_limit_derivation.md` -- working
  notes for the paper-text derivation of $M_\text{min}(d)$.
- *Planned:* `notes/atomic_isco.md` -- working notes for the
  atomic-ISCO derivation.
- *Planned:* `notes/observational_signatures_21cm_and_feka.md` --
  working notes mapping the framework's predictions onto existing
  survey data.

`project_*` or `feedback_*` memory entries this subproject would create
or update:

- *New:* `project-paper-03-tidal-ionization` -- the forward-looking
  design entry for Paper III; analogous to
  `project-discrete-probability-paper`.  Should cover the central
  results, the audit-row closure path, the cross-repo dependencies,
  and the load-bearing rationale (memory entries serve as the
  framework's forward-looking design doc; see
  `feedback-memory-as-functional-design`).

**Tools / resources needed** (anything not currently in hand)

- [ ] better CPU (specify): _______________________
- [ ] better GPU (specify): _______________________
- [ ] more memory / disk
- [ ] longer wall-clock budget (estimate): `exp_18` g-scan runtime
  depends on grid resolution; longer scans give cleaner
  $g_\text{crit}$ extraction but aren't blockers.
- [ ] dataset access (specify): _______________________
- [ ] subscription / paid software (specify): _______________________
- [X] collaborator with specific expertise (specify):
  observational-astronomy reviewer for the 21\,cm HI / Fe
  K$\alpha$ comparisons (the framework's structural claim is
  independent of the comparisons, but the comparisons will
  benefit from someone who knows the survey data well).
- [ ] sympy / `dcl_formalism` primitive that doesn't exist yet:
  _______________________
- [ ] new GitHub repo creation / template  *(repo already exists)*
- [ ] new Zenodo Community  *(submit to existing communities; no new
  community)*
- [ ] other: _______________________

**Dependencies / blockers**

What has to land before this subproject can productively start or be
deposited?

- `dcl-core` v0.1.0 release (currently pre-release in
  `external/dcl-core`).  Paper III's deposit follows dcl-core's per
  `project-cross-repo-release-coordination`.
- Phase 2 paper-text derivations are the main writing work; nothing
  external blocks them.
- Phase 3 numerical confirmation depends on running `exp_18` from
  this repo (script in place); not blocked.
- Phase 4 observational comparisons benefit from but do not require
  collaborator help.

**Status**

- [X] proposed (idea-stage)
- [X] scoped (this template filled in fully; motivation + deliverables
  + slot are written down)
- [X] repo / location created
- [X] first deliverable drafted  *(v0.1 in place: scaffold complete,
  audit table seeded, exp_18 inherited; paper-text derivations
  and runtime evidence pending Phase 2 + Phase 3)*
- [ ] first deposit live on Zenodo
- [ ] mature (subsequent deliverables ship on the cadence established
  here)

*(Status note: this is a retroactive draft.  The first four boxes
are checked because the corresponding work is already done.  The
remaining boxes track the path to v1.0 deposit.)*

**Additional context**

- *Retroactive subproject documentation.*  This is the second
  `new-subproject` issue filed; the first (Hilbert-6th capstone)
  was prospective ("we're going to spin this up").  Paper III is
  in-flight, so the template is being used as a *documentation*
  artefact rather than a *planning* artefact.  Filling it out is
  worth doing because (a) it gives Paper III parallel structure to
  the other subprojects on the project board, (b) it tests whether
  the `new-subproject` template fits mid-flight subprojects (good
  feedback signal -- it does, with the status-checkbox semantics
  doing the work), and (c) it surfaces the v1.0 closure path
  (Phase 2-5) explicitly enough that the deposit isn't ad hoc.
- *Paper title parallel.*  The series title pattern is *Geometry
  First* -> *Geometry Forces Physics* -> ... .  Paper III breaks
  the pattern (*Tidal Ionization of Atomic Hydrogen and the Quantum
  Roche Limit*) because the central result is a *specific
  prediction* rather than a *methodological claim*.  This is
  intentional: the "Geometry verbs Physics" pattern is reserved
  for methodological-capstone papers (I, II, the Hilbert-6th
  capstone); Paper III is a sharp-prediction paper and its title
  honours the result.
- *Observational stakes.*  The two observational signatures
  (21\,cm HI inner-edge; Fe K$\alpha$ inner edge) are the
  framework's first *concrete, falsifiable* astronomical
  predictions.  Reviewers (and the foundations / observational-
  astronomy communities) will weigh them carefully -- a clear
  miss in either signature would constitute a partial falsification
  of the gradient-detuning mechanism.  This is good (a real test
  of the framework); the audit-table treatment should be precise
  enough that the test is unambiguous.
