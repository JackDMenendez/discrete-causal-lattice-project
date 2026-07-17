---
handoff: 2026-07-16-paper04-to-paper08-vacuum-prescription-question
from: dcl-paper-04 (focused)
to: dcl-paper-08 (focused)
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: [987ee7b, 842efbe, c10f138]
pr: none
status: consumed
state: in-progress
semver: n/a (paper repo; experiment scaffolding + a blocking theory question to VIII)
flags:
  - "BLOCKING THEORY QUESTION for VIII (the ask): IV's dynamical k-resolved
     induced-action extractor needs a VACUUM / MODE-FILLING PRESCRIPTION for the
     Brillouin-zone sum -- which band(s) of the 2-band NON-UNITARY Bloch transfer
     operator T(k) constitute the 'sea' whose second-order eigenphase shift is
     summed. Paper I's induced action came out GEOMETRIC (holonomy, no explicit
     sea sum), so the prescription must be the one that reproduces the geometric
     (P, Q_B) blocks. This is a THEORY choice, not a numerics knob. IV will not
     guess it (a wrong guess could silently disagree with VIII -- the very
     red-flag the companion handoff warns against). See the question in
     'Consumer actions'."
  - "RED-FLAG-RECONCILE (inherited from 2026-07-16-paper08-paper04-companion):
     IV's engine-extracted (eps, mu^-1) must MATCH VIII's (P={1,4,4},
     Q_B={4,4,16}); a mismatch is reconciled before either deposits. IV has so
     far reproduced the null split and the block STRUCTURE, not yet the clean
     tensor from dynamics (blocked on the prescription above)."
  - "ENGINE LIMITATION (not a defect, but shapes scope): core3d has NO dynamical
     gauge field -- external_potential/vector_potential are STATIC backgrounds, so
     there is no literal propagating photon to clock. IV's 'dynamical' content is
     the A=1-survival of the induced-action anisotropy in a matter observable +
     the dispersion-solver verdict. A literal dynamical-photon dispersion would be
     a MAJOR dcl-core extension (out of scope). VIII should know this framing
     before writing its held intro/conclusion."
decisions:
  - "IV's independent deliverable re-aimed (per companion handoff + this session's
     findings): from 'extract eps' (VIII already did the static read-off + a
     numeric Fresnel sweep) to the DYNAMICAL, large-N, A=1-survival confirmation
     of (a) the null split from engine-extracted blocks and (b) the common-mode
     vacuum-speed anisotropy (single-domain factor-~2 vs O_h-restored). This is
     the non-duplicative content VIII's own caveats defer to IV. Recorded in
     paper-04 notes/exp_03_dynamical_confirmation_plan.md."
consumed_by: dcl-paper-08 (focused)
consumed_at: 2026-07-16
---

## Summary

Paper IV consumed the companion-publication handoff and started its independent
confirmation. Two IV foundations are built and validated, and IV has independently
reproduced VIII's null birefringence. But the *dynamical, large-N* extraction of
the induced-action tensor from the engine -- IV's genuinely non-duplicative
deliverable -- is blocked on one theory choice that is VIII's to make: the
vacuum/mode-filling prescription for the Brillouin-zone mode sum. This handoff
asks that question and reports IV's status + the reconcile items VIII should track.

## Shipped (paper-04, this session)

- `987ee7b` -- consume record: VIII delivered the electric block; VIII+IV are
  companion papers; supersedes the "IV v1.0 held" ruling. (CLAUDE.md)
- `842efbe` -- exp_03 dynamical-confirmation PLAN + validated foundations.
- `c10f138` -- estimator finding: the clean tensor needs the k-resolved route.

Validated foundations (in paper-04 scratchpad, to promote into `exp_03`):
- **Fresnel dispersion solver** -- independently reproduces VIII's null split:
  max |v+ - v-| = **1.8e-15** over 2000 directions; detuned control -> 0.5 split
  (a null is not a false pass); single-domain common-mode v: **1.0 on axis ->
  2.0 perp** (the factor-2 anisotropy); O_h 4-domain average -> isotropic.
- **Bloch transfer operator T(k)** for the bipartite Dirac hop -- matches the
  real engine to **6e-16**; reproduces optical-axis dispersion flatness.
- **Dynamical feasibility** (real TickScheduler, multi-tick, A=1): the induced-
  action anisotropy SURVIVES A=1 renormalization -- uniaxial about (1,1,-1),
  B axis-enhanced / E axis-suppressed (opposite senses, matching {4,4,16}/{1,4,4}).

## Verification

- Fresnel solver + Bloch operator: numeric validations above (independent of VIII's
  code). Dynamical feasibility: correct qualitative senses under the real engine.
- **Not yet verified (blocked):** a clean, nticks-independent induced-action TENSOR
  from the dynamics. Three real-space readouts (wavepacket local-phase,
  return-overlap arg<psi_0|psi_N>, uniform-state RMS phase) all show the right
  senses but their axis:perp ratio DRIFTS with nticks (B: 4.1->7.8->11.9) because
  the optical-axis dispersion flatness conflates the induced action with the free
  dispersion. Clean extraction needs the k-resolved vacuum-polarization route --
  which needs the prescription below.

## Remaining

- IV: build the k-resolved Bloch vacuum-polarization extractor
  (T(k;A) with the field as a k->k+/-q coupling; per-mode 2nd-order eigenphase
  shift; free part subtracted; BZ average -> Pi_00(q->0)->eps, Pi_ij->mu^-1),
  anchored to reproduce {4,4,16} magnetically before trusting the electric
  {1,4,4}. **Gated on the vacuum/mode-filling prescription (VIII's answer).**
- Then: engine-extracted blocks -> dispersion solver -> null + common-mode
  verdict; GPU large-N stability; acceptance tests; paper wiring.

## Decisions & flags

See frontmatter. Load-bearing: the prescription question (blocking); the
red-flag-reconcile on the blocks; and the engine-limitation framing (no dynamical
photon) VIII needs before writing its held intro/conclusion/abstract.

## -> Consumer actions (Paper VIII session)

- [ ] **ANSWER THE PRESCRIPTION QUESTION.** For a dynamical BZ mode sum over the
      2-band non-unitary Bloch transfer operator `T(k)` (one even+odd period;
      det T = -sin^2(omega/2), one physical band |lambda|~1 and one doubler
      |lambda|~sin^2(omega/2)), **which band(s) and what weighting** make the
      summed second-order field-induced eigenphase shift reproduce VIII's
      GEOMETRIC holonomy blocks `eps = P = {1,4,4}` and `mu^-1 = Q_B = {4,4,16}`?
      I.e., what is the induced action's mode-filling prescription in this
      real-time A=1 framework (Paper I got it as a pure holonomy with no explicit
      sea sum -- how does that map onto a BZ eigenphase sum)? A pointer to the
      derivation step in VIII's `electric_induced_action.py` / `electric_block.tex`
      that fixes this is sufficient.
- [ ] **Note the engine-limitation framing** (no dynamical gauge field in core3d;
      IV's "dynamical" = A=1-survival of the induced-action anisotropy, not photon
      propagation) so VIII's held intro/conclusion/abstract do not over-claim a
      literal dynamical-photon dispersion for the companion.
- [ ] **Confirm the reconcile bar:** agreement of IV's engine-extracted
      (eps, mu^-1) with VIII's (P, Q_B) to what tolerance counts as "matched" for
      the companion (structure/eigenvalues/axis, or numeric entrywise)?
- [ ] **Reply** via a return handoff to `dcl-paper-04-optical-axis-birefringence`
      (or amend this file's status once answered), so IV can unblock the extractor.
