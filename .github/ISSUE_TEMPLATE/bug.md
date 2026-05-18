---
name: Bug report (experiment or utility)
about: Report a bug in an experiment or utility workflow
labels: bug
---

## Bug report

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

**Affected repository** (check one or more)

- [ ] `dcl` -- Paper I (*Geometry First*, doi:10.5281/zenodo.20078529)
- [ ] `dcl-sm-derivation` -- Paper II (*Geometry Forces Physics*, doi:10.5281/zenodo.20240736)
- [ ] `dcl-generator-zoo` -- 71-dim per-site automorphism catalogue
- [ ] `dcl-paper-03-tidal-ionization` -- Paper III (quantum Roche limit), v0.1
- [ ] `dcl-core` -- Python engine (v0.1.0-dev)
- [ ] `dcl-formalism` -- sympy-extending formalism package (planned)
- [ ] `discrete-causal-lattice-project` -- this meta / project repo
- [ ] `physics-research` -- formalisation notes (external)
- [ ] other: _______________________

**Repository version**

- Repo: ``
- Commit / tag: ``
- Date observed: ``

**Experiment ID** (if applicable)

`exp_NN_<name>` from `src/experiments/`.

**Describe the bug**

Clear and concise description of what the bug is.

**To reproduce**

Steps to reproduce:

1. Initial parameters (`OMEGA_E`, `STRENGTH`, `GRID`, etc.):
2. Experiment / utility invoked:
3. ...

**Data produced** (attach or paste)

- [ ] `.npy` files
- [ ] figures
- [ ] PDF
- [ ] LaTeX output
- [ ] stdout logs

**Logs / stdout / stack trace**

```text
(paste here)
```

**Audit-table impact** (if applicable)

- Affected row(s) in `paper/sections/audit_table.tex`:
- Status change: `<old>` -> `<new>` (`PASS` / `PART` / `STUB` / `FAIL`)
- [ ] **Regression flag**: this changes a previously-`PASS` row to `FAIL` (treat as critical)

**Environment**

- OS: [Windows / macOS / Linux]
- Python: [e.g. 3.12.4]
- Shell / build tool: [e.g. MSYS2 UCRT64, latexmk]

**Additional context**

Any other context, screenshots, or prior-art issues to link.
