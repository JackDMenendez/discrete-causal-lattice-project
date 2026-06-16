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

*Geometry Axiomatizes Physics: Hilbert's Sixth Problem from a Single
Conservation Law* -- the Hilbert-Sixth capstone paper of the A=1
Discrete Causal Lattice series.

(Working title; matches the series pattern *Geometry First*
[Paper~I] -> *Geometry Forces Physics* [Paper~II] -> *Geometry
Axiomatizes Physics* [capstone].  Alternative: *Toward Hilbert's
Sixth Problem on the A=1 Lattice* if the actual scope at writing
time is narrower than a complete resolution; decision waits on the
closure state of upstream audit rows.)

**Primary deliverable type** (single-select -- frames the subproject)

- [x] paper -- a new paper in the series (Zenodo deposit type: paper)
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

- [x] paper PDF + source
- [ ] software package + tagged release  *(the `dcl-formalism`
      package is its own subproject; this capstone consumes it but
      does not bundle it)*
- [ ] dataset (JSON / CSV / Parquet / NPY)
- [ ] research-artefact (interactive viz, notebook collection, web demo)
- [ ] animation (GIF / MP4 / WebM) -- standalone, not bound to a paper
      figure
- [x] audit-table CSV snapshot at release (per
      `project-zenodo-dataset-deposits` slot 2)

*In-repo artefacts (no separate DOI, co-released with the primary):*

- [x] new repo (template + junction setup)  *(`dcl-paper-XX-hilbert-sixth`;
      `XX` set at release time based on series order)*
- [ ] new subdirectory in an existing repo
- [x] new audit table (`paper/sections/audit_table.tex`)
- [x] `CITATION.cff`
- [x] `notes/<topic>.md` file(s)  *(see "Notes / memory entries"
      below)*
- [x] `release_notes/README.md`
- [x] `external/<name>` junction in dependent repos  *(junctions IN
      to this repo: `external/dcl`, `external/dcl-sm-derivation`,
      `external/dcl-paper-03-tidal-ionization`,
      `external/dcl-discrete-probability`, `external/dcl-core`,
      `external/dcl-formalism`, `external/research`)*

*Project planning state (lives in Claude memory, not the repo):*

- [x] new memory entry: `project-hilbert-sixth-capstone`
- [x] update existing memory entry: `project-a1-formalism-package`
      -- delete the nested *"Hilbert-6th design constraint"* section
      and replace it with a `[[project-hilbert-sixth-capstone]]` link;
      also update `project-zenodo-dataset-deposits` to add the
      capstone's audit-table CSV to slot 2's enumeration.

*Coordination outputs:*

- [ ] cross-repo pin bump in downstream papers  *(none -- this is the
      terminal paper in the catalogued slate)*
- [x] new Zenodo Community listing / cross-listing  *(propose
      submission to **Geometric Foundations of Quantum Theory and
      Gravity** and **Quantum Gravity Research (Open Source)** in
      parallel with the series-wide community)*

**Slot in the framework** (where this subproject fits in the planned
series; pick from existing memory entries or propose a new slot)

- [ ] Proton internals (memory: `project-proton-internals-downstream`)
- [ ] Discrete-probability paper (memory:
      `project-discrete-probability-paper`)
- [ ] `dcl-formalism` package + paper (memory:
      `project-a1-formalism-package`)
- [x] Hilbert-6th axiomatization (Paper~I follow-on \#18)
- [ ] Paper~I follow-on slot (cite #__):
      _______________________
- [ ] new slot, not in any catalogue yet (this is OK -- describe
      below): _______________________

**Motivation / load-bearing rationale**

Hilbert's sixth problem (1900): "treat in the same manner, by means
of axioms, those physical sciences in which already today mathematics
plays an important part."  The A=1 DCL programme is positioned to
address this directly because:

1. *Paper~I* establishes the substrate priority -- *geometry first*.
2. *Paper~II* derives the SM gauge group from a single conservation
   axiom -- *geometry forces physics*.
3. *The discrete-probability paper* closes the gauge-coupling
   prefactor `c` (centerpiece showcase), giving absolute values of
   `g_1`, `g_2`, `g_3` at the lattice scale.
4. *The `dcl-formalism` package* provides the operational
   realisation: axioms as first-class types, theorems as proof
   chains, continuum limits explicit -- the Hilbert-6th design
   constraint made executable.

The capstone synthesises these into the claim that *physics is
axiomatizable in the Hilbert sense from a single conservation law on
the bipartite octahedral lattice* -- i.e. that the Hilbert
programme, viewed as 124 years of unfulfilled promise, has a
substrate-first resolution.

Worth being its own paper rather than an appendix or follow-on note
because:

- It is the *methodological capstone* -- the claim that ties Paper~I's
  "geometry first" stance to a fully-fledged axiomatization, closing
  the methodological arc.
- It has its own audience (foundations community, philosophy of
  physics, mathematical physics) distinct from the
  gauge-derivation / cosmology audiences of upstream papers.
- Reviewer expectations for Hilbert-6th-shaped work are specific
  (axiom independence, completeness, consistency, continuum-limit
  verifications) and warrant a paper-shaped treatment, not folded
  into anything else.

**Eventual Zenodo deposit type**

- [x] paper (will be cross-listed to: *Geometric Foundations of
      Quantum Theory and Gravity*, *Quantum Gravity Research (Open
      Source)*, A=1 DCL series community)
- [ ] software (release-tag-driven; concept-DOI + per-version DOIs)
- [ ] dataset (versioned; relates to a paper deposit via
      `is supplement to`)
- [ ] other (poster / presentation / lesson):
      _______________________

Zenodo relation metadata (how this deposit relates to existing deposits
in the series):

- `is supplement to`: Paper I, Paper II, Paper III,
  discrete-probability paper, `dcl-formalism` package (the capstone
  synthesises across all upstream papers in the series)
- `is part of`: A=1 Discrete Causal Lattice series community
- `is documented by`: (primary artefact; nothing documents it
  upstream)

**Repo / location plan**

- [x] new repo (name): `dcl-paper-XX-hilbert-sixth` (`XX` set at
      release time -- probably the highest paper number in the
      catalogued slate)
- [ ] new subdirectory in existing repo:
      _______________________
- [ ] lives entirely in an existing paper repo (no new repo needed)
- Created from template? `dcl-paper-experiment-template`.
- Junction setup needed in dependent repos?  Junctions *into*
  this repo from upstream: `external/dcl`,
  `external/dcl-sm-derivation`,
  `external/dcl-paper-03-tidal-ionization`,
  `external/dcl-discrete-probability`, `external/dcl-core`,
  `external/dcl-formalism`, `external/research`.

**License plan** (default: series convention)

- [x] series default (MIT for code, CC BY 4.0 for prose)
- [ ] override: _______________________ -- reason:
      _______________________

**Audit-table plan**

For paper- and dataset-type subprojects, the audit table is first-class
and should exist from day one.

- [x] audit table from day one (paper / dataset)
- [ ] no audit table needed (artefact / formalism module)
- Initial seeded rows (one line each):
  - *Substrate priority* (PASS, upstream Paper~I): the discrete
    bipartite octahedral lattice is the ontological substrate.
  - *Lorentz from O_h-averaged Dirac* (PASS, upstream Paper~I).
  - *SM gauge group from single conservation axiom* (PASS, upstream
    Paper~II + discrete-probability paper).
  - *Gravity from clock-density* (PASS, upstream Paper~I).
  - *Formalism realisation* (PASS, upstream `dcl-formalism`
    package): axioms / theorems / continuum-limit primitives are
    implemented as executable types.
  - *Hilbert-6th consistency* (STUB, capstone-internal): the axiom
    set is internally consistent (no contradiction derivable).
  - *Hilbert-6th completeness* (PART, capstone-internal): every
    series-wide PASS row is a theorem derivable from the axiom set;
    enumerate the closure.
  - *Hilbert-6th independence* (STUB, capstone-internal): the
    conservation axiom is the minimal axiomatic basis (no proper
    subset of axioms yields the same theorems).
  - *Hilbert-6th continuum limit* (PART, capstone-internal):
    continuum-limit operators recover existing-physics targets;
    sympy-verified via the formalism package.
  - *Open remainder characterisation* (STUB, capstone-internal):
    any audit rows in upstream papers that remain open at capstone
    release time are explicitly characterised (derivable but not
    yet derived, vs. open question, vs. falsified).

**Cross-repo dependencies**

- Requires a `dcl-core` release first?  Yes -- the latest stable at
  capstone release time.  Pin to a specific version, not `@main`.
- Requires another paper / package / dataset to land first?
  - Papers I, II, III at v1.0+ (Papers I, II done; III in flight)
  - Discrete-probability paper at v1.0 (closure of gauge-coupling
    prefactor `c`)
  - `dcl-formalism` package at v1.0 (axiom / theorem / continuum-limit
    primitives implemented)
- Triggers a downstream bump (`dcl-core` release that forces this
  subproject's consumers to bump)?  No -- terminal paper.

(See memory entry `project-cross-repo-release-coordination` for the
bump-and-rebuild workflow.)

**Phased program** (expand as the subproject matures)

- [ ] Phase 1: outline the synthesis structure across Papers
      I -> II -> III -> discrete-probability -> `dcl-formalism`;
      identify the axiom set (probably 1: A=1 conservation on the
      bipartite octahedral lattice); draft the methodological framing
      (substrate-first -> axiomatic-completeness arc).
- [ ] Phase 2: write the *consistency* proof (no internal contradictions
      in the axiom set; sympy-verified via the formalism package).
- [ ] Phase 3: write the *completeness* statement (the audit-row
      enumeration: every series-wide PASS is a theorem derivable from
      the axiom set; cross-references close into the capstone).
- [ ] Phase 4: write the *continuum-limit* verification (continuum-limit
      operators recover existing-physics targets; sympy-verified).
- [ ] Phase 5: write the *independence* proof (the conservation axiom
      is minimal -- no proper subset yields the same theorems); may
      reduce to a one-line statement depending on the actual minimality
      of the axiom set at capstone-writing time.
- [ ] Phase 6: deposit on Zenodo (reserved-DOI flow per
      `project-cross-repo-release-coordination`); cross-list to the
      curated communities; arXiv submission via established endorsement
      chain.

**Notes that may be created or updated**

`notes/<topic>.md` files this subproject would create or touch -- even
stub notes that just capture the question are useful for upstream flow
to `external/research/Notes/`:

- `notes/hilbert_sixth_synthesis_arc.md` -- tracks how each upstream
  paper's PASS rows fold into the capstone's claim
- `notes/hilbert_sixth_axiom_set.md` -- the precise statement of the
  axiom set
- `notes/hilbert_sixth_consistency.md` -- consistency-proof working
  notes
- `notes/hilbert_sixth_completeness.md` -- completeness-proof working
  notes
- `notes/hilbert_sixth_independence.md` -- independence-proof working
  notes
- `notes/hilbert_sixth_continuum_limit.md` -- continuum-limit-verification
  working notes

`project_*` or `feedback_*` memory entries this subproject would create
or update (memory entries serve as the framework's forward-looking
design doc; see `feedback-memory-as-functional-design`):

- *New:* `project-hilbert-sixth-capstone` -- this subproject's
  forward-looking design entry (vision / closure path / audit-row
  positioning / load-bearing rationale).
- *Update:* `project-a1-formalism-package` -- delete the nested
  *"Hilbert-6th design constraint"* section; replace with a
  `[[project-hilbert-sixth-capstone]]` link.
- *Update:* `project-zenodo-dataset-deposits` -- add the capstone's
  audit-table CSV to slot 2's enumeration.

**Tools / resources needed** (anything not currently in hand)

- [ ] better CPU (specify): _______________________
- [ ] better GPU (specify): _______________________
- [ ] more memory / disk
- [ ] longer wall-clock budget (estimate): non-trivial sympy sessions
      for continuum-limit verification at large `N` may benefit from
      hours-scale runs; not a blocker.
- [ ] dataset access (specify): _______________________
- [ ] subscription / paid software (specify): _______________________
- [x] collaborator with specific expertise (specify): a
      mathematical-physics reviewer with foundations / Hilbert-programme
      familiarity (Sorkin, MacKay candidates from
      `project-arxiv-endorsement-outreach`)
- [x] sympy / `dcl_formalism` primitive that doesn't exist yet: the
      entire axiom / theorem / continuum-limit primitive set
      (operationalised in the `dcl-formalism` package; this capstone
      consumes those primitives -- it does not build them).
- [x] new GitHub repo creation / template
- [ ] new Zenodo Community  *(submit to existing communities; no new
      community)*
- [ ] other: _______________________

**Dependencies / blockers**

What has to land before this subproject can productively start or be
deposited?

- Discrete-probability paper must close the gauge-coupling prefactor
  `c` (currently planned; closure path documented in
  `project-discrete-probability-paper`).
- `dcl-formalism` package must be implemented with the axiom /
  theorem / continuum-limit primitives (currently planned; design
  constraints documented in `project-a1-formalism-package`).
- All upstream papers' open audit rows must close *or* the capstone
  must explicitly characterise the open remainder (handled by the
  "open remainder characterisation" audit row above).

**Status**

- [x] proposed (idea-stage)
- [ ] scoped (this template filled in fully; motivation + deliverables
      + slot are written down)
- [ ] repo / location created
- [ ] first deliverable drafted
- [ ] first deposit live on Zenodo
- [ ] mature (subsequent deliverables ship on the cadence established
      here)

*(Status note: this draft fills in the template fully, but the
provisioning hasn't been done.  Once memory entry
`project-hilbert-sixth-capstone` exists and this issue is filed,
status moves to `scoped`.  Status moves to `repo / location created`
when the new `dcl-paper-XX-hilbert-sixth` repo is provisioned per
`project-new-subproject-provisioning-skill`.)*

**Additional context**

- *Title decision.*  The series pattern *Geometry First* ->
  *Geometry Forces Physics* -> *Geometry Axiomatizes Physics* makes
  the three-paper methodological arc visually obvious in any
  citation list; the verb progression (*First* -> *Forces* ->
  *Axiomatizes*) tells the methodological story without prose.
  "From a Single Conservation Law" in the subtitle mirrors Paper~II
  exactly, signalling "we did it again, with one more increment of
  generality."
- *Boldness tradeoff.*  "Resolution of Hilbert's Sixth" is a
  124-year-old promise; reviewers will weigh the title against the
  paper's content carefully.  The series-pattern title anchors the
  boldness in the methodological arc rather than asserting in
  isolation -- which feels earned by the upstream work rather than
  claimed.  If actual scope at writing time is narrower than a
  complete resolution, the safe-hedge title is *Geometry Axiomatizes
  Physics: Toward Hilbert's Sixth Problem on the A=1 Lattice*.
- *Provisioning is the test case.*  This will be the first
  `new-subproject` issue filed.  The provisioning of the
  `dcl-paper-XX-hilbert-sixth` repo will exercise the playbook in
  `project-new-subproject-provisioning-skill` for the first time;
  manual provisioning notes from that exercise will inform the
  eventual skill.
