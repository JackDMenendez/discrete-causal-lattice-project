# discrete-causal-lattice-project

Project-tracking repository for the A=1 Discrete Causal Lattice series.

## Purpose

Use this repository to track work across the series in one place:

- Bugs in experiments, utilities, LaTeX builds.
- Enhancements to papers, experiments, utilities, formalism.
- Figure / animation requests.
- Release-coordination threads (especially the bump-and-rebuild
  workflow when `dcl-core` releases trigger downstream paper pin
  updates).

Items get filed via the issue templates under
[`.github/ISSUE_TEMPLATE/`](./.github/ISSUE_TEMPLATE/) and routed to
the project board at
<https://github.com/users/JackDMenendez/projects/6/views/1?layout_template=table>.

## Repositories tracked

| Repo | Role | Latest |
|---|---|---|
| [`dcl`](https://github.com/JackDMenendez/dcl) | Paper I -- *Geometry First* | v1.0, doi:10.5281/zenodo.20078529 |
| [`dcl-sm-derivation`](https://github.com/JackDMenendez/dcl-paper-02-sm-derivation) | Paper II -- *Geometry Forces Physics* (SM gauge derivation) | v1.0, doi:10.5281/zenodo.20240736 |
| [`dcl-generator-zoo`](https://github.com/JackDMenendez/dcl-generator-zoo) | Catalogue of the 71-dim per-site automorphism algebra | v0.1-DRAFT |
| [`dcl-paper-03-tidal-ionization`](https://github.com/JackDMenendez/dcl-paper-03-tidal-ionization) | Paper III -- quantum Roche limit / tidal ionization | v0.1 |
| [`dcl-core`](https://github.com/JackDMenendez/dcl-core) | Python engine (`dcl_core.core` + `dcl_core.core3d`) | v0.1.0-dev |
| `dcl-formalism` | sympy-extending formalism package (Paper I follow-ons #13 + #14) | *planned* |
| `physics-research` | parallel formalisation notes | *private; external* |

## Issue templates

The templates under `.github/ISSUE_TEMPLATE/` are trial balloons.

**How checkboxes work in the templates.**  `- [ ]` (with the
space between the brackets) is an unchecked box; `- [x]` is
checked.  When the issue is rendered on GitHub you can just click
the box to toggle and GitHub updates the markdown for you.  When
editing the issue body directly (no rendered view), hand-edit
`[ ]` -> `[x]` to check.  Each template starts with a one-line
reminder containing a copyable `[x]` for that purpose.

The templates share a common shape:

- A **repository selector** (which of the series repos this
  affects) so routing is crisp.
- An **audit-table impact** section where applicable -- the
  framework's PASS / PART / STUB / FAIL audit rows are first-class,
  and a regression that flips a PASS to FAIL is categorically
  different from a STUB-to-PART enhancement.
- A **dependencies / related issues** section -- the series has
  cross-repo dependencies (especially `dcl-core` releases
  triggering downstream paper bumps), and these get tracked here.

Each template:

- `bug.md` -- bug reports for experiments / utilities.
- `core-software-change.md` -- changes to `dcl-core` (pre-routed).
- `experiment-feature.md` -- new experiment or enhancement.
- `formalism-feature.md` -- formal work; new `dcl-formalism`
  modules; new definitions / theorems / sympy primitives.
- `gif-feature.md`, `image-feature.md` -- visual artifacts.
- `latex-formatting.md` -- LaTeX rendering / formatting issues.
- `paper-enhancement.md` -- paper section / appendix work.
- `release-coordination.md` -- track a release end-to-end,
  including the cross-repo bump-and-rebuild workflow.
- `research-artifact.md` -- propose a standalone research object
  (interactive visualisation, notebook, web demo, dataset, small
  tool) that is *not* tied to a single paper.  Distinct from
  `image-feature.md` / `gif-feature.md`, which are for static or
  animated artifacts bound to a specific paper / README / slide.
- `research-investigation.md` -- capture a forward-looking
  research thread that may span multiple experiments, papers,
  packages, and notes -- no single deliverable yet (e.g. proton
  internals, discrete-probability paper, Hilbert-6th
  axiomatization).  Distinct from `paper-enhancement` (which
  targets specific sections) and `experiment-feature` (which
  targets a specific `exp_NN`).
- `utility-feature.md` -- new utility script or enhancement.

**A note on shape.**  The `paper-enhancement` and
`research-investigation` templates are *planning-shaped*
(description / objectives / requirements / tools needed /
phased program / status) rather than bug-shaped.  Filling them
in is a planning exercise; expect to revisit and extend the
issue body as the work matures.  The other enhancement
templates (experiment, utility, formalism, etc.) sit somewhere
in between -- they target a specific thing but still surface
multi-objective and audit-row impact.
- `config.yml` -- disables the blank-issue path; links to the
  project board.

Open to suggestions on shape / additions / consolidations.
Especially worth weighing: migrating these from markdown templates
to **YAML Issue Forms** (real dropdowns, required-vs-optional
fields, better UX) once the workflow is stable.  The current
markdown form is easier to edit while the templates are still in
flux.

## License

This repository's templates / docs / scaffolding: same as the
series default (MIT for code, CC BY 4.0 for prose).
