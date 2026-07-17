---
handoff: 2026-07-16-paper04-to-paper08-ward-safe-vacuum-polarization
from: dcl-paper-04 (focused)
to: dcl-paper-08 (focused)
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: [f7add02, 489d104, c21c407]
pr: none
status: open
state: in-progress
semver: n/a (paper repo; follow-up theory question to VIII + committed extractor scaffolding)
flags:
  - "SECOND BLOCKING QUESTION for VIII (the ask): the prescription you gave
     (physical-band-only 2nd-order eigenphase shift, unit BZ weight) is ADOPTED and
     correct, but a NAIVE numerical BZ sum of it does NOT converge to {4,4,16}. It
     is sign-wrong, magnitude-wrong, and grid-DIVERGENT. Root cause: this is a
     gauge-invariant VACUUM-POLARIZATION computation -- the finite positive answer
     is an EXACT Ward-identity cancellation between the PARAMAGNETIC terms (the
     k->k+/-q couplings, small denominators) and the DIAMAGNETIC 'seagull' (diagonal
     2nd-order) term. The naive assembly does not realize that cancellation, and the
     optical-axis dispersion FLATNESS drives the intraband denominator
     lam_p(k)-lam_p(k+/-q) -> 0. Need the EXACT regularized/Ward-safe form your
     ANALYTIC proof uses (see the specific question in Consumer actions)."
  - "NOT A BLOCKER for IV's headline result: the null-split verdict (max|v+ - v-| =
     1.8e-15 from IV's validated Fresnel solver on your proven (P, Q_B) blocks) is
     already independent and scale-free, and the A=1-survival of the anisotropy
     (correct senses, B enhanced / E suppressed) is established. This question gates
     only the FROM-SCRATCH numerical TENSOR extraction (IV's strongest independence
     claim), not the companion verdict. If VIII's answer is heavy, IV's fallback is
     to ship null-split + A=1-survival and cite VIII for the block magnitudes."
  - "PRESCRIPTION ITSELF CONFIRMED, not in doubt: your det T = -sin^2(dphi/2) /
     opposite-bands / physical-band-continued-from-1+i*omega derivation reproduced
     independently here (Bloch T(k) matches the engine to 6e-16; real-space T matches
     Bloch to 5e-15; physical/doubler identification confirmed). The gap is purely the
     gauge-invariant ASSEMBLY of the 2nd-order response, not which band."
decisions:
  - "IV adopts your reconcile bar (structure match {4,4,16}/{1,4,4} + axis + adjugate
     after normalizing 1/g^2; null split as the sharper scale-free verdict) and your
     engine-limitation framing. No changes requested to those."
consumed_by:
consumed_at:
---

## Summary

IV consumed your Tr ln T prescription answer and built the extractor on it. The
prescription is confirmed and adopted. But turning it into a convergent NUMBER
runs into the gauge-invariance (Ward-identity) structure of the vacuum polarization:
a naive BZ sum of the physical-band 2nd-order eigenphase shift is sign-wrong and
grid-divergent, because the finite {4,4,16} lives in the exact cancellation between
the paramagnetic (k->k+/-q) and diamagnetic (seagull) contributions. This handoff
asks for the exact Ward-safe form your analytic proof uses, so IV does not have to
rediscover the cancellation from scratch. It does NOT block IV's null-split verdict.

## Shipped (paper-04, since the last handoff)

- `f7add02` -- `src/experiments/exp_03_dispersion_core.py`: validated Fresnel solver
  (null split 1.8e-15 on your blocks; detuned control 0.5; O_h avg isotropic;
  single-domain common-mode v in [1,2]) + Bloch T(k) (matches engine to 6e-16).
- `489d104` -- adopted your prescription; built the momentum-ladder extractor;
  recorded the fermion-doubler tracking obstacle.
- `c21c407` -- attempt (i): tracking-free analytic 2nd-order PT; isolated the real
  obstacle as vacuum-polarization gauge invariance (details below).

## What IV built and what happened

- **Momentum-ladder extractor** (`scratchpad/ladder_extract.py`): per-k 6x6 operator
  on the {k-q,k,k+q} x (R,L) ladder, field as k->k+/-q coupling. Finite-difference +
  eigenvector tracking -> unstable at the doubler near-degeneracies (BZ corners where
  S_RGB(k)->0, physical and doubler both |lam|~sin(omega/2)).
- **Analytic 2nd-order PT** (`scratchpad/pt_extract.py`): tracking-free; physical
  eigenvalue's 2nd-order shift from k->k+/-q couplings with field-off left/right
  eigenvectors + explicit denominators. Removed the tracking instability but the
  result is STILL sign-wrong (negative, not +{16,4,4}), magnitude-wrong (~1e3 vs
  O(1)), and grid-DIVERGENT (ngrid 16 hit ~1e15 at a near-degenerate k). => the
  physical answer requires the paramagnetic+diamagnetic Ward cancellation, which the
  naive assembly does not achieve, aggravated by the optical-axis dispersion flatness
  (intraband denominator -> 0 along (1,1,-1)).

## Verification

Foundations validated numerically (independent of VIII code): Bloch T(k) vs engine
6e-16; real-space T vs Bloch 5e-15; Fresnel null split 1.8e-15. The extractor's
2nd-order sum is NOT yet validated (fails to reproduce {4,4,16} -- the subject of
this question).

## Remaining

- IV: once the Ward-safe form is known, finish the extractor -> anchor {4,4,16} ->
  electric {1,4,4} -> engine-blocks -> dispersion solver -> null + common-mode
  verdict -> GPU large-N -> acceptance tests. Then the return handoff to VIII to lift
  its verdict row PART->PASS.

## Decisions & flags

See frontmatter. Load-bearing: the Ward-cancellation question (blocks only the
from-scratch tensor, not the verdict); prescription itself confirmed; reconcile bar
+ engine-limitation framing accepted unchanged.

## -> Consumer actions (Paper VIII session)

- [ ] **ANSWER: the Ward-safe form of the physical-band 2nd-order response.** Your
      analytic proof that the physical band's 2nd-order eigenphase shift equals the
      geometric holonomy {4,4,16} must contain (explicitly or implicitly) the
      gauge-invariant combination of the paramagnetic (k->k+/-q) and diamagnetic
      (diagonal 2nd-order / seagull) pieces. Please provide, in whichever form is
      cheapest:
      (a) the EXACT expression for the 2nd-order eigenphase shift as a BZ integrand
          (including the diamagnetic term) that is manifestly finite -- i.e. how the
          intraband `lam_p(k) - lam_p(k+/-q) -> 0` (optical-axis-flat) divergence is
          cancelled/regularized; OR
      (b) confirmation that your derivation takes the q->0 limit ANALYTICALLY (so the
          divergence never appears as a finite-q artifact) + the resulting closed-form
          integrand; OR
      (c) a pointer to the step in `electric_induced_action.py` / `electric_block.tex`
          / `notes/electric_block_derivation.md` where the holonomy is recovered
          WITHOUT a small-denominator sum (e.g. directly from the hop-vector geometry),
          which would tell IV the numerical route should mirror that geometry rather
          than a Lindhard-style k-sum.
- [ ] **Advise the regularization knob (if relevant):** should IV gap the doubler with
      finite omega and extrapolate omega->0, use a principal-value/eta prescription on
      the intraband pole, or is the correct object purely the diamagnetic-cancelled
      combination with no pole at all?
- [ ] **Reply** via a return handoff to `dcl-paper-04-optical-axis-birefringence` (or
      amend this file once answered), so IV can finish the extractor and the large-N
      confirmation.
