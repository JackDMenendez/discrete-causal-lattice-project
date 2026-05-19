---
name: New subproject
about: Spin up a new releasable subproject -- paper, software package, dataset, research-artefact, or formalism module
labels: subproject, planning
---

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

Short phrase naming the subproject.

**Primary deliverable type** (single-select -- frames the subproject)

- [ ] paper -- a new paper in the series (Zenodo deposit type: paper)
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

- [ ] paper PDF + source
- [ ] software package + tagged release
- [ ] dataset (JSON / CSV / Parquet / NPY)
- [ ] research-artefact (interactive viz, notebook collection, web demo)
- [ ] animation (GIF / MP4 / WebM) -- standalone, not bound to a paper
      figure
- [ ] audit-table CSV snapshot at release (per
      `project-zenodo-dataset-deposits` slot 2)

*In-repo artefacts (no separate DOI, co-released with the primary):*

- [ ] new repo (template + junction setup)
- [ ] new subdirectory in an existing repo
- [ ] new audit table (`paper/sections/audit_table.tex`)
- [ ] `CITATION.cff`
- [ ] `notes/<topic>.md` file(s)
- [ ] `release_notes/README.md`
- [ ] `external/<name>` junction in dependent repos

*Project planning state (lives in Claude memory, not the repo):*

- [ ] new memory entry: _______________________
- [ ] update existing memory entry: _______________________

*Coordination outputs:*

- [ ] cross-repo pin bump in downstream papers
- [ ] new Zenodo Community listing / cross-listing

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
- [ ] new slot, not in any catalogue yet (this is OK -- describe
      below): _______________________

**Motivation / load-bearing rationale**

Why this subproject is worth being its own releasable thing rather than
folded into an existing artefact.  What downstream consumer needs it.
What it lets the framework claim that it can't claim today.

**Eventual Zenodo deposit type**

- [ ] paper (will be cross-listed to: _______________________)
- [ ] software (release-tag-driven; concept-DOI + per-version DOIs)
- [ ] dataset (versioned; relates to a paper deposit via
      `is supplement to`)
- [ ] other (poster / presentation / lesson):
      _______________________

Zenodo relation metadata (how this deposit relates to existing deposits
in the series):

- `is supplement to`: _______________________
- `is part of`: _______________________
- `is documented by`: _______________________

**Repo / location plan**

- [ ] new repo (name): _______________________
- [ ] new subdirectory in existing repo:
      _______________________
- [ ] lives entirely in an existing paper repo (no new repo needed)
- Created from template? (`dcl-paper-experiment-template` etc.):
  _______________________
- Junction setup needed in dependent repos?
  _______________________

**License plan** (default: series convention)

- [ ] series default (MIT for code, CC BY 4.0 for prose)
- [ ] override: _______________________ -- reason:
      _______________________

**Audit-table plan**

For paper- and dataset-type subprojects, the audit table is first-class
and should exist from day one.

- [ ] audit table from day one (paper / dataset)
- [ ] no audit table needed (artefact / formalism module)
- Initial seeded rows (one line each):
  _______________________

**Cross-repo dependencies**

- Requires a `dcl-core` release first?  Which version?
  _______________________
- Requires another paper / package / dataset to land first?
  _______________________
- Triggers a downstream bump (`dcl-core` release that forces this
  subproject's consumers to bump)?  Which consumers?
  _______________________

(See memory entry `project-cross-repo-release-coordination` for the
bump-and-rebuild workflow.)

**Phased program** (expand as the subproject matures)

- [ ] Phase 1: _______________________
- [ ] Phase 2: _______________________
- [ ] Phase 3: _______________________
- [ ] Phase 4: _______________________

**Notes / memory entries to create or update**

`notes/<topic>.md` files this subproject would create or touch -- even
stub notes that just capture the question are useful for upstream flow
to `external/research/Notes/`.

`project_*` or `feedback_*` memory entries this subproject would create
or update (memory entries serve as the framework's forward-looking
design doc; see `feedback-memory-as-functional-design`).

**Tools / resources needed** (anything not currently in hand)

- [ ] better CPU (specify): _______________________
- [ ] better GPU (specify): _______________________
- [ ] more memory / disk
- [ ] longer wall-clock budget (estimate): _______________________
- [ ] dataset access (specify): _______________________
- [ ] subscription / paid software (specify): _______________________
- [ ] collaborator with specific expertise (specify):
      _______________________
- [ ] sympy / `dcl_formalism` primitive that doesn't exist yet:
      _______________________
- [ ] new GitHub repo creation / template
- [ ] new Zenodo Community
- [ ] other: _______________________

**Dependencies / blockers**

What has to land before this subproject can productively start or be
deposited?

**Status**

- [ ] proposed (idea-stage)
- [ ] scoped (this template filled in fully; motivation + deliverables
      + slot are written down)
- [ ] repo / location created
- [ ] first deliverable drafted
- [ ] first deposit live on Zenodo
- [ ] mature (subsequent deliverables ship on the cadence established
      here)

**Additional context**

Anything else worth recording.  Speculative connections to other
subprojects, framing alternatives held open, risks.
