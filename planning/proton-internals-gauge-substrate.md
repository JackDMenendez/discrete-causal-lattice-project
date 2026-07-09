# Planning: Proton Internals via the Gauge-Coupling Substrate

**Type:** research-investigation planning doc (living; not a board issue yet)
**Drafted:** 2026-07-09 · PM (dcl-website session)
**Status:** DRAFT for discussion
**Owning repos (eventual):** `dcl-core` (engine), `dcl-paper-02-sm-derivation` (SU(3)/colour theory), `dcl-generator-zoo` (dim-71 centralizer), a future proton-internals paper.
**Extends:** README "Planned" row *Proton internals*; memories
`project-quark-proton-engine-requirements`, `project-proton-internals-downstream`,
`paper04-gauge-structural-core3d-v030`; note `dcl-core/notes/color_structure.md`.

---

## 1. Thesis

The U(1) Peierls gauge coupling shipped in `dcl_core` **v0.3.0** is not just the
instrument for the Paper IV birefringence channel — it is the **abelian scaffold**
for the non-abelian SU(3) colour machinery that proton internals require. The link
variable, the mid-point convention, the plaquette-holonomy / Wilson-loop extractor,
the gauge-covariance (Ward) test, and the proof that A=1 survives with a field
switched on are all reusable, one-for-one, when the field is promoted from a phase
in U(1) to an element of SU(3). Building the abelian substrate out fully is therefore
the cheapest possible down-payment on the proton programme: every near-term abelian
result stands on its own **and** de-risks a specific piece of the non-abelian road.

The one-for-one correspondence the whole plan rests on:

| v0.3.0 abelian (shipped) | proton-internals non-abelian (goal) |
|---|---|
| hop link phase `exp(i A·v)` (U(1)) | SU(3) link variable `U_j` from traversal of `V_j` |
| mid-point convention `A_mid = ½(A(x)+A(x+v))` | mid-point SU(3) link (path-ordered) |
| bipartite plaquette holonomy → induced-action `Q`-tensor | non-abelian Wilson loop → colour field strength |
| gauge covariance under `A → A + ∇Λ` (Ward test) | covariance under local SU(3) `U → gUg⁻¹` |
| A=1 exact with an external field present | A=1 exact on the added colour factor |
| single background field, single particle | dynamical colour + multi-particle (3 quarks) |

## 2. What is true today (assets), and what accuracy demands we NOT claim

**Assets already in hand:**

- **Abelian substrate (v0.3.0):** Peierls hop, `uniform_B_potential`, exact induced
  `Q`-tensor from engine link holonomies (`{4,4,16}`, axis `(1,1,-1)`, reproduces
  Paper I App. B to the bit), fused GPU `hop_average` path, CPU/GPU parity.
- **Colour theory (Paper II, PASS, symbolic):** the geometric RGB vectors give only
  the abelian `Z₃` Cartan corner; real `su(3)` (dim 8) is *generated* by a **colour-
  memory tick rule** acting on a separate `C³` factor. See
  `dcl-core/notes/color_structure.md` and Paper II
  `src/utilities/su3_generation_from_colour_memory.py`.
- **Engine requirements already scoped** (memory `project-quark-proton-engine-requirements`,
  2026-06-12): (a) a **multi-particle** `core3d` session; (b) a **token structure for
  thirds** (charges ±1/3, ±2/3; colour in 3s ⇒ budget `N` divisible by 3). Coupling:
  exact thirds constrains the multi-particle budget.
- **Hardware already scoped:** the workstation-upgrade note twice names "multi-session
  (proton) work" as what the 24 GB GPU is insurance for.

**Accuracy guardrail (do not oversell):** the **gauge-sector** vacuum birefringence is
*not* a live falsifier — per memory `paper04-gauge-structural-core3d-v030`, the `O_h`
symmetry averages the operator-level `Q` anisotropy to `8·I`, so the framework
*predicts the absence* of gauge-sector birefringence; the **kinematic** channel
(dimension-6, `(a/λ)²`-suppressed) is the falsifiable one, and E+B "test #5" is the
*confirmatory numerical witness* of that averaging. Proton internals is a **separate
application** of the gauge scaffold (dynamical colour binding), not a birefringence
prediction. Keep the two stories apart in all prose.

## 3. The four pillars

Proton internals is not one gap but four, and the gauge coupling is the connective
tissue among them:

1. **Colour gauge (non-abelian).** Promote the abelian link phase to an SU(3) link
   variable — the colour analogue of the Peierls substitution. This is the binding
   force.
2. **Colour factor (Hilbert space).** Grow the per-site amplitude from the two-complex-
   dimensional chirality spinor (`C²`) to `C² ⊗ C³`, with the `su(3)` action carried by
   the colour-memory tick rule (Paper II). Pillars 1 and 2 are the two faces of colour —
   the gauge field lives on the links, the colour index lives on the sites.
3. **Token thirds.** Make the integer-token accounting carry fractional charge/colour
   (budget `N ≡ 0 mod 3`). The combinatoric `core3d` makes this unavoidable where the
   float `core` engine hid it — a feature, and a possible handle on δp_min Outcome D.
4. **Multi-particle binding.** Extend `core3d` from single-particle to an *n*-body
   session (three quarks, `uud`), plausibly a 3-session generalization of the
   Arnold-tongue joint-resonance lock-in.

## 4. Phased programme

Dependency order: **0 → 1 → {2, 3} → 4** (2 and 3 run largely in parallel once 1
lands, but 3's token budget is constrained by 2's thirds requirement).

### Phase 0 — Harden and complete the abelian substrate  *(owner: dcl-core; low risk)*
Lock the reusable primitives as first-class, tested surface, and land the near-term
abelian experiments that each stand alone yet exercise a Phase-1 dependency.

- Promote to standing tests: gauge covariance / Ward identity (`test_gauge_invariance.py`,
  already on the invariant list), A=1-under-field, holonomy extractor as a public utility.
- Near-term experiments (each a small `exp_NN`, independently publishable):
  vacuum-averaged magnetic susceptibility (design-doc-04 R4); Landau levels / cyclotron;
  Aharonov–Bohm phase around a loop; Hofstadter-type spectrum; **E+B test #5** (the
  Paper IV confirmatory witness — closes the last GPU-bound gauge item).
- **Exit gate:** link-variable + holonomy + covariance-test API is generic enough that
  swapping U(1) for a matrix group touches only the group operations, not the scheduler.

### Phase 1 — The colour factor and the SU(3) link  *(owner: dcl-core + Paper II bridge; medium risk)*
The pivot from abelian to non-abelian; the moment Paper II "starts running numerically."

- Implement the `C³` colour-memory factor (`C² → C² ⊗ C³`) and the colour-memory tick
  rule that closes to `su(3)` (Paper II PASS — but candidate-dependent; see gate).
- Generalize the abelian link to an SU(3) link variable `U_j` from traversal of `V_j`,
  wired through the geometry↔colour bridge `U_j = P_{1→j} U_1 P_{1→j}⁻¹`.
- Reuse the holonomy machinery → non-abelian Wilson loops; generalize the covariance
  test to local SU(3).
- **Exit gate:** numerical `su(3)` closure of the chosen tick rule matches Paper II's
  symbolic result; **decide which colour-memory tick rule** proton dynamics selects (or
  establish that the non-uniqueness is physical). This is a real open question, not a
  formality.

### Phase 2 — Token thirds and the colour-singlet condition  *(owner: dcl-core + Paper II + discrete-probability paper; medium risk)*
- Make the token budget carry thirds (`N ≡ 0 mod 3`; ±1/3, ±2/3), consistent with exact
  integer A=1.
- **Define the colour-singlet / baryon projector on `C³`** — currently CONJECTURED
  ("what is colourless on the lattice?"; note that `V_r+V_g+V_b = (1,1,-1)` is the
  `Z₃` Cartan shadow, *not* the singlet).
- **Opportunity:** the fractional-charge constraint is a concrete handle the discrete-
  probability paper could use to **pin δp_min** (Outcome D, left unpinned for Paper III).
- **Exit gate:** singlet projector well-posed and A=1-consistent.

### Phase 3 — Multi-particle `core3d` session  *(owner: dcl-core; high risk — major engine work)*
- Extend the single-particle engine to an *n*-body session with internal binding
  (candidate: 3-session Arnold-tongue joint-resonance lock-in).
- Honour the coupling from Phase 2: exact thirds forces the multi-particle budget to a
  multiple of 3.
- GPU-scale; this is the load-bearing consumer of the scoped 24 GB multi-session GPU.
- **Likely its own board subproject** (sibling to #9 core3d 3D-upgrade), not a single issue.

### Phase 4 — Proton bound state and confinement signature  *(owner: proton-internals paper; high risk — the payoff)*
- Assemble: three quarks (`uud`), SU(3) colour binding (Phase 1), singlet projection
  (Phase 2), *n*-body session (Phase 3) → seek a bound, confined, colour-singlet state.
- Observables to define/measure: a confinement signature (Wilson-loop area law / string
  tension analogue), and whether the colour factor has a **mass-analogue amplitude** the
  way chirality mixing becomes mass via clock density.
- This is the centrepiece of a future proton-internals paper (or the discrete-probability
  paper's showcase).

## 5. Cross-repo coordination and what to spawn

- **Bridge handoff to a Paper II / dcl-core session** for Phase 1: the `C³` colour-memory
  tick rule is Paper II's result to hand over and dcl-core's to implement; this is the
  first place Paper II gains an engine dependency (flagged in `color_structure.md`).
- **Reconciliation thread:** proton internals, the complex-`TokenResidual.carry`
  hypothesis, and the generator-zoo dim-71 centralizer "extras" may be the *same object*
  seen from different sides (color_structure.md §4). Schedule an explicit does-this-unify
  investigation rather than discovering it three times.
- **Board:** when Phase 1 is greenlit, open a **new-subproject** issue for proton internals
  (research-investigation shape, like the planned row) with per-phase sub-issues, and wire
  Phase-3 as a `core-software-change` subproject sibling to #9. Use the existing sub-issue /
  `addBlockedBy` tooling (first used for #13/#18/#20).

## 6. Why now — the opportunities this creates

- **Leverage, not greenfield:** Phases 0–1 reuse the shipped v0.3.0 scaffold; the marginal
  cost of the abelian build-out is low and each item is publishable.
- **Makes Paper II executable:** turns a symbolic PASS (the `su(3)` colour algebra) into a
  running numerical demonstration — a strong, concrete narrative for the series.
- **Unifies scattered threads:** Paper II colour, the complex-carry hypothesis, the
  generator-zoo extras, and δp_min Outcome D all touch this object; the programme is where
  they meet.
- **Hardware already aligned:** the multi-session GPU was scoped for exactly this.

## 7. Risks and non-goals

- **Deferred hard parts (design-doc-04):** fully dynamical non-abelian gauge propagation and
  the `1/g²` coupling prefactor are hard. Phases 1–2 should use a background/static colour
  field first; dynamical colour is a later increment.
- **Tick-rule non-uniqueness (Phase 1 gate):** if many colour-memory rules close to the same
  `su(3)`, decide whether proton dynamics selects one or the ambiguity is physical — do not
  paper over it.
- **Multi-particle is a big rewrite (Phase 3):** the single-particle assumption is deep in
  `core3d`; this is the largest schedule risk and the reason to bank the cheap abelian wins first.
- **Keep the two gauge stories apart:** the EM/birefringence channel (Paper IV, structurally
  null) and the colour-confinement channel (this plan) share a scaffold but make different
  claims. Never let one borrow the other's credibility.

## 8. Pointers

- Abelian substrate: `dcl-core/docs/design/04_gauge_field_and_vacuum_response.md`,
  `release_notes/v0.3.0.md`, news `news/posts/2026-07-08-dcl-core-v0-3-0.qmd`.
- Colour theory: `dcl-core/notes/color_structure.md`; Paper II
  (`dcl-paper-02-sm-derivation`) `src/utilities/automorphism_rgb_su3.py`,
  `notes/su3_generation_from_colour_memory.md`, `notes/induced_gauge_action_nonabelian.md`.
- Engine requirements: memory `project-quark-proton-engine-requirements`.
- Gauge-structural / falsifiability guardrail: memory `paper04-gauge-structural-core3d-v030`.
- Board: project 6; existing gauge items #15/#16/#17 (Paper IV), #18 (exp_03), #20 (v0.3.0 Peierls).
