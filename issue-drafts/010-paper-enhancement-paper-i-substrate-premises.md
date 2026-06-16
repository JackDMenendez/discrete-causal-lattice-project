## 10 Paper enhancement

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

> *Origin (2026-06-09):* surfaced while hardening the essay
> [*A frozen design, in plain sight*](https://geometryinducedphysics.org/essays/posts/2026-06-09-frozen-design-in-plain-sight/)
> against the retrodiction charge. Two independent critiques converged on
> the same gap: the essay's **minimality** leg leans on Paper I's
> coordination-six claim being a clean, premise-explicit result — and on
> inspection it is **not**. The essay was softened to match what Paper I
> actually proves; this issue is to bring Paper I itself up to standard.

**Affected paper**

- [x] `dcl` -- Paper I (*Geometry First*)
- [ ] `dcl-sm-derivation` -- Paper II
- [ ] `dcl-generator-zoo`
- [ ] `dcl-paper-03-tidal-ionization`

**Description**

Make the substrate's structure **premise-explicit**. As written, Paper I:

- **§2.1** *posits* the six basis vectors as a definition ("The six
  directions of causal adjacency define the basis vectors…");
- **§2.2** describes the bipartite RGB/CMY split as happening "naturally";
- **§2.6** asserts, in one conditional prose sentence, that the structure
  is "the unique solution for $\mathbb{Z}^3$ with coordination number six"
  — *given* coordination six and a split into chirally-opposite triples —
  with **no theorem and no proof**;
- **`conclusion.tex` (~L563)** says coordination six is "forced by the
  bipartite octahedral geometry," which is **circular** (forced by the
  structure that already has coordination six).

The forcing is therefore **premise-relative**: even granting the §2.6
uniqueness, the choice merely relocates into the premises (coordination
six; *chirally-opposite triples*), which are posited, not derived. The
"chirally-opposite" premise is the seam — it is the requirement that most
looks chosen to deliver spinors.

**Objectives** (what success looks like)

- [ ] State **every** substrate premise explicitly, and for each, mark it
      *forced-from-a-deeper-premise* or *posited* — no circular "forced by
      the geometry."
- [ ] Resolve the uniqueness claim one of two ways: **(A)** upgrade it to a
      genuine premise-explicit **theorem** (six cube-diagonal directions as
      the unique $\mathbb{Z}^3$ coordination-six bipartite-chiral solution,
      premises stated and defended), or **(B)** honestly **soften** §2.6 to
      "posited / motivated" and drop the overclaim.
- [ ] De-circularize the `conclusion.tex` "forced by the bipartite
      geometry" line.
- [ ] Defend the `chirally-opposite` premise as forced or minimal — or
      concede it as a stated design choice.

**Requirements**

- [ ] new audit-table row(s): _n/a (structural/foundational, not an
      experiment row)_
- [ ] update existing audit-table row(s): _n/a_
- [x] new paper section / appendix: *(if path A)* an appendix with the
      uniqueness proof and its premises.
- [x] revise existing section: `octahedral_substrate.tex` §2.1, §2.2, §2.6;
      `conclusion.tex` (de-circularize coordination-six).
- [ ] reorganise paper structure
- [ ] new figure or animation
- [x] new note in `notes/`: a premise-audit / uniqueness-derivation note.
- [ ] new experiment
- [ ] new utility
- [ ] new bibliography entry
- [ ] new / updated `CITATION.cff` reference
- [ ] other

**Sections that may be updated**

- `paper/sections/octahedral_substrate.tex` (§2.1 definition, §2.2
  bipartite, §2.6 prior-work uniqueness sentence).
- `paper/sections/conclusion.tex` (the circular "forced by the bipartite
  geometry" line).

**Notes that may be created or updated**

- New: `notes/substrate_premises_and_coordination_six.md` — enumerate the
  premises, mark forced vs. posited, and either sketch the uniqueness proof
  or record that it is posited. Flows upstream to
  `physics-research/Notes/`.
- Possible: a companion note on the **colour-3 = space-3** identification —
  does anything *checkable* follow from it (a candidate bite), or is it a
  coincidence called principle?

**Audit-table impact**

- New audit row? `[ ]` yes / `[x]` no — foundational, not an experiment.
- Existing rows affected: none directly, but the substrate underlies every
  row; the *minimality* defense of the whole `PASS` wall depends on this.
- [ ] Regression flag — not a PASS→FAIL change; this is a rigor upgrade.

**Tools / resources needed**

- [ ] none beyond the author's time — *(path A may want a short
      combinatorial enumeration to confirm uniqueness over $\mathbb{Z}^3$
      coordination-six bipartite-chiral configurations.)*

**Motivation**

The program's strongest answer to the retrodiction charge is the
**three-leg** argument (freeze + minimality + novel predictions). The
*minimality* leg's force depends on the substrate being drawn from a small,
honestly-stated premise space. Right now the essay is **more candid about
this than Paper I is** — Paper I asserts a uniqueness it does not prove and
contains a circular "forced" line. Closing that gap makes both the paper and
the essay airtight, and (path A) could convert the program's biggest design
choice into a theorem.

**References / related material**

- Essay: *A frozen design, in plain sight* (committed `f8fb086` on the
  website repo; the premise-honest revision).
- `physics-research/Notes/` — the δp_min / discriminating-delta notes share
  the "lead with un-suppressed, premise-independent claims" heuristic.
- Scope note `008` (lattice dimensional family) — the premise regress and
  the colour/space question connect there.

**Dependencies / related issues**

- Relates to `008` (dimensional family; colour-as-space-vs-internal). No
  hard blocker; this is foundational cleanup that strengthens everything
  downstream.

**Status**

- [x] proposed (idea-stage)
- [ ] scoped
- [ ] in progress
- [ ] paused

**Additional context**

Path B (soften) is the safe, immediate fix and keeps the paper honest. Path
A (prove) is the high-value outcome — a uniqueness theorem would make
"coordination six is forced" a citable result the essay could lean on fully.
Decide A vs. B before the next Paper I revision/deposit.
