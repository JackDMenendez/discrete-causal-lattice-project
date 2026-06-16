## Research investigation

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

A *research investigation* is a forward-looking thread that may
span multiple experiments, papers, packages, and notes.  It is
**not** a single deliverable -- the eventual output may be one
paper, several papers, a section of an existing paper, an audit
row, a new module, a memory entry, or some combination, and
which one isn't known yet.

> *Origin (2026-06-07):* this scoping note crystallised out of a
> reader's question on the essay
> [*Six of eight: is the causal lattice a sparse slice?*](https://geometryinducedphysics.org/essays/posts/2026-06-07-six-of-eight/)
> The essay's footnote already concedes that the higher-dimensional
> "family" is **not formally stated** and points to "a planned paper";
> this is the draft scoping of that planned work.

**Investigation title**

*The lattice's dimensional family -- formally defining the higher-$D$
generalisation of $\mathbb{T}^3_\diamond$, and resolving the colour /
space duality between the geometric (Paper I) and matrix (Paper II)
pictures.*

**Research question / hypothesis**

How should the higher-dimensional "diamond family" of the A=1 lattice be
**formally defined**, and is the natural generalisation *spatial* or
*internal*?

Two observations sharpen the question.

1. **Two generalisation knobs, not one.**
   - *Spatial* -- add spatial axes. A $D$-cube reading keeps $D$ of its
     $2^{D-1}$ body-diagonal pairs (coordination $2D$); a simplex reading
     uses the $(D{+}1)$-vertex $D$-simplex (the literal crystallographic
     "diamond", coordination $D{+}1$). They already diverge at 4D: the
     tesseract's 16 corners vs. the 5-cell's 5 vertices.
   - *Internal* -- keep 3 spatial dims and grow the matrix. The six
     causal directions factor as
     $\mathbb{C}^2_{\text{chirality}} \otimes \mathbb{C}^3_{\text{colour}}
     = \mathbb{C}^6$ (6×6 operators); Paper II extends this to
     $\mathbb{C}^{12} = \mathbb{C}^2 \otimes \mathbb{C}^2 \otimes
     \mathbb{C}^3$ and finds the SM gauge algebra inside a 71-dim
     symmetry. This is a *tower of internal representations*, not bigger
     lattices.

2. **The colour / space duality.** In Paper I the colour $\mathbb{C}^3$
   is *spent as the three spatial axes* (RGB = the spatial gamma
   directions $\gamma^1,\gamma^2,\gamma^3$). In Paper II the same
   $\mathbb{C}^3$ stays *internal* and carries $SU(3)$. **Is this one
   $\mathbb{C}^3$ wearing two hats, or two $\mathbb{C}^3$'s identified by
   a projection?** The six direction-vectors have rank 3 in
   $\mathbb{R}^3$, so the map from the $\mathbb{C}^6$ (matrix) object to
   the 3D (lattice) object is a **projection with a 3-dimensional
   kernel** -- a literal Plato's-cave shadow, with gauge content
   potentially hiding in the kernel the shadow can't show. This is
   consistent with Paper II's symmetry (71-dim) being *larger* than the
   geometry alone reveals.

Central hypothesis to test: the spatial family and the internal tower are
**projections of a single parent object**, and "which family is physical"
is really "what is the parent, and what does the 3D lattice project away?"

**What's known so far** (upstream from existing papers / notes / memory)

- **Paper I** -- $\mathbb{T}^3_\diamond$ basis vectors
  $V_1{=}(1,1,1), V_2{=}(1,-1,-1), V_3{=}(-1,1,-1)$ and negatives;
  RGB/CMY = chirality $\psi_R/\psi_L$; RGB = the spatial gamma
  directions; **coordination six is the unique solution for
  $\mathbb{Z}^3$** (`octahedral_substrate.tex` §2.6), so 3D is *special*,
  not a sampled member. Optical axis
  $V_1{+}V_2{+}V_3 = (1,1,-1)$ is exactly the cube body-diagonal pair the
  lattice omits (6 of 8 corners).
- **Paper II** -- extended amplitude
  $\mathbb{C}^{12} = \mathbb{C}^2 \otimes \mathbb{C}^2 \otimes
  \mathbb{C}^3$; discrete-Hermitian centralizer
  $\mathfrak{su}(6) \oplus \mathfrak{su}(6) \oplus \mathfrak{u}(1)$
  (dim 71); SM gauge algebra recovered as the *factor-product
  projection*; colour $SU(3)$ dynamically generated on the
  $\mathbb{C}^3$.
- **Plato's Cave essay** -- the higher-$D$ diamond family and **spectral
  dimension $d_s$** (return-probability / spreading law of the induced
  walk) as the discriminator measurable "from inside the cave."
- **Six-of-eight essay** -- the 6-of-8 cube-diagonal observation and the
  footnote conceding the family is unfixed.
- **`dcl-generator-zoo`** -- catalogue of the 71-dim per-site
  automorphism algebra (Paper II companion).

**What's unknown** (the productive gaps)

- [ ] **Which spatial generalisation** -- cube-diagonal vs. simplex (they
      differ already at 4D). Do they have different spectral dimensions?
- [ ] **Spatial vs. internal** -- independent knobs, or projections of one
      parent? Is the internal tower (Paper II) the "real" family and the
      spatial picture a low-rank shadow?
- [ ] **Colour: spatial or internal?** One $\mathbb{C}^3$ or two? Fully
      characterise the $\mathbb{C}^6 \to \mathbb{R}^3$ projection and its
      3-dim kernel; does the kernel carry the gauge content?
- [ ] **Spectral dimension** $d_s$ of each candidate member -- *an*
      observable discriminator.
- [ ] **Pixelation scaling** (from a probability floor $\delta p_\min$) --
      a **second, independent** discriminator. With an integer-token floor,
      higher-$D$ members spread probability thinner across more directions
      and hit the one-token floor *sooner*, so interference / coherence
      pixelation **coarsens with dimension**. Arguably more directly
      observable than $d_s$ (it lives in interference contrast, not
      random-walk asymptotics), and runnable *now* on the integer-token
      engine. See the essay *Is probability pixelated?* and the δp_min
      thread (`005`).
- [ ] **Uniqueness in higher $D$** -- Paper I's uniqueness is specific to
      $\mathbb{Z}^3$ / coordination six; is there an analogous
      uniqueness criterion that *selects* a higher-$D$ member, or are
      they non-unique?

**Connection to existing artefacts** (where this thread plugs in)

- Essays: [Six of eight](https://geometryinducedphysics.org/essays/posts/2026-06-07-six-of-eight/)
  (and its footnote), [Plato's Cave and the DCL projector](https://geometryinducedphysics.org/essays/posts/2026-05-23-platos-cave-and-the-projector/).
- Papers: Paper I (§2 substrate, uniqueness), Paper II (the $\mathbb{C}^{12}$
  centralizer / factor-product projection -- the internal-tower anchor).
- Subprojects: `dcl-mathematics` foundations repo (`004`) is the natural
  formal home; the Hilbert-Sixth capstone (`001`) is the place a
  unified parent object would land axiomatically.
- Claim map: the optical-axis predictions (`STUB`) are downstream of which
  family is correct.

**Expected eventual output** (one or more -- the shape may evolve)

- [x] the **"planned paper"** the six-of-eight footnote already promises --
      a formal definition of the family (spatial axis + internal tower)
      and the projection relating them.
- [x] a `dcl-mathematics` note / module formalising the
      $\mathbb{C}^6 = \mathbb{C}^2 \otimes \mathbb{C}^3$ factoring and the
      $\mathbb{C}^6 \to \mathbb{R}^3$ projection.
- [ ] an experiment computing $d_s$ for candidate members (cube vs.
      simplex; 3D vs. 4D) on `dcl-core`.
- [ ] possible new audit rows / a `claim-map` update if a member is
      selected.
- [ ] an essay reporting the resolution (and replacing the footnote's
      open admission).

**Investigation program** (phased plan; expand as the thread matures)

1. **Formalise the two knobs.** Write down the spatial family (cube-diagonal
   *and* simplex constructions, $D=2,3,4$) and the internal tower
   ($\mathbb{C}^6 \to \mathbb{C}^{12} \to \dots$) explicitly.
2. **Characterise the projection.** Make the $\mathbb{C}^6 \to \mathbb{R}^3$
   map and its 3-dim kernel precise; ask whether colour-as-space and
   colour-as-$SU(3)$ are one $\mathbb{C}^3$ or two identified by it.
3. **Discriminators (two, independent).** For candidate members compute
   both (a) the **spectral dimension** $d_s$ (random-walk asymptotics, the
   Plato's-cave observable) and (b) the **pixelation scaling** under a
   probability floor $\delta p_\min$ (interference / coherence grain vs.
   dimension). The integer-token engine (`dcl-core` v0.2.1+) makes the
   pixelation test runnable directly — discrete A=1 vs. continuum, and at
   varying $D$.
4. **Selection / unification.** Test the "single parent" hypothesis; decide
   whether a uniqueness criterion picks a member, and whether the spatial
   and internal families unify.

**Notes that may be created or updated**

- New: `dcl-mathematics` note on the dimensional family + the colour/space
  projection.
- Update: the six-of-eight essay footnote (resolve or sharpen) once the
  construction is fixed.
- Memory: a project memory slug `lattice-dimensional-family` mirroring this.

**Tools / resources needed** (anything not currently in hand)

- `dcl-core` walk/return-probability tooling for spectral-dimension
  estimates (may need a small new utility).
- `dcl-mathematics` formal scaffolding (repo `004`, may not exist yet).

**Dependencies / blockers**

- Builds on Paper II's centralizer algebra (the internal-tower anchor).
- Not blocking any shipped result; the optical-axis predictions remain
  `STUB` regardless. This is foundational / forward-looking.

**Status**

`proposed` -- scoping draft from a 2026-06-07 discussion. Not filed on
GitHub yet.

**Additional context**

Prompted by the public, explorable unit-cell 3D model and a reader's
question about it -- a concrete instance of the open/explorable workflow
turning outside engagement into a research thread.
