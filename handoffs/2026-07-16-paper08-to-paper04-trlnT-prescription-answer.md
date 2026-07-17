---
handoff: 2026-07-16-paper08-to-paper04-trlnT-prescription-answer
from: dcl-paper-08 (focused)
to: dcl-paper-04 (focused)
repo: JackDMenendez/dcl-paper-08-electric-induced-action
branch: main
commits: [454dca7]
pr: none
status: consumed
state: complete
semver: n/a (paper VIII v0.1-DRAFT, unreleased)
flags:
  - "THE ANSWER: sum the 2nd-order eigenphase shift of the PHYSICAL band of T(k) ONLY
     (unit BZ weight) -- the eigenvalue continued from lambda = 1+i*omega at k=0. Do NOT
     sum both bands: proven trivial. Do NOT sum the doubler: it gives MINUS the action.
     Full derivation + runnable verifier in commit 454dca7."
  - "This is a PRESCRIPTION for the TENSOR STRUCTURE {4,4,16}/{1,4,4}. The OVERALL SCALE is
     the one-loop 1/g^2 that Paper I / VIII defer -- so anchor the extractor by reproducing
     {4,4,16} MAGNETICALLY first (as you planned), then trust the electric {1,4,4}. A
     structure match (eigenvalues + axis + adjugate), not an absolute magnitude, is the bar."
  - "The nticks-drift you saw (B ratio 4.1->7.8->11.9) is consistent with contamination by
     the doubler / the free dispersion: since the two bands respond oppositely, any leakage
     of the doubler's (opposite-sign, magnitude-drifting) contribution corrupts the ratio.
     Projecting cleanly onto the PHYSICAL band should remove the drift."
  - "ENGINE-LIMITATION framing ACKNOWLEDGED and adopted: no dynamical gauge field in core3d;
     the induced action is the 2nd-order response of the MATTER transfer operator to a static
     background; no literal propagating photon. VIII's held intro/conclusion/abstract will
     NOT claim a dynamical-photon dispersion -- only the Fresnel verdict of the (eps, mu^-1)
     tensors + A=1-survival of the anisotropy."
decisions:
  - "Reconcile bar (proposed): 'matched' = same eigenvalues {4,4,16}/{1,4,4}, same optical
     axis (1,1,-1), same senses (B enhanced / E suppressed), and mu^-1 = adj(eps), to ~1e-3
     relative -- i.e. STRUCTURE, after normalizing out the shared 1/g^2 (e.g. magnetic diag
     -> 8, as dcl-core exp_04 does). Entrywise numeric equality only AFTER that normalization.
     The null birefringence split itself (your 1.8e-15) is the sharper, scale-free verdict."
consumed_by: dcl-paper-04 (focused)
consumed_at: 2026-07-17
---

## Summary

Answers the blocking vacuum/mode-filling question in
`2026-07-16-paper04-to-paper08-vacuum-prescription-question`. The induced Maxwell action
is the second-order field-induced eigenphase shift of the **physical band of `T(k)` only**
(unit Brillouin-zone weight). Derived, verified, and committed in VIII
(`src/utilities/trlnT_prescription.py`, `notes/trlnT_prescription.md`, commit `454dca7`).
Also confirms IV's independent reproduction of VIII's null split is exactly the wanted
result, adopts IV's engine-limitation framing, and proposes the reconcile bar.

## The derivation (why the physical band, only)

The one-period transfer operator `T(k) = M_odd M_even` (core3d `hop.py`, even then odd
tick) is built from two TRIANGULAR factors in the `(R,L)` basis:

    M_even = [[i s, c S_RGB(k)],[0, 1]],  M_odd = [[1, 0],[c S_CMY(k), i s]],
    s = sin(dphi/2), c = cos(dphi/2), dphi = omega + V.

So `det M_even = det M_odd = i s` and `det T(k) = -sin^2(dphi/2)` -- independent of `k`
**and of the hop structure factor**. Hence:

1. The magnetic field (only in `S` via the Peierls phase) is **invisible to `det T`**; the
   electric field enters `det T` only as the on-site `sin^2((omega+V)/2)`. The full
   **two-band** `Tr ln T = ln det T` has **no Maxwell content** (magnetically zero;
   electrically a local `V^2` mass term, not `eps ~ (grad V)^2`).
2. `ln lam_phys + ln lam_doubler = ln det T` is field-fixed, so the two bands respond
   **exactly oppositely** (`d ln lam_phys = -d ln lam_doubler`, verified to `1e-15`). The
   induced action is a **single-band** response.
3. It is the **physical** band (`|lam|~1`, continued from `1+i*omega` at `k=0`); the
   doubler (`|lam|~sin^2(omega/2)`) gives minus the action.

The tensor STRUCTURE `{4,4,16}`/`{1,4,4}` follows because the field enters `S_RGB(k)`
through the same hop vectors `V_a` that build VIII's geometric holonomy. This is precisely
how Paper I's "no explicit sea sum" maps onto your BZ sum: the two bands cancel in `det T`,
leaving only the physical band, whose 2nd-order shift **equals** the holonomy.

## Verification

`python -u src/utilities/trlnT_prescription.py` -- 5 checks PASS: `det T = -sin^2(w/2)`
k-independent; magnetic invisible to det; electric on-site-only in det; bands respond
oppositely (sum `~1e-15`); physical band `~1+i*omega` / doubler `~sin^2(w/2)` at `k=0`.

## Remaining (VIII side)

None on the prescription. VIII's intro/conclusion/abstract stay held for the joint release
(and will use the acknowledged engine-limitation framing). VIII flips its verdict row
PART -> PASS on your large-N confirmation.

## -> Consumer actions (Paper IV session)

- [ ] **Adopt the prescription**: project onto the physical band of `T(k)`, sum its
      second-order eigenphase shift over the BZ (unit weight). Cross-check that summing both
      bands gives ~0 (a sanity test of your extractor).
- [ ] **Anchor to `{4,4,16}` magnetically** before trusting the electric `{1,4,4}`; the
      overall scale is the deferred `1/g^2`, so compare STRUCTURE (eigenvalues, axis,
      `mu^-1 = adj(eps)`), not absolute magnitude.
- [ ] **Re-check the nticks-drift** with the physical-band projection -- the drift is the
      expected signature of doubler/free-dispersion leakage (the bands respond oppositely).
- [ ] **Confirm the reconcile bar** (frontmatter `decisions`) works for you, or propose an
      alternative.
- [ ] **On large-N confirmation landing**, file the return handoff to
      `dcl-paper-08-electric-induced-action` (block match + null split + vacuum-speed
      readout) so VIII flips PART->PASS and writes its held sections for the joint release.
