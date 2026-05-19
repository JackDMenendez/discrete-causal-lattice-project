---
name: Paper enhancement
about: Plan a paper enhancement -- new section, appendix, audit row, figure, note, or restructure
labels: enhancement, paper
---

## Paper enhancement

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

This template plans a *modification* to an existing paper -- a new
section, appendix, audit row, figure, note, restructure, or
bibliography entry.  For:

- a *new* paper, software package, dataset, or research-artefact
  (i.e. a new releasable subproject), use `new-subproject`;
- a single visual artefact, use `image-feature` / `gif-feature` /
  `research-artifact`;
- a new experiment, use `experiment-feature`;
- an exploratory thread without a single deliverable yet, use
  `research-investigation`;
- a LaTeX rendering bug, use `latex-formatting`.

**Affected paper** (check one or more -- existing repos only; if the
target paper doesn't exist yet, use `new-subproject` instead)

- [ ] `dcl` -- Paper I (*Geometry First*)
- [ ] `dcl-sm-derivation` -- Paper II (*Geometry Forces Physics*)
- [ ] `dcl-generator-zoo` (catalogue paper)
- [ ] `dcl-paper-03-tidal-ionization` -- Paper III

**Description**

Plain-language summary of the enhancement.  What is being added,
revised, or restructured?

**Objectives** (what success looks like, as a list)

- [ ] objective 1
- [ ] objective 2
- [ ] objective 3

**Requirements** (what needs to happen for the enhancement to
land -- check any that apply, and name specifics)

- [ ] new audit-table row(s): _______________________
- [ ] update existing audit-table row(s): _______________________
- [ ] new paper section / appendix: _______________________
- [ ] revise existing section: _______________________
- [ ] reorganise paper structure
- [ ] new figure or animation
- [ ] new note in `notes/`: _______________________
- [ ] new experiment in `src/experiments/`: _______________________
- [ ] new utility in `src/utilities/`: _______________________
- [ ] new bibliography entry: _______________________
- [ ] new / updated `CITATION.cff` reference
- [ ] other: _______________________

**Sections that may be updated**

List the file paths (`paper/sections/<topic>.tex`).  Even rough
guesses are useful for scoping.

**Notes that may be created or updated**

List the `notes/<topic>.md` files this enhancement would touch.
New stub notes are fine -- they help findings flow upstream to
`external/research/Notes/` per the project's standing convention.

**Audit-table impact** (if applicable)

- New audit row?  `[ ]` yes / `[ ]` no.  If yes, draft claim line:
  _______________________
- Existing audit row(s) affected: _______________________
- Status change: `<old>` -> `<new>` (`PASS` / `PART` / `STUB` / `FAIL`)
- [ ] **Regression flag**: this changes a previously-`PASS` row to
      `FAIL` or `PART` (treat as critical)

**Tools / resources needed** (anything not currently in hand)

- [ ] better CPU (specify): _______________________
- [ ] better GPU (specify): _______________________
- [ ] more memory / disk
- [ ] longer wall-clock budget (estimate): _______________________
- [ ] dataset access (specify): _______________________
- [ ] subscription / paid software (specify): _______________________
- [ ] collaborator with specific expertise (specify): _______________________
- [ ] other: _______________________

**Motivation**

Why this enhancement matters.  Cite the upstream notes,
follow-on catalogue entries, or memory entries that motivate it.

**References / related material**

Papers, notes, issues, links.

**Dependencies / related issues**

What has to land first?  Other issues / threads to coordinate
with.

**Status**

- [ ] proposed (idea-stage)
- [ ] scoped (this template filled in fully)
- [ ] in progress
- [ ] paused (waiting on a dependency)

**Additional context**

Anything else worth recording.
