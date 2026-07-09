# Planning: The Particle Spectrum and Particle Energies

**Type:** research-investigation planning doc (living; not a board issue yet)
**Drafted:** 2026-07-09 · PM (dcl-website session)
**Status:** DRAFT for discussion
**Companion to:** [`proton-internals-gauge-substrate.md`](proton-internals-gauge-substrate.md)
(same engine road; this doc adds *mass measurement* and the *energy-in-lattice-parameters*
discipline on top).
**Owning repos (eventual):** `dcl-core` (engine + measurement), `dcl-generator-zoo` (the
representation catalogue), `dcl-paper-02-sm-derivation` (irrep→particle map, gauge prefactor),
a future particle-spectrum / discrete-probability paper.
**Grounded in:** `dcl-generator-zoo` (71-generator catalogue), Paper II
[`notes/work_plan.md`](../../dcl-paper-02-sm-derivation/notes/work_plan.md) (Phase 4 g-ratio,
lattice scale unfixed), `dcl-core/notes/color_structure.md` (mass via chirality mixing),
`dcl-core/release_notes/v0.3.0.md` (the `dcl_core.calibration` boundary; `a = c·tick_seconds`).

---

## 1. Two senses of "zoo" — do not conflate them

- **The generator zoo** (`dcl-generator-zoo`) catalogues the **71 generators** of the per-site
  automorphism algebra on the twelve-complex-dimensional amplitude
  (chirality ⊗ isospin ⊗ colour = C² ⊗ C² ⊗ C³): stable names, (SU(3), SU(2)) irrep tags,
  bracket classes. It describes **symmetry channels / forces**, not particle masses.
  *Finishing it is a release chore:* run `generator_zoo.py`, commit the JSON + LaTeX, flip the
  Zoo-specific audit rows PART→PASS, deposit v1.0 on Zenodo. Small; nearly done.
- **The particle spectrum with energies** — this doc — is a much larger open program. A particle
  is a **state** (an irreducible multiplet), and its energy must be **measured from the
  dynamics**, not read off the algebra.

## 2. What we need to compute the energy of each particle (dependency order)

1. **Representations → particles (+ a generation index).** Map the catalogue's irrep tags to
   physical particles (which multiplet is the electron, the up-quark, …). The current C¹² is
   **single-generation**; the zoo notes that three generations require *extending the centralizer
   with additional tensor factors*. The families are not yet in the state space.
2. **Full internal structure running in the engine.** `core3d` carries only the C² chirality
   spinor today. A quark/lepton as a *dynamical state* needs the full C² ⊗ C² ⊗ C³ implemented
   and evolving — Phases 1–2 of the proton plan, generalised past colour to isospin.
3. **The mass mechanism, implemented and measured (the keystone).** Mass here is not a parameter:
   the claim is **chirality mixing becomes mass via clock density** (the phase oscillator). A
   particle's rest energy is a *measured gap* — implement the chirality-mixing/clock-density rule
   and read the dispersion `E² = m² + |p|²` at zero momentum. Described qualitatively; **not yet
   implemented as a measurement**.
4. **Close the gauge one-loop prefactor** (Paper II Phase 4, **PART**). The framework's first
   quantitative gauge prediction is g₃²/g₂² = **3/2** at the lattice scale (couplings 1 : 4 : 6);
   PART→PASS needs the explicit one-loop `−Tr ln D_lat[U]` for the universal prefactor.
5. **Fix the lattice scale `1/a` from first principles** — the work plan says twice this is *not
   yet done*. Without it: dimensionless structure and ratios, never absolute MeV/GeV. This is the
   calibration question in its sharpest form (below).

Item 3 is the keystone; items 2–3 are the same C¹²-in-`core3d` build the proton plan needs, so
masses and the proton bound state come out of one engine road.

## 3. The organizing discipline: express every energy in lattice parameters

**Every computed energy must be reported in terms of the lattice's own parameters, with the
physical-unit value a derived reading — not the primary result.** This is the
"counting is a discovery, seconds are a decision" rule applied to energy.

### 3.1 The lattice energy quantum

The lattice has exactly one natural energy scale. With the tick duration `tick_seconds` (the
single calibration debt) and the lattice spacing `a`, tied by the light-cone identity
`a = c · tick_seconds` (`c` measured, not a debt), define

> **E₀ = ħ / tick_seconds = ħc / a**   (ħ measured CODATA, not a debt).

Call E₀ the **lattice energy quantum** (the "tick energy").

### 3.2 The canonical form

Every energy the engine computes is required to take the form

> **E = E₀ · Ê**,  with **Ê a pure number** —

a dimensionless function of dimensionless lattice quantities:

- lattice momentum times spacing, `k · a`;
- the per-tick **chirality-mixing angle** (the "mass angle" — what rest mass *is* in lattice terms);
- the phase-clock winding `omega` (radians per tick);
- the token budget `N` (equivalently δp_min = 1/N);
- dimensionless coupling ratios (e.g. g₃²/g₂² = 3/2).

### 3.3 Why this is the whole game

- **Ê is the discovery** — counted/derived from the lattice, containing no imported number.
- **E₀ carries the single decision** — and since ħ and c are measured, the **only** free number in
  any energy anywhere is `tick_seconds` (equivalently `a`). This is the one-debt thesis expressed
  for energy.
- **Mass ratios are pure numbers.** `E_i / E_j = Ê_i / Ê_j` — the E₀ cancels — so **mass ratios
  need no calibration at all**; they are pure discoveries. Only *absolute* masses invoke E₀. This
  is the rigorous form of "ratios before absolutes," and the natural first falsifiable target
  (the analogue of the g₃²/g₂² = 3/2 ratio, which is likewise E₀-independent).

### 3.4 Reporting / provenance rule

An energy result is emitted as its **lattice-parameter expression `Ê`** (symbolic where possible)
**plus the `E₀` multiplier** — never as a bare joule/eV number. Each energy is then
self-documenting about which part was counted and which was the one imported scale. This mirrors
what the code already does: `core3d` keeps `omega` (radians/tick) as the primary quantity and
[`dcl_core.calibration`](../../dcl-core/src/dcl_core/calibration.py)'s `energy_joule = ħ · omega /
tick_seconds` as the derived reading. The discipline makes that pattern universal.

*Implementation hint (for the eventual dcl-core work):* an energy return type that carries both
the dimensionless `Ê` (and its lattice-parameter provenance) and the `E₀` conversion, so the SI
value is always a method call on a lattice-frame object, never a stored constant. The existing
one-debt CI tripwire in `test_calibration_boundary.py` guards the invariant that E₀ introduces no
*second* free number.

## 4. How the discipline shapes the engine road

- **Mass mechanism (item 3) must output `Ê`.** The chirality-mixing/clock-density measurement is
  required to yield the dimensionless mass angle (and hence Ê at zero momentum), not a joule
  number. The SI mass is `E₀ · Ê` computed at the boundary.
- **Dispersion tests already fit.** `test_continuum_limit` checks `E² = m² + |p|²`; expressed in
  lattice parameters this is `Ê² = Ê_m² + (k·a)²`-shaped — all dimensionless, all counted.
- **Spectrum work reports ratios first.** Mass-ratio predictions (E₀-independent) are the first
  deliverable and are falsifiable without ever fixing `a`.
- **Absolute spectrum waits on item 5.** Whether the lattice can *predict* `a` (hence E₀) from
  first principles, rather than importing it, is the open question that decides whether absolute
  masses are discoveries or a single decision.

## 5. Open questions

1. **Does the framework fix `a` / E₀ from first principles?** If not, absolute energies carry
   exactly one imported number (`tick_seconds`) and mass *ratios* carry none — state this plainly.
2. **The mass angle's origin.** Is the per-tick chirality-mixing angle a free input per particle,
   or is it itself derived (from clock density, token structure, generation index)? If derived,
   even absolute masses become counted once E₀ is fixed.
3. **Generation index.** Which added tensor factor produces three families, and does it change the
   71-generator centralizer count?
4. **Gauge prefactor (item 4).** Closing Phase 4 to PASS gives the universal `c` that turns
   coupling ratios into absolute couplings — a parallel "ratios then absolutes" story on the gauge
   side.

## 6. Pointers

- Companion: [`proton-internals-gauge-substrate.md`](proton-internals-gauge-substrate.md)
  (the C¹²-in-`core3d` engine road these energies ride on).
- Catalogue: `dcl-generator-zoo/README.md`, `src/utilities/generator_zoo.py`.
- Gauge ratio + unfixed scale: Paper II `notes/work_plan.md` Phase 4.
- Mass mechanism: `dcl-core/notes/color_structure.md`.
- Calibration boundary + `a = c·tick_seconds`: `dcl-core/release_notes/v0.3.0.md`,
  `dcl-core/src/dcl_core/calibration.py`.
