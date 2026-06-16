## Research artifact (standalone)

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

Use this template for a research artifact that lives as its own
*object* rather than as content inside an existing paper repo.

> *Origin (2026-06-07):* idea raised right after shipping the explorable
> 3D models (`dcl-lattice-viewer` v0.1.0, the unit-cell and
> wavepacket artifacts). Parked as a scope note for now -- **not yet
> built.** The explorable-lattice artifact page already has a short
> "Make your own" section that this cookbook would expand and supersede.

**Artifact title**

*Build your own lattice -- a DIY cookbook for turning A=1 lattice state
into browser-explorable 3D models.*

**Artifact type** (check any that apply)

- [ ] interactive visualisation (3D, explorable, WebGL, Plotly, ...)
- [ ] Jupyter notebook (executable narrative)
- [ ] web demo / single-page app
- [ ] dataset / data deposit
- [ ] standalone tool or library
- [ ] reference catalogue
- [x] tutorial / explainer -- a recipe-style cookbook
- [ ] other: _______________________

**Technology / stack** (check any that apply)

- [ ] JavaScript (Three.js, plain WebGL, D3, ...)
- [x] Python (`dcl-lattice-viewer`, `dcl-core`, `trimesh`)
- [x] both (Python-generated `.glb`/`.html` + a `<model-viewer>` embed)
- [ ] pure HTML / CSS (no scripting)
- [ ] LaTeX (printable artifact)
- [ ] other: _______________________

Specific libraries / frameworks: `dcl-lattice-viewer` v0.1.0,
`dcl-core`, `trimesh` (unit-cell mesh), `@google/model-viewer`,
`gltf-transform` (web optimisation).

**Repository placement** (check one)

- [ ] new dedicated repo (proposed name): _______________________
- [x] add to an existing repo -- the website
      (`dcl-website-geometry-induced-physics-org`)
- [ ] add to the meta `discrete-causal-lattice-project` repo
- [ ] external host
- [ ] decide later

*Page-placement decision still open* (deferred): (a) a new
`artifacts/` cookbook page cross-linked from the explorable-lattice
page; (b) a new top-level "Cookbook"/"Guides" navbar entry; or
(c) expand the existing "Make your own" section in place.

**Hosting target** (check any that apply)

- [x] GitHub Pages on the artifact's repo (the website)
- [x] static asset committed to the artifact's repo (no hosting needed)
- [ ] Zenodo deposit
- [ ] linked from a paper section
- [ ] private / unhosted
- [ ] other: _______________________

**Source data / inputs**

`dcl-lattice-viewer demo` (synthetic wavepacket, no engine run) and
`dcl-lattice-viewer build` on a real `dcl-core` `exp_*` `.npy`/`.npz`
dump; the `trimesh` unit-cell recipe (centre node + 6 RGB/CMY
neighbours from `dcl-core`'s `RGB_VECTORS`/`CMY_VECTORS`).

**Standalone or paper-affiliated** (check any that apply)

- [x] standalone -- a how-to companion to the `dcl-lattice-viewer`
      tool and the website's 3D artifacts
- [ ] companion to an existing paper
- [ ] companion to a planned paper
- [ ] preparatory exploration for an as-yet-unscoped paper

**Citation plan**

- [ ] Zenodo DOI required
- [ ] `CITATION.cff` in the artifact's repo
- [ ] mentioned as a related identifier in a paper deposit
- [x] no formal citation (web how-to content)

**Success criteria**

A reader goes from nothing to an embedded, web-light, explorable
lattice on their own page. Proposed recipe set:

1. **Setup** -- `pip install` `dcl-core` + `dcl-lattice-viewer[glb]`.
2. **A lattice in 30 seconds** -- `demo` -> open the `.html` / view the `.glb`.
3. **Colour modes** -- `phase` / `parity` / `count`, and what each
   *reveals* (parity = the bipartite RGB/CMY split).
4. **Build the bipartite unit cell** -- the `trimesh` recipe (centre +
   6 neighbours along the real basis vectors).
5. **Render a real run** -- `build` from an `exp_*` `.npy`/`.npz` dump.
6. **Animate ticks** -- the `4D`-array `(T,nx,ny,nz)` path.
7. **Embed it on your own page** -- the `<model-viewer>` snippet **plus
   the deployment gotchas learned the hard way**: keep the `.glb` plain
   or compress with `gltf-transform`; the Draco-decoder fetch can hang a
   viewer (prefer plain or meshopt for robustness); size-tune via
   `--shape`/`--units`; expect GitHub-Pages/CDN cache lag (hard-refresh).

That last bucket is the unique value -- it's exactly the debugging the
website hit on 2026-06-07 (1.4 MB load stall, Draco hang on Edge),
written so the next person skips it.

**Dependencies / related issues**

- `dcl-lattice-viewer` v0.1.0 (the tool the cookbook teaches).
- `dcl-core` (the engine whose `.npy` fields it consumes).
- Website artifacts already shipped: `explorable-lattice.qmd`,
  `lattice-unit-cell.qmd` (the cookbook generalises both).

**Additional context**

Pure documentation -- no new science. A natural co-release item when
`dcl-lattice-viewer` cuts its next tagged version; flag for release
coordination then. Lightweight enough to build in a single pass once the
page-placement question is decided.
