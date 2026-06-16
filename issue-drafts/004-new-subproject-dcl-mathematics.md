## New subproject

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

A *new subproject* is a new releasable thing in the series.  Releasable
means it eventually earns its own Zenodo DOI, repo, or other stable
handle and is consumed by something downstream (a paper, a reader, a
sibling subproject).

For modifying an existing paper, use `paper-enhancement`.  For an
early-stage research thread whose deliverable shape isn't decided yet,
use `research-investigation`.  For a specific interactive / explorable
artefact, use `research-artifact` directly.

**Subproject title**

*Foundations of the A=1 Discrete Causal Lattice: Bipartite Octahedral
Lattices in Arbitrary Dimension* -- the foundations-mathematics
supporting repository of the A=1 Discrete Causal Lattice series.
Repo: `dcl-mathematics`.

(Working title.  Alternative short form: *Mathematics of the A=1
Discrete Causal Lattice -- Foundations Toolkit*.  Title intentionally
does **not** follow the "Geometry verbs Physics" pattern of the
methodological-capstone papers -- this is a *supporting* mathematics
repository, not a methodological-claim or specific-prediction paper.)

The repo houses pure mathematics that supports the series' physics
work.  The first paper is a *foundations toolkit*: general
constructions on bipartite octahedral lattices in arbitrary
dimension -- discrete differential geometry, function spaces, discrete
measure theory, automorphism algebra in $n$-D, and the discrete-to-
continuum limit machinery that downstream papers will consume.
Boltzmann-shaped operators and the fluid (NS / Euler) limit appear as
*motivating examples* rather than as proof targets of this first
paper; their full treatment is left to subsequent papers, possibly in
this repo or in a sibling repo.

**Primary deliverable type** (single-select -- frames the subproject)

- [x] paper -- a new paper in the series (Zenodo deposit type: paper).
      *Publication decision deferred; the paper serves as the
      series' internal mathematical reference regardless of whether
      it is ever externally published.*
- [ ] software package -- a new pip-installable / importable package
      (Zenodo deposit type: software)
- [ ] dataset -- structured, machine-readable, citable data
      (Zenodo deposit type: dataset; see memory entry
      `project-zenodo-dataset-deposits`)
- [ ] research-artefact -- standalone interactive / explorable object
      (Zenodo deposit type: software or other; see also
      `research-artifact.md` for artefact-specific scoping)
- [ ] formalism module -- a `dcl_formalism` module (Hilbert-6th-shaped:
      axioms / theorems / continuum-limit primitives; see memory entry
      `project-a1-formalism-package`)
- [ ] other: _______________________

**Deliverables** (full set this subproject will produce -- check all
that apply, including secondary artefacts co-produced with the primary)

*Citable artefacts (each may earn its own Zenodo DOI):*

- [x] paper PDF + source  *(publication TBD; see Zenodo section
      below)*
- [ ] software package + tagged release  *(no code in this repo; the
      sympy operationalisation of these theorems lives in
      `dcl-formalism` per `project-a1-formalism-package`)*
- [ ] dataset (JSON / CSV / Parquet / NPY)
- [ ] research-artefact (interactive viz, notebook collection, web demo)
- [ ] animation (GIF / MP4 / WebM) -- standalone, not bound to a paper
      figure
- [x] audit-table CSV snapshot at release (per
      `project-zenodo-dataset-deposits` slot 2)  *(conditional on
      external publication; if publication is deferred indefinitely,
      this slot stays open and no snapshot is deposited)*

*In-repo artefacts (no separate DOI, co-released with the primary):*

- [x] new repo (template + junction setup)  *(`dcl-mathematics`;
      provisioned from `dcl-paper-template` via
      `project-dcl-project-repo-provisioning`)*
- [ ] new subdirectory in an existing repo
- [x] new audit table (`paper/sections/audit_table.tex`)  *(seeded
      with toolkit-internal coverage rows -- see "Audit-table plan"
      below)*
- [x] `CITATION.cff`
- [x] `notes/<topic>.md` file(s)  *(see "Notes / memory entries"
      below)*
- [x] `release_notes/README.md`
- [x] `external/<name>` junction in dependent repos  *(junctions IN
      to this repo from downstream consumers: `external/dcl`
      (foundational lattice setup), `external/research` (parallel
      formalisation notes); junctions FROM this repo into downstream
      consumers as they pin: `external/dcl-formalism` (when the
      package starts implementing these theorems),
      `external/dcl-paper-XX-hilbert-sixth` (when the capstone starts
      citing these theorems))*

*Project planning state (lives in Claude memory, not the repo):*

- [x] new memory entry: `project-dcl-mathematics` -- forward-looking
      design entry (scope / first-paper outline / coverage closure
      path / downstream-consumer roster).  See "Notes / memory
      entries" below.
- [x] update existing memory entry: `project-a1-formalism-package`
      (planned) -- when that entry is written, note that the
      *theorems* implemented as sympy primitives in `dcl-formalism`
      cite this repo as the canonical source; `dcl-mathematics`
      proves them, `dcl-formalism` operationalises them.

*Coordination outputs:*

- [ ] cross-repo pin bump in downstream papers  *(none at scaffold
      time; downstream pins land when downstream consumers start
      citing specific theorems from this repo)*
- [ ] new Zenodo Community listing / cross-listing  *(if publication
      proceeds, cross-list to **Geometric Foundations of Quantum
      Theory and Gravity** and the A=1 DCL series community)*

**Slot in the framework** (where this subproject fits in the planned
series; pick from existing memory entries or propose a new slot)

- [ ] Proton internals (memory: `project-proton-internals-downstream`)
- [ ] Discrete-probability paper (memory:
      `project-discrete-probability-paper`)
- [ ] `dcl-formalism` package + paper (memory:
      `project-a1-formalism-package`)
- [ ] Hilbert-6th axiomatization (Paper~I follow-on \#18)
- [ ] Paper~I follow-on slot (cite #__):
      _______________________
- [x] new slot, not in any catalogue yet (this is OK -- describe
      below): **foundations-mathematics support repository for the
      series.**  Distinct from `dcl-formalism` (which remains planned
      as the sympy *package* over these theorems) and from the
      Hilbert-Sixth capstone (Paper~I follow-on \#18, which
      *consumes* these theorems via `dcl-formalism`).  The slot
      exists because the series' physics papers (Boltzmann->NS work,
      the discrete-probability paper, the capstone) all need a
      shared body of theorems about bipartite octahedral lattices in
      arbitrary dimension; consolidating them in a single repo
      gives downstream papers a single citable source and prevents
      mathematical drift between papers.

**Motivation / load-bearing rationale**

Why this subproject is worth being its own releasable thing rather than
folded into an existing artefact:

1. *Shared mathematical substrate.*  Paper~I established the A=1
   bipartite octahedral lattice in its physical (3+1)-D setting and
   developed the mathematics needed for the substrate-priority
   claim.  Subsequent papers (Paper~II's gauge derivation, Paper~III's
   tidal-ionization machinery, the planned discrete-probability paper,
   the planned Hilbert-6th capstone) each use *more* of the
   underlying mathematics than Paper~I needed to expose -- and use it
   in arbitrary dimension when the lattice is treated as a
   mathematical object rather than as a substrate for a specific
   physical claim.  A single home for the foundational theorems
   prevents drift between papers and gives reviewers a single
   reference to check.

2. *Generality is a research claim.*  Extending the bipartite
   octahedral lattice from 3-D (physically motivated) to arbitrary
   dimension is a non-trivial mathematical project.  The
   automorphism algebra (71-dim per-site in 3-D, per `dcl-zoo`),
   the discrete differential calculus, the function-space machinery,
   and the discrete-to-continuum limit all need their $n$-D
   formulations spelled out.  That generality is itself worth
   stating and proving -- both as the foundation for the
   Hilbert-Sixth capstone's universality claims and as a stand-alone
   contribution to the mathematics of discrete causal structures.

3. *Boltzmann + NS is the Hilbert-Sixth on-ramp.*  Hilbert's 1900
   problem singled out Boltzmann's kinetic theory and the rigorous
   derivation of fluid equations (the Boltzmann -> Euler / Navier-
   Stokes limit) as the centerpiece of an axiomatised physics.  The
   capstone (\#18) needs the math machinery to make that limit
   rigorous on the A=1 lattice; that machinery is what this repo
   will develop.  Pulling it out of the capstone and into a
   dedicated math repo keeps the capstone focused on the
   axiomatisation claim and gives the lattice-kinetics work a
   technical home.

4. *Internal-reference value independent of publication.*  Even if
   external publication is deferred indefinitely, the repo serves
   as the series' canonical internal reference for the foundations
   mathematics -- a working monograph that downstream papers cite
   informally and that future contributors read to understand the
   shape of the toolkit.  That role is real regardless of
   peer-review status.

Worth being its own paper / repo rather than an appendix or section
in another paper because the audience (mathematical physics,
foundations community) and the level of mathematical exposition
(theorems-with-proofs in arbitrary dimension) are both distinct from
the physics papers' shape (specific predictions in physical
dimension).

**Eventual Zenodo deposit type**

- [x] paper (will be cross-listed to: *Geometric Foundations of
      Quantum Theory and Gravity*, A=1 DCL series community)
      *-- conditional on the publication decision; deposit lands
      only if the paper is externally published.  If publication
      stays deferred, no Zenodo deposit; the repo serves as the
      series' internal reference under the series-default license
      (CC BY 4.0 for prose).*
- [ ] software (release-tag-driven; concept-DOI + per-version DOIs)
- [ ] dataset (versioned; relates to a paper deposit via
      `is supplement to`)
- [ ] other (poster / presentation / lesson):
      _______________________

Zenodo relation metadata (if/when deposit happens):

- `is supplement to`: Paper~I (the source-of-record for the bipartite
  octahedral lattice in its physical setting; this repo generalises
  the mathematics to arbitrary dimension)
- `is part of`: A=1 Discrete Causal Lattice series community
- `is documented by`: (primary mathematical reference; nothing
  documents it upstream within the series)

**Repo / location plan**

- [x] new repo (name): `dcl-mathematics`
- [ ] new subdirectory in existing repo:
      _______________________
- [ ] lives entirely in an existing paper repo (no new repo needed)
- Created from template?  `dcl-paper-template` (paper-only, no
  Python / experiments).
- Junction setup needed in dependent repos?  Junctions *into* this
  repo from upstream: `external/dcl` (Paper~I, source-of-record for
  the bipartite octahedral lattice), `external/research`
  (`physics-research` formalisation notes).  Junctions *from* this
  repo into downstream consumers land as those consumers begin to
  pin specific theorems: `external/dcl-formalism` (sympy
  operationalisation), `external/dcl-paper-XX-hilbert-sixth` (the
  capstone), and any future physics papers (Boltzmann-on-lattice,
  NS-as-fluid-limit) that consume specific theorems.

**License plan** (default: series convention)

- [x] series default (MIT for code, CC BY 4.0 for prose).  This repo
      is paper-only, so the load-bearing license is CC BY 4.0 over
      the LaTeX source and rendered PDF; MIT covers any incidental
      build scripts inherited from `dcl-paper-template`.
- [ ] override: _______________________ -- reason:
      _______________________

**Audit-table plan**

For paper- and dataset-type subprojects, the audit table is first-class
and should exist from day one.

- [x] audit table from day one (paper / dataset)
- [ ] no audit table needed (artefact / formalism module)
- Initial seeded rows (one line each):

  *Inherited from Paper~I (PASS, upstream-of-record):*

  - Bipartite octahedral lattice as the substrate (3-D physical
    setting; Paper~I establishes existence and basic structure).
  - 71-dim per-site automorphism algebra in 3-D (catalogued in
    `dcl-zoo`; PASS upstream of this repo, generalisation to $n$-D
    is STUB-internal here).

  *Foundations-toolkit-internal (STUB at v0.1; the repo's coverage
  closure path is this row set):*

  - General bipartite octahedral lattice in dimension $n$:
    combinatorial definition, neighbour structure, parity / two-
    colouring (STUB; first-paper Section 1).
  - Automorphism algebra in dimension $n$: extension of the 3-D
    71-dim per-site algebra; rank / generators / commutation
    relations as a function of $n$ (STUB; first-paper Section 2).
  - Discrete differential geometry on the lattice: discrete
    exterior calculus, discrete connections / curvature, integration
    by parts (STUB; first-paper Section 3).
  - Function spaces: discrete $L^p$ / Sobolev-analogues / $\ell^p$
    on the lattice, with $n$-D scaling laws and embedding theorems
    (STUB; first-paper Section 4).
  - Discrete measure theory on the lattice: counting measures,
    Haar-analogues for the automorphism algebra, change-of-variables
    (STUB; first-paper Section 5).
  - Discrete-to-continuum limit operators: limit topology,
    convergence modes (weak / strong / distributional), consistency
    with continuum operators (STUB; first-paper Section 6 -- the
    Hilbert-Sixth on-ramp).
  - Boltzmann-shaped operators on the lattice (motivating example,
    not a proof target of the first paper): collision operator,
    H-functional, equilibrium measures (STUB; first-paper Section
    7.1).
  - Fluid (NS / Euler) limit ansatz (motivating example, not a proof
    target of the first paper): the discrete-to-continuum scaling
    that should recover the standard fluid equations from a
    lattice-Boltzmann limit (STUB; first-paper Section 7.2).

  Rows after Section 6 (Boltzmann + NS) are explicitly *motivating
  examples* -- they describe what the toolkit will support in
  subsequent papers, not what the first paper proves.

**Cross-repo dependencies**

- Requires a `dcl-core` release first?  No -- the repo is paper-only,
  no Python dependency.  *(If a future paper in the repo introduces
  numerical experiments, that would change; the first paper does
  not.)*
- Requires another paper / package / dataset to land first?  Paper~I
  at v1.0 (done; doi:10.5281/zenodo.20078529) -- as the source-of-
  record for the bipartite octahedral lattice in its physical
  setting.  Nothing else blocks the foundations toolkit's
  development.
- Triggers a downstream bump (`dcl-core` release that forces this
  subproject's consumers to bump)?  No direct bump (no package).
  Downstream consumers (`dcl-formalism`, Hilbert-6th capstone,
  future Boltzmann / NS papers) will *cite* this repo's theorems
  rather than pin a release tag; the citation form is the
  coordination surface, not a pip-pin.

(See memory entry `project-cross-repo-release-coordination` for the
bump-and-rebuild workflow -- mostly N/A here.)

**Phased program** (expand as the subproject matures)

- [ ] Phase 1: scaffold the repo from `dcl-paper-template`; seed
      audit table with the row set above; draft the first paper's
      outline; document the scope decisions (n-D generality, what's
      in / what's out, the "motivating examples vs proof targets"
      distinction).  Write `notes/dcl_mathematics_scope_and_outline.md`.
- [ ] Phase 2: write the *combinatorial-foundations* sections
      (Sections 1-2 above: lattice in $n$-D, automorphism algebra
      in $n$-D).  Flip the corresponding audit rows STUB -> PART or
      PASS as proofs land.
- [ ] Phase 3: write the *analytic-foundations* sections (Sections
      3-5 above: discrete differential geometry, function spaces,
      discrete measure theory).  Flip audit rows.
- [ ] Phase 4: write the *limit-machinery* section (Section 6: the
      discrete-to-continuum limit operators -- the Hilbert-Sixth
      on-ramp).  This is the load-bearing section for the capstone
      and the place where the most mathematical care is needed.
      Flip audit row.
- [ ] Phase 5: write the *motivating-examples* sections (Section 7.1
      Boltzmann; Section 7.2 NS / Euler).  These are framing /
      ansatz / open-problem-statement -- not full proofs.  The full
      proofs are left to subsequent papers (in this repo or in
      sibling repos).
- [ ] Phase 6: publication decision.  If yes: polish for submission,
      Zenodo deposit per `project-cross-repo-release-coordination`,
      cross-list to communities, arXiv submission via established
      endorsement chain (`project-arxiv-endorsement-outreach`).  If
      no: tag a v1.0 internal-reference cut on the repo and leave
      the Zenodo slot open; downstream consumers cite the
      internal-reference tag.

**Notes that may be created or updated**

`notes/<topic>.md` files this subproject would create or touch -- even
stub notes that just capture the question are useful for upstream flow
to `external/research/Notes/`:

- *Planned:* `notes/dcl_mathematics_scope_and_outline.md` -- the
  first paper's outline + the scope-decision record (n-D generality,
  motivating-examples-vs-proof-targets split, what gets deferred
  to sibling papers).
- *Planned:* `notes/bipartite_octahedral_lattice_n_dim.md` --
  working notes for the general-$n$ definition of the bipartite
  octahedral lattice.
- *Planned:* `notes/automorphism_algebra_n_dim.md` -- working notes
  for the $n$-D generalisation of the 3-D 71-dim per-site
  automorphism algebra (cross-reference `dcl-zoo`).
- *Planned:* `notes/discrete_differential_geometry_on_lattice.md` --
  working notes for the discrete exterior calculus / connections /
  curvature on the lattice.
- *Planned:* `notes/function_spaces_on_lattice.md` -- working notes
  for discrete $L^p$ / Sobolev-analogue / $\ell^p$ scaling and
  embedding theorems.
- *Planned:* `notes/discrete_measure_theory_on_lattice.md` -- working
  notes for counting measures, Haar-analogues, integration by parts.
- *Planned:* `notes/discrete_to_continuum_limits.md` -- working notes
  for the limit operators, convergence modes, consistency conditions
  (the Hilbert-Sixth on-ramp).
- *Planned:* `notes/boltzmann_on_lattice.md` -- motivating-example
  framing notes for the Boltzmann-shaped collision operator and
  H-functional on the lattice.
- *Planned:* `notes/fluid_limit_ansatz.md` -- motivating-example
  framing notes for the lattice-Boltzmann -> NS / Euler limit
  ansatz.

`project_*` or `feedback_*` memory entries this subproject would create
or update (memory entries serve as the framework's forward-looking
design doc; see `feedback-memory-as-functional-design`):

- *New:* `project-dcl-mathematics` -- this subproject's forward-
  looking design entry (scope / first-paper outline / coverage
  closure path / downstream-consumer roster / publication decision
  state).
- *Update (when written):* `project-a1-formalism-package` -- note
  that the *theorems* implemented as sympy primitives in
  `dcl-formalism` cite this repo as the canonical source.
  `dcl-mathematics` proves them; `dcl-formalism` operationalises
  them.
- *Update (when written):* `project-hilbert-sixth-capstone` -- add
  `dcl-mathematics` to the upstream-dependency list (the capstone's
  Hilbert-Sixth on-ramp consumes the discrete-to-continuum limit
  machinery from this repo).

**Tools / resources needed** (anything not currently in hand)

- [ ] better CPU (specify): _______________________
- [ ] better GPU (specify): _______________________
- [ ] more memory / disk
- [ ] longer wall-clock budget (estimate): _______________________
      *(paper-only; no compute pressure)*
- [ ] dataset access (specify): _______________________
- [ ] subscription / paid software (specify): _______________________
- [x] collaborator with specific expertise (specify): a
      mathematical-physics reviewer with discrete-geometry /
      discrete-PDE / kinetic-theory background.  Optional but
      valuable for Phase 4 (limit machinery) and Phase 5 (motivating
      examples).
- [ ] sympy / `dcl_formalism` primitive that doesn't exist yet:
      _______________________  *(this repo proves theorems; the
      sympy primitives over them live in `dcl-formalism`, not here)*
- [x] new GitHub repo creation / template *(`dcl-mathematics`
      provisioned from `dcl-paper-template` per
      `project-dcl-project-repo-provisioning`)*
- [ ] new Zenodo Community  *(if published, submit to existing
      communities; no new community)*
- [ ] other: _______________________

**Dependencies / blockers**

What has to land before this subproject can productively start or be
deposited?

- *Productively start:* nothing blocks Phase 1 (scaffold + outline +
  audit-table seed).  Paper~I at v1.0 is already done; that is the
  only upstream prerequisite.
- *Phase 4 (limit machinery)* benefits from but does not require
  coordination with the planned `dcl-formalism` package -- the
  sympy operationalisation is independent of the paper-text
  derivation.
- *Phase 6 (publication)* requires the publication decision itself
  (currently deferred); no external blocker beyond authorial
  decision-making and the standard arXiv endorsement /
  Zenodo deposit workflow.

**Status**

- [x] proposed (idea-stage)
- [x] scoped (this template filled in fully; motivation + deliverables
      + slot are written down)
- [ ] repo / location created  *(provisioning in flight at
      issue-filing time; user creates the GitHub repo from
      `dcl-paper-template` and runs `repo-setup.sh`, then Claude
      provisions the repo per
      `project-dcl-project-repo-provisioning` step 4)*
- [ ] first deliverable drafted
- [ ] first deposit live on Zenodo  *(conditional on the publication
      decision; the box may stay unchecked indefinitely)*
- [ ] mature (subsequent deliverables ship on the cadence established
      here)

**Additional context**

- *Relationship to `dcl-formalism` (Paper~I follow-ons \#13 + \#14).*
  The `dcl-formalism` slot remains planned and distinct.  Division of
  labour: `dcl-mathematics` *proves* the theorems (paper-text,
  $n$-D, peer-reviewable mathematics); `dcl-formalism` *operationalises*
  selected theorems as sympy primitives (executable, machine-checked,
  framework-internal).  Same body of mathematics, two different
  surfaces -- paper-text proofs vs sympy types / proof chains.  The
  capstone (\#18) consumes both: the proofs for the axiomatisation
  claim, the primitives for the executable consistency / completeness /
  continuum-limit checks.

- *Relationship to the Hilbert-Sixth capstone (Paper~I follow-on
  \#18).*  This repo is *upstream* of the capstone -- the
  discrete-to-continuum limit machinery developed here (Phase 4) is
  the technical content that the capstone synthesises into the
  Hilbert-Sixth axiomatisation claim.  The capstone does not duplicate
  the proofs; it cites them.

- *Why "Mathematics" not "Formalism" in the repo name.*  The series
  uses "formalism" for the sympy-extending operationalisation layer
  (planned `dcl-formalism` package).  "Mathematics" is broader and
  signals the paper-text proof surface -- distinguishing the
  paper-only repo (theorems with proofs in arbitrary dimension) from
  the package repo (sympy primitives over those theorems).
  Choosing different words for the two surfaces keeps the
  cross-references unambiguous.

- *Why a paper-only repo even though publication is uncertain.*
  Two reasons.  (1) Internal-reference value: the series needs a
  canonical mathematical reference, and the paper format -- theorems,
  proofs, sectioned exposition -- is the right shape for that role
  regardless of external peer review.  (2) Optionality: starting in
  paper form preserves the publication option; starting in note form
  would force a rewrite to migrate to paper form later.  The
  marginal cost of "paper-shaped from day one" is small; the cost
  of retroactively shaping working notes into a paper is large.

- *Title format break from the series pattern.*  The methodological-
  capstone papers (I, II, the planned \#18) follow *Geometry verbs
  Physics*.  Paper~III broke that pattern because it is a sharp-
  prediction paper (Roche limit + observational signatures).  This
  repo breaks the pattern for a different reason -- it is *supporting*
  work, not a methodological claim or a specific prediction.  The
  title therefore foregrounds the mathematical content (*Foundations
  of the A=1 Discrete Causal Lattice*) rather than a verb-shaped
  methodological assertion.

- *Provisioning workflow.*  This is the first prospective subproject
  to be provisioned under the `project-dcl-project-repo-provisioning`
  five-step workflow (discuss -> user creates from template -> user
  runs `repo-setup.sh` -> Claude provisions -> Claude commits / pushes).
  Manual notes from the provisioning will inform whether the workflow
  needs adjustment for paper-only repos (e.g. the `--no-venv` path
  through `repo-setup.sh`).
