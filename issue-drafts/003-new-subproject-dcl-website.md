## New subproject

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

> *Non-paper subproject:* the `new-subproject` template is paper-shaped
> by default.  This issue fills it out for a *public-website* artifact
> instead, marking paper-only fields ("audit-table plan", certain
> Zenodo-relation rows) **N/A** and adding website-specific sections
> ("Site information architecture", "Hosting / DNS plan", "Theming /
> visual design plan").  Per the README, that adaptation is expected
> for non-paper artifacts.

> *Retroactive draft on the repo side:* the empty GitHub repository
> [`dcl-website-geometry-induced-physics-org`](https://github.com/JackDMenendez/dcl-website-geometry-induced-physics-org)
> already exists (junctioned at `external/dcl-website`).  This issue
> documents the scaffold-then-publish plan; status starts at `repo
> created, scaffold in flight` once the initial Quarto scaffold is
> pushed.

A *new subproject* is a new releasable thing in the series.  Releasable
means it eventually earns its own Zenodo DOI, repo, or other stable
handle and is consumed by something downstream (a paper, a reader, a
sibling subproject).

For modifying an existing paper, use `paper-enhancement`.  For an
early-stage research thread whose deliverable shape isn't decided yet,
use `research-investigation`.  For a specific interactive / explorable
artifact, use `research-artifact` directly.

**Subproject title**

*A=1 Discrete Causal Lattice -- Public Website* -- a series-wide news,
publications, and collaboration-surface website.  Working domain
(inferred from the repo name -- confirm at scaffold time):
`geometryinducedphysics.org`.  Repo:
`dcl-website-geometry-induced-physics-org`.

The site is the *public-facing surface* of the A=1 DCL series.  It
serves three audiences: (1) readers / reviewers who arrive from
arXiv, Zenodo, or citation trails and want a unified entry-point to
the series; (2) prospective collaborators / endorsers who need a
crisp summary of where the work is, what's open, and how to reach
in; (3) the principal investigator and any future co-authors, as a
news / status board that mirrors the project board without requiring
a GitHub login.

**Primary deliverable type** (single-select -- frames the subproject)

- [ ] paper -- a new paper in the series (Zenodo deposit type: paper)
- [ ] software package -- a new pip-installable / importable package
      (Zenodo deposit type: software)
- [ ] dataset -- structured, machine-readable, citable data
      (Zenodo deposit type: dataset; see memory entry
      `project-zenodo-dataset-deposits`)
- [ ] research-artifact -- standalone interactive / explorable object
      (Zenodo deposit type: software or other; see also
      `research-artifact.md` for artifact-specific scoping)
- [ ] formalism module -- a `dcl_formalism` module (Hilbert-6th-shaped:
      axioms / theorems / continuum-limit primitives; see memory entry
      `project-a1-formalism-package`)
- [x] other: **public website / showcase surface**.  Not a single
      releasable scientific artifact -- a long-lived hosting surface
      that *surfaces* the series' releasable artifacts (papers,
      packages, datasets, research-artifacts already DOI'd via
      Zenodo).  The site itself does not earn a separate Zenodo DOI
      under the current plan; individual interactive research-artifacts
      hosted on the site may still earn their own DOIs via the
      `research-artifact` template.

**Deliverables** (full set this subproject will produce -- check all
that apply, including secondary artifacts co-produced with the primary)

*Citable artifacts (each may earn its own Zenodo DOI):*

- [ ] paper PDF + source
- [ ] software package + tagged release
- [ ] dataset (JSON / CSV / Parquet / NPY)
- [ ] research-artifact (interactive viz, notebook collection, web demo)
      *(none at scaffold time; the site is the **host** for future
      research-artifacts.  Each artifact hosted on the site that earns
      its own DOI goes through the `research-artifact` template
      separately -- the site does not bundle them as one citable
      thing.)*
- [ ] animation (GIF / MP4 / WebM) -- standalone, not bound to a paper
      figure
- [ ] audit-table CSV snapshot at release  **N/A (no audit table; see
      "Audit-table plan" below)**

*In-repo artifacts (no separate DOI, co-released with the primary):*

- [x] new repo (template + junction setup)  *(`dcl-website-geometry-induced-physics-org`
      already exists, empty; this scaffold is its first commit.  Junctioned
      at `external/dcl-website` in this project-tracking repo.)*
- [ ] new subdirectory in an existing repo
- [ ] new audit table (`paper/sections/audit_table.tex`)  **N/A**
- [x] `CITATION.cff`  *(modest -- cites the website itself as a
      living document; primarily exists to give crawlers a canonical
      author + URL anchor.)*
- [x] `notes/<topic>.md` file(s)  *(content-source notes -- see
      "Notes / memory entries" below)*
- [ ] `release_notes/README.md`  *(no versioned releases; the site is
      continuously deployed from `main`.)*
- [x] `external/<name>` junction in dependent repos  *(no inbound
      junctions from papers/packages -- the website **consumes** the
      paper repos via their public Zenodo / GitHub URLs, not via
      junctions.  An outbound junction from this project-tracking
      repo into the website repo at `external/dcl-website` already
      exists.)*

*Project planning state (lives in Claude memory, not the repo):*

- [x] new memory entry: `project-dcl-website` -- forward-looking
      design entry (IA / content plan / theming / hosting / cadence).
- [x] update existing memory entry: top-level series-tracking entry
      (whichever entry catalogs the repos -- add `dcl-website` to
      it so future conversations know the website exists alongside
      the paper / package repos).

*Coordination outputs:*

- [ ] cross-repo pin bump in downstream papers  *(N/A -- the website
      consumes papers, not the other way around)*
- [ ] new Zenodo Community listing / cross-listing  *(the site **links
      to** the existing series community; it does not create a new
      one)*

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
- [x] new slot, not in any catalog yet (this is OK -- describe
      below): **public-communication surface for the series.**  Not
      a scientific deliverable -- an outreach / coordination /
      news-broadcast surface that complements the project board.
      Analogous in role to the Zenodo community listing or an
      arXiv-author-page, but author-controlled and visually rich
      (3D models, image galleries, articles, reviews).

**Motivation / load-bearing rationale**

Why this subproject is worth being its own releasable thing rather than
folded into an existing artifact:

1. *No existing artifact in the series is shaped to serve external
   readers.*  Papers earn DOIs and live on Zenodo / arXiv; the project
   board lives on GitHub; memory entries are private.  None of these
   present a curated, visually-rich, narrative entry-point for the
   series.

2. *The series is now multi-paper with cross-references between
   subprojects.*  At one paper, the Zenodo landing page is enough.
   At five+ planned subprojects with explicit cross-references
   (Paper~I -> Paper~II -> Paper~III -> discrete-probability ->
   `dcl-formalism` -> Hilbert-Sixth capstone), an entry-point that
   shows the arc *as an arc* is load-bearing for readers who arrive
   mid-series.

3. *Some series content does not fit a paper format.*  3D models of
   the bipartite octahedral lattice, generator-zoo visualizations,
   animations of Arnold-tongue lock-in / unlock, and short
   methodological essays / reviews -- all are valuable as
   communication artifacts but not appropriate as paper figures or
   as standalone research-artifact deposits.  The website is the
   natural home for these.

4. *Collaboration / endorsement reach-in needs a public surface.*
   Per `project-arxiv-endorsement-outreach`, the series is in active
   outreach to reviewers and collaborators (Sorkin, MacKay, et al.).
   A polished public-facing page strengthens that reach-in: it shows
   the work is part of an ongoing program, not a one-off
   pre-print.

5. *Funding-partner attribution needs a visible home.*  The series'
   funding partners (current and future) need an attribution
   surface that isn't buried in paper acknowledgements.

**Eventual Zenodo deposit type**

- [ ] paper
- [ ] software (release-tag-driven; concept-DOI + per-version DOIs)
- [ ] dataset (versioned; relates to a paper deposit via
      `is supplement to`)
- [x] other: **no Zenodo deposit for the site itself.**  The website
      is a continuously-published web surface; archival snapshots
      are out of scope for the current plan.  Future option held
      open: deposit yearly archival snapshots to Zenodo (deposit
      type: "publication / journal article" or "other") if a
      reviewer / archive ever requires it.  Individual research-artifacts
      hosted on the site still earn DOIs through the
      `research-artifact` template separately.

Zenodo relation metadata (how this deposit relates to existing deposits
in the series):

- `is supplement to`: **N/A (no Zenodo deposit)**.  Conceptually the
  site is `is documented by` (inverse: `documents`) of every Zenodo
  deposit in the series.
- `is part of`: **N/A**
- `is documented by`: **N/A**

**Repo / location plan**

- [x] new repo (name): `dcl-website-geometry-induced-physics-org`
      *(already exists, empty; first commit is the Quarto scaffold)*
- [ ] new subdirectory in existing repo
- [ ] lives entirely in an existing paper repo (no new repo needed)
- Created from template?  No template -- bespoke Quarto scaffold,
  since no website-template repo exists in the series.  The
  scaffold *itself* may become a reusable artifact (a
  `dcl-website-template`) if a sibling site is ever needed (e.g.
  per-paper landing pages).
- Junction setup needed in dependent repos?  No inbound junctions
  needed.  The outbound junction `external/dcl-website` in this
  project-tracking repo already exists.

**License plan** (default: series convention)

- [x] series default (MIT for code, CC BY 4.0 for prose).  Site code
      (Quarto config, custom layouts, JS / CSS) is MIT; site prose /
      articles / page content is CC BY 4.0.  Each is declared in a
      separate top-level file (`LICENSE-CODE` + `LICENSE-PROSE`) so
      crawlers and reusers can resolve cleanly.
- [ ] override: _______________________ -- reason:
      _______________________

**Audit-table plan**

For paper- and dataset-type subprojects, the audit table is first-class
and should exist from day one.

- [ ] audit table from day one (paper / dataset)
- [x] no audit table needed (artifact / formalism module).  The
      website surfaces audit-table content *from upstream papers* via
      embedded summaries / links; it does not maintain its own audit
      table.  A site-quality / content-completeness checklist lives
      in `notes/site_quality_checklist.md` instead (link-rot scan,
      image-alt-text coverage, math-render spot-checks, 3D-model
      accessibility fallback).

**Site information architecture (added section -- website-specific)**

Initial sections at scaffold time (each backed by a `.qmd` listing or
content page; expand as content matures):

- [x] **Home** (`index.qmd`) -- one-screen pitch: what the A=1 DCL
      program is, the methodological arc *Geometry First* ->
      *Geometry Forces Physics* -> *Geometry Axiomatizes Physics*,
      latest news teaser, call-to-action buttons to "Papers" and
      "News".
- [x] **News** (`news/`) -- chronological listing of project updates:
      paper releases, Zenodo deposits, talk announcements, audit-row
      flips, framework-level milestones.  Each post is a `.qmd` in
      `news/posts/YYYY-MM-DD-<slug>.qmd`; the listing page renders
      newest-first.
- [x] **Papers** (`papers/`) -- one card per paper in the series with
      title, abstract, status, links (Zenodo DOI, arXiv, repo, PDF).
      Mirrors but does not replace the canonical Zenodo / arXiv
      landing pages.
- [x] **Research artifacts** (`artifacts/`) -- 3D models, animations,
      interactive viz hosted on-site or embedded from external
      hosts.  Each artifact gets its own page with description,
      provenance (which paper / which exp_NN script produced it),
      and download / interaction affordances.
- [x] **Reviews / essays** (`essays/`) -- short-form methodological
      essays and reviews: framing pieces, response-to-reviewer
      essays, retrospective notes.  Distinct from `news/` (which is
      announcement-shaped) and from papers (which are peer-review-
      shaped).
- [x] **Collaborators** (`collaborators.qmd`) -- public collaborator
      roster with bios and affiliation.  Single page at scaffold time;
      promotes to a listing if the collaborator set grows.
- [x] **Funding partners** (`funding.qmd`) -- public attribution for
      funding partners (current and future).  Single page; logo
      grid + acknowledgement prose.
- [x] **Contact / reach-in** (`contact.qmd`) -- how to get in touch
      (email, GitHub, ORCID); the "endorse / review / collaborate"
      call-to-action surface from `project-arxiv-endorsement-outreach`.
- [ ] **About / methodology** (`about.qmd`) -- deferred to a later
      milestone; the home page suffices initially.
- [ ] **Search** -- deferred; Quarto's built-in search is enabled by
      default and is sufficient until the content set warrants a
      dedicated search page.

**Hosting / DNS plan (added section -- website-specific)**

- [x] hosting: **GitHub Pages** (free, custom-domain HTTPS, builds
      via GitHub Actions on push to `main`).  Same author account as
      the paper repos.
- [x] build: **GitHub Actions workflow**
      (`.github/workflows/publish.yml`) renders the Quarto site
      and publishes via `actions/deploy-pages@v4` (no `gh-pages`
      branch; Pages **Source** = *GitHub Actions*).
- [x] domain: **`geometryinducedphysics.org`** (confirmed
      2026-05-19).  Apex domain pointed at GitHub Pages via
      `A` / `AAAA` records; `www` subdomain set to `CNAME` ->
      `<user>.github.io`.
- [x] HTTPS: GitHub Pages "Enforce HTTPS" enabled once DNS
      propagates and the cert provisioning completes.
- [x] temporary-site cutover: the existing temporary site (location
      not yet recorded -- TBD) is replaced wholesale.  DNS swap is
      the cutover; no content migration is planned (the temporary
      site is a placeholder, not a content store).

**Theming / visual design plan (added section -- website-specific)**

- [x] framework: **Quarto** (academic-publishing-first, markdown-in-git
      workflow, first-class math rendering via KaTeX / MathJax,
      built-in publication-list and blog-listing pages).
- [x] theme base: Quarto's built-in `cosmo` or `flatly` Bootstrap
      theme at scaffold time; brand-customize via `_quarto.yml`'s
      `theme:` + a `custom.scss` overlay once initial content is in.
- [x] math: **KaTeX** (Quarto default; sub-millisecond render, no
      CDN dependency at build time).  Spot-check math rendering with
      a representative formula from each paper (Paper~I clock-density
      mass, Paper~II `c`-prefactor placeholder, Paper~III quantum
      Roche limit).
- [x] 3D models: **`<model-viewer>`** web component (Google's open-
      source viewer; no proprietary dependency).  GLB / GLTF format
      with PNG poster fallback for accessibility / no-WebGL clients.
      First model: bipartite octahedral lattice unit cell (sourced
      from `dcl-core`'s visualization utilities or the
      `dcl-generator-zoo` repo).
- [x] image galleries: Quarto's built-in `layout` syntax (responsive
      grid; lightbox via Quarto extension).
- [x] color palette / typography: deferred to a "v1.0 visual polish"
      pass once initial content is in place.  Scaffold uses defaults.

**Cross-repo dependencies**

- Requires a `dcl-core` release first?  No -- the website does not
  consume `dcl-core` directly.  *(If a research-artifact ever ships
  on the site that consumes `dcl-core`, that artifact is scoped via
  the `research-artifact` template, not folded into the website
  subproject.)*
- Requires another paper / package / dataset to land first?  No --
  the website can launch with whatever set of papers exist at launch
  time and grow as papers ship.
- Triggers a downstream bump (`dcl-core` release that forces this
  subproject's consumers to bump)?  No.

(See memory entry `project-cross-repo-release-coordination` for the
bump-and-rebuild workflow.)

**Phased program** (expand as the subproject matures)

- [x] Phase 1: **scaffold**.  Quarto project skeleton, `_quarto.yml`,
      placeholder content for each IA section, GitHub Actions deploy
      workflow, MIT + CC BY 4.0 license files, README.  First commit
      + push to `main`.  *(In flight at issue-filing time.)*
- [ ] Phase 2: **content seed**.  One real news post per shipped
      paper (Paper~I, Paper~II), papers-section cards for all
      catalogd subprojects (existing + planned), placeholder
      collaborator + funding pages.
- [ ] Phase 3: **3D-model integration**.  First `<model-viewer>` page
      with the bipartite octahedral lattice unit cell.  GLB export
      pipeline from `dcl-core`'s visualization utilities documented
      in `notes/glb_export_pipeline.md`.
- [ ] Phase 4: **domain cutover**.  Confirm domain ownership, swap
      DNS, add `CNAME`, enable enforce-HTTPS, retire the temporary
      site.
- [ ] Phase 5: **visual polish**.  Brand-customize theme (palette,
      typography, hero), responsive-image audit, accessibility audit
      (alt text, keyboard nav, contrast).
- [ ] Phase 6: **artifact + essay buildout**.  Migrate or originate
      content for `artifacts/` and `essays/`; first response-to-
      reviewer essay if appropriate to the outreach state.

**Notes that may be created or updated**

`notes/<topic>.md` files this subproject would create or touch -- in
the website repo, `notes/` plays the same role it plays in paper repos
(working notes that may upstream to `external/research/Notes/`):

- *Planned:* `notes/site_quality_checklist.md` -- the link-rot /
  alt-text / math-render / 3D-model-fallback checklist (in lieu of
  an audit table; periodically rerun).
- *Planned:* `notes/glb_export_pipeline.md` -- how to export GLB
  models from `dcl-core`'s visualization utilities for `<model-viewer>`
  consumption.
- *Planned:* `notes/dns_and_https_runbook.md` -- domain ownership,
  registrar details, DNS records, certificate provisioning notes
  (registrar credentials remain out of repo; the runbook documents
  *which* records to set, not the credentials themselves).
- *Planned:* `notes/content_voice_and_audience.md` -- editorial voice
  guidance (formal / sober / methodologically-anchored; cf. the
  paper-text register).  Keeps news posts and essays consistent
  across multiple authors over time.

`project_*` or `feedback_*` memory entries this subproject would create
or update (memory entries serve as the framework's forward-looking
design doc; see `feedback-memory-as-functional-design`):

- *New:* `project-dcl-website` -- this subproject's forward-looking
  design entry (IA / content plan / theming / hosting / cadence /
  domain).  Includes the domain confirmation once verified.
- *Update:* whichever top-level series-tracking memory entry
  catalogs the repos -- add `dcl-website-geometry-induced-physics-org`
  to it.

**Tools / resources needed** (anything not currently in hand)

- [ ] better CPU (specify): _______________________
- [ ] better GPU (specify): _______________________
- [ ] more memory / disk
- [ ] longer wall-clock budget (estimate): builds are seconds; no
      compute pressure.
- [ ] dataset access (specify): _______________________
- [x] subscription / paid software (specify): **domain registration
      renewal** (already in hand for `geometryinducedphysics.org`;
      ongoing yearly cost is the only recurring expense).
- [x] collaborator with specific expertise (specify): **none required
      for the scaffold**; later phases may benefit from a designer
      for the visual-polish pass (Phase 5).
- [ ] sympy / `dcl_formalism` primitive that doesn't exist yet:
      _______________________
- [x] new GitHub repo creation / template *(repo already exists,
      empty; no provisioning needed beyond the first push)*
- [ ] new Zenodo Community
- [x] other: **Quarto CLI** installed in the build environment (local
      dev + GitHub Actions runner).  Free, open-source; published
      releases at <https://quarto.org/docs/get-started/>.

**Dependencies / blockers**

What has to land before this subproject can productively start or be
deposited?

- **Phase 1 (scaffold) has no blockers.**  Quarto + GitHub Pages are
  both immediately available; the repo exists; the domain exists.
- **Phase 3 (3D-model integration)** is blocked on a GLB export path
  from `dcl-core`'s visualization utilities -- either an existing
  one (verify) or a small pipeline to author (one-off; documented in
  `notes/glb_export_pipeline.md`).
- **Phase 4 (domain cutover)** is blocked on confirming the working
  domain (`geometryinducedphysics.org` is inferred from the repo
  name; verify) and on registrar DNS access at cutover time.

**Status**

- [x] proposed (idea-stage)
- [x] scoped (this template filled in fully; motivation + deliverables
      + slot are written down)
- [x] repo / location created  *(empty repo exists on GitHub; junctioned
      at `external/dcl-website`)*
- [ ] first deliverable drafted  *(Phase 1 scaffold in flight at
      issue-filing time; flip to `[x]` once the scaffold is on
      `main` and the GitHub Pages build is green.)*
- [ ] first deposit live on Zenodo  *(N/A under the current plan; the
      site has no scheduled Zenodo deposits.  Box stays unchecked
      indefinitely.)*
- [ ] mature (subsequent deliverables ship on the cadence established
      here)

*(Status note: the issue is `scoped` at filing time; once the scaffold
is pushed to `main` and the GitHub Actions build is green, Phase 1 is
done and the "first deliverable drafted" box flips.  Phases 2-6 ladder
forward from there; `mature` is when the news cadence and the
papers-section content are both in steady state.)*

**Additional context**

- *Why Quarto, not Hugo / Astro / WordPress.*  Quarto is purpose-built
  for academic publishing: first-class math (KaTeX / MathJax),
  citations, cross-references, executable code blocks, publication
  listings, blog-listings -- all out of the box.  It matches the
  series' existing markdown / LaTeX / git-driven authoring workflow,
  so contributing content does not require learning a new tool.
  Astro is more flexible visually but requires building the academic
  furniture yourself; Hugo's academic-theme ecosystem (post-Wowchemy)
  is fragmented; WordPress fights both the workflow and the math.

- *Why GitHub Pages, not Netlify / Cloudflare Pages.*  GitHub Pages
  is on the same account that hosts the paper repos; one less
  third-party account to manage; free; custom-domain HTTPS works.
  The only Netlify / Cloudflare advantage that would matter here
  (preview deploys per PR) is not load-bearing for a single-author
  workflow.

- *Why "other" rather than "research-artifact" as the primary
  deliverable type.*  A research-artifact in this series' usage is a
  standalone, citable, DOI-earning object -- the website is a
  *hosting surface* for such artifacts, not an artifact itself.
  Modelling it as a research-artifact would force a Zenodo deposit
  plan that doesn't apply (websites don't naturally version into
  snapshots) and would put it in the wrong category in the catalog
  (a vehicle, not a destination).

- *Optional future split.*  If the scaffold turns out to be reusable
  for sibling sites (e.g. a per-paper landing page that a publisher
  asks for), the Quarto scaffold can be promoted to a
  `dcl-website-template` repo with this site as the first
  instantiation.  No commitment at scaffold time; flag for revisit
  after the visual-polish pass.

- *Funding-partner sensitivity.*  The funding page is a public
  attribution surface.  Before each partner is listed, confirm
  their attribution preferences (named individual vs. institution
  vs. anonymised contributor) -- this is partner-specific and
  cannot be inferred from public data.
