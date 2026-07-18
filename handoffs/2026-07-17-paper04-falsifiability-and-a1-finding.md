---
handoff: 2026-07-17-paper04-falsifiability-and-a1-finding
from: dcl-paper-04 (focused)
to: PM
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: [4018225]
pr: none
status: open
state: complete
semver: n/a (paper content: falsifiability framing + a derived physics result)
flags:
  - "SUBSTANTIVE PHYSICS FINDING (series-level, not just Paper IV wording): the A=1
     normalization argument, derived + numerically verified, shows the kinematic
     transfer-operator eigenphase DISPERSES for omega!=0 (massive sector) but is
     EXACTLY FLAT at omega=0 (massless limit): arg(lambda_pm) in {0,pi}, k-independent,
     max|grad_k theta|=0 (verified). So the massless/photon limit of the SPINOR
     propagator does NOT disperse -- the directional dispersion is a MASSIVE-sector
     effect. The object an astrophysical PHOTON test would constrain is therefore NOT
     the omega->0 kinematic mode; on this lattice the photon is the induced GAUGE field,
     whose dispersion is the common-mode speed anisotropy (gated on the open O_h
     restoration question)."
  - "FALSIFIABILITY VERDICT (the paper's motivation, now called out -- it was entirely
     absent from the paper before): optical-axis BIREFRINGENCE is a NULL (it cancels)
     and so is NOT a falsification channel -- a consistency check, not a test. 'The DCL
     is not falsifiable via optical-axis birefringence.' The candidate falsifiable
     content is the directional dispersion, but as a massive-sector effect whose mapping
     onto an astrophysical PHOTON bound is NOT established. New audit row = PART."
  - "SERIES IMPACT (PM/author must weigh): the falsifiability analysis in Paper IV's
     notes/falsifiability_and_sme_mapping.md (SME dim-6 PHOTON sector c^(6), LHAASO
     GRB 221009A window a<~3e-28 m) assumes a PHOTON dim-6 dispersion. The omega=0
     result shows the kinematic spinor channel does NOT provide one; the photon
     dispersion lives in the gauge sector's common-mode anisotropy, which is factor-~2
     (order unity) and O_h-restoration-dependent. So the clean 'kinematic dim-6 photon
     falsifier' the series leaned on needs re-examination -- it is NOT delivered as
     previously stated. This is a real result, not a presentation choice."
  - "NUANCE (claim-auditor-corrected): omega=0 has NO energy DISPERSION, but it is NOT
     featureless. The eigenvalue-MAGNITUDE anisotropy |H~|^2=1-(4/3)|k_perp|^2 is a real,
     omega-INDEPENDENT observable -- the anisotropic spreading exp_01 measures -- because
     the A=1 rule renormalizes the TOTAL norm of a state, not each k-mode, so it does not
     flatten the relative magnitudes across a wavepacket. So the massless channel carries a
     genuine magnitude/filtering anisotropy (distinct from a speed/energy dispersion). For
     falsifiability option (b), THIS is the real massless observational handle -- an
     amplitude/attenuation anisotropy, not an SME dim-6 dispersion -- and its testability is
     its own question. (Do not restate the earlier draft's wrong claim that renormalization
     'flattens' it.)"
  - "AFFIRMED ALGEBRA UNAFFECTED: the adjugate theorem Q_B=adj(P) and the doubled-root
     birefringence cancellation stand independently of the falsifiability question."
decisions:
  - "Called out falsifiability HONESTLY now (audit-row + intro + conclusion) rather than
     waiting for the photon-dispersion resolution, on the user's instruction (2026-07-17).
     The bold 'frontier-testable photon falsifier' framing is NOT asserted -- it is named
     as the open item, because the A=1 finding points away from it, not toward it."
consumed_by:
consumed_at:
---

## Summary

The user flagged that Paper IV's core motivation -- falsifiability of the DCL -- was
never called out in the paper. Fixing that surfaced a real result. The A=1 normalization
argument (which the external reviewer had asked for) is now derived and numerically
checked, and it shows the massless limit of the kinematic channel does not disperse.
Consequently: optical-axis birefringence is a consistency null (not a falsifier), the
directional dispersion is a massive-sector effect, and the falsifiable *photon* dispersion
the series has leaned on is not delivered by the kinematic channel -- it routes through the
gauge sector's common-mode anisotropy and the open O_h question. Called out honestly in
the paper; flagged here because it bears on the series' falsifiability claims.

## What was added (paper-04, commit 4018225)

- Kinematic section: new subsection *The A=1 normalization and the massless limit* --
  derives the eigenphase->group-velocity reading for omega!=0 (the per-tick renormalization
  is a real, phase-preserving rescaling -> a unitary physical propagator whose eigenphase is
  the energy), and Prop *Massless-limit degeneracy* (omega=0 eigenphase flat, verified
  max|grad theta|=0). Aligned the opening caveat + the photon-limit remark to the derived
  result.
- Audit table: refreshed kinematic row (group velocity now DERIVED for omega!=0; omega=0
  dispersionless); new *Falsifiability of the DCL along the optical axis* row (PART):
  birefringence is a null / not a falsifier; directional dispersion is the candidate
  falsifiable content, photon extension open.
- Introduction: falsifiability-motivation paragraph. Conclusion: written (was a placeholder),
  foregrounding the verdict and naming the open items where falsifiability is actually decided.

## Verification

`omega=0`: max|grad_k arg(lambda_+)| = 0.000 (arg identically 0); `omega=0.3,0.8`: O(1)
dispersion; |lambda_+|<1 throughout (the non-unitarity). Paper builds clean (make paper,
19 pp, no undefined refs). Claim-auditor pass in progress at write time.

## Remaining / decisions for PM + author

- **The series' falsifiability story needs a decision.** The 'kinematic dim-6 photon
  dispersion' falsifier (Paper IV `notes/falsifiability_and_sme_mapping.md`; the program
  claim map) is NOT provided by the kinematic spinor channel (massless limit doesn't
  disperse). Options the author should weigh: (a) relocate the falsifiable photon channel
  to the gauge sector's common-mode anisotropy and do that analysis (routes through the
  O_h-restoration question + the dynamical effective-action derivation); (b) reframe the
  massive-sector directional dispersion as the falsifiable claim and find its real
  observational handle (not the photon SME bound); (c) accept that this paper's clean
  falsifiable content is narrower than the series map assumed and update the map. This is
  a physics/strategy call, not a wording one.
- Paper IV itself is honest as it stands (the verdict is stated, the photon extension is
  the named open item), but it is NOT the clean falsifiability demonstration the series
  intended until (a)/(b) is resolved.

## -> Consumer actions (PM / author)

- [ ] **Decide the falsifiability strategy** (a/b/c above) -- this is the load-bearing call;
      route it back to this session to execute.
- [ ] **Reconcile the program claim map / `notes/falsifiability_and_sme_mapping.md`** with
      the omega=0 finding (the SME dim-6 photon mapping assumed a photon dispersion the
      kinematic channel does not supply).
- [ ] **Note on the board (#13):** falsifiability is now called out in Paper IV, honestly,
      with the photon-dispersion falsifier as a stated open item -- the paper is a correct
      working draft, not the finished falsifiability demonstration.
