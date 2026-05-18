---
name: Experiment feature
about: Propose a new experiment or enhance an experiment workflow
labels: enhancement, experiment
---

## Experiment feature

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

**Affected repository** (check one or more)

- [ ] `dcl` -- Paper I
- [ ] `dcl-sm-derivation` -- Paper II
- [ ] `dcl-generator-zoo`
- [ ] `dcl-paper-03-tidal-ionization` -- Paper III
- [ ] `dcl-core`
- [ ] other (planned / proposed): _______________________

**Repository status** (check one)

- [ ] existing
- [ ] planned (scoped; repo to be created)
- [ ] proposed (idea-stage only)

**Experiment ID**

`exp_NN_<name>` (existing) or `exp_NN_<proposed_name>` (new).
Check `src/experiments/EXPERIMENTS.md` for the next free `NN`.

**Experiment goal**

Goal, hypothesis, or research question.  One paragraph.

**Motivation**

Why this experiment is needed.  Cite the audit-table row or
follow-on catalogue entry (`external/dcl/notes/follow_on_implications.md`)
this experiment serves.

**Inputs / parameters**

Expected inputs, parameter ranges, or configuration.  Use the
Paper~I convention: `OMEGA_E`, `OMEGA_P`, `STRENGTH`, `GRID`, etc.

**Expected outputs**

- [ ] `.npy` arrays under `data/`
- [ ] stdout log under `data/<exp_id>*.log`
- [ ] figures under `paper/figures/` or `figures/`
- [ ] new audit-table row in `paper/sections/audit_table.tex`

**Metrics / evaluation**

How will the result be evaluated?  PASS / PART / FAIL criteria
specific to this experiment.

**Audit-table impact** (if applicable)

- New row?  ` [ ] yes  /  [ ] no`
- Existing row affected:
- Expected status at first run: `[ ] PASS  [ ] PART  [ ] STUB  [ ] FAIL`

**Resource estimate**

- Wall-clock per run: [e.g. 30 s, 2 hr, 24 hr]
- Hardware: [CPU only / GPU required / specific lattice grid size]
- Determinism: [seeded / non-deterministic]

**Reproducibility notes**

Anything reviewers will need to know to reproduce this
experiment from a fresh clone of the tagged release.

**Dependencies / related issues**

List dependencies, related issues, or upstream notes.

**Success criteria**

Concrete, falsifiable.  What does the experiment have to produce
for the audit row to flip to its target status?

**Additional context**

Any other context.
