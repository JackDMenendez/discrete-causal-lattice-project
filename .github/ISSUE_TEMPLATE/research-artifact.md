---
name: Research artifact (standalone)
about: Propose a standalone research object -- interactive visualisation, notebook, web demo, dataset, tool -- not owned by a single paper
labels: enhancement, research-artifact
---

## Research artifact (standalone)

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

Use this template for a research artifact that lives as its own
*object* rather than as content inside an existing paper repo.
Examples: an interactive 3D visualisation, a Jupyter notebook
reproducing some result, a web demo, a published dataset, a small
companion tool (too small to warrant its own paper).

If the artifact is *tightly bound* to a single paper (a figure
for Section~3, a GIF for the README, a utility script in
`src/utilities/`), prefer one of: `paper-enhancement`,
`image-feature`, `gif-feature`, `utility-feature`.  If you find
yourself wanting "interactive" on one of those, you probably want
this template instead.

**Artifact type** (check any that apply)

- [ ] interactive visualisation (3D, explorable, WebGL, Plotly, ...)
- [ ] Jupyter notebook (executable narrative)
- [ ] web demo / single-page app
- [ ] dataset / data deposit
- [ ] standalone tool or library (small enough not to warrant its
      own paper)
- [ ] reference catalogue (e.g. the generator-zoo style: JSON +
      LaTeX longtable)
- [ ] tutorial / explainer
- [ ] other: _______________________

**Technology / stack** (check any that apply)

- [ ] JavaScript (Three.js, plain WebGL, D3, ...)
- [ ] Python (Plotly, ipywidgets, bokeh, manim, streamlit, ...)
- [ ] both (e.g. Python-rendered HTML with embedded JS)
- [ ] pure HTML / CSS (no scripting)
- [ ] LaTeX (printable artifact)
- [ ] other: _______________________

Specific libraries / frameworks (free text):

**Repository placement** (check one)

- [ ] new dedicated repo (proposed name): _______________________
- [ ] add to an existing repo (which?): _______________________
- [ ] add to the meta `discrete-causal-lattice-project` repo
- [ ] external host (Observable, Streamlit Community Cloud,
      Hugging Face Spaces, ...): _______________________
- [ ] decide later

**Hosting target** (where the artifact will be served from -- check
any that apply)

- [ ] GitHub Pages on the artifact's repo
- [ ] static asset committed to the artifact's repo (no hosting
      needed)
- [ ] Zenodo deposit (citeable, archival)
- [ ] linked from a paper section (which paper?): _______________________
- [ ] private / unhosted (working draft)
- [ ] other: _______________________

**Source data / inputs**

What is the artifact's underlying data or model?  Examples:
`data/exp_NN.npy`, sympy expressions, a hand-curated catalogue,
output of an external simulation, the generator-zoo JSON.

**Standalone or paper-affiliated** (check any that apply)

- [ ] standalone -- cited *by* one or more papers but not "owned"
      by any
- [ ] companion to an existing paper (which?): _______________________
- [ ] companion to a planned paper: _______________________
- [ ] preparatory exploration for an as-yet-unscoped paper

**Citation plan**

- [ ] Zenodo DOI required (citeable artifact, archival)
- [ ] `CITATION.cff` in the artifact's repo
- [ ] mentioned as a related identifier in one or more paper
      deposits
- [ ] no formal citation (informal / internal artifact)

**Success criteria**

What does the finished artifact look like?  How will a reader
*use* it?  Example: "a reader can rotate and zoom the 71-dim
Cayley graph of the per-site automorphism algebra in a browser,
with each generator labelled and clickable to surface its
catalogue entry."

**Dependencies / related issues**

List dependencies, related issues, and any upstream papers /
catalogues this artifact depends on.

**Additional context**

Any other context.  In particular, if this artifact will be
co-released with a paper or a `dcl-core` version, flag it here
so release coordination can pick it up
(see the release-coordination template).
