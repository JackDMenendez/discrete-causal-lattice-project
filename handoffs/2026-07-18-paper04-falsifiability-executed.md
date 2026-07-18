---
handoff: 2026-07-18-paper04-falsifiability-executed
from: dcl-paper-04 (focused)
to: PM
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: [ad10bb5, b27bea6]
pr: none
status: consumed
state: complete
semver: n/a (paper content: falsifiability section)
flags:
  - "DONE + PUSHED: the do-both falsifiability decision is executed and on origin/main. New
     paper/sections/falsifiability.tex (wired in): the birefringence null is framed as a
     PASSED falsifiable prediction (forbids a tightly-bounded observable; excludes the
     CPT-odd dim-5 birefringent rivals; corroborates the CPT-even non-birefringent class),
     with BOTH honesty guardrails; a multi-channel map table; 2.b kinematic content
     (dim-6, Planck-suppressed, distinctive SIDEREAL signature + neutrinos, honest
     above-Planck bound); 2.a gauge photon dispersion as OPEN/contingent (Tr ln T + O_h,
     may be null) -- NOT asserted. Intro/conclusion/audit-row reframed; SME notes reconciled.
     SME placement verified vs Kostelecky-Mewes; bib adds K-M 2009, LHAASO 2024, K-Russell.
     Builds clean (make paper, 23 pp). Claim-auditor: passed (3 items fixed, incl. making the
     LHAASO a<~3e-28 m figure an explicitly EXTERNAL scale-setting bound, not a result of the
     framework's own open photon channel)."
  - "2.a IS TRACKED FOLLOW-ON, NOT DONE. The gauge-sector photon dispersion (common-mode
     anisotropy) is presented OPEN/contingent, gated on exactly the VIII-revision program:
     (1) the effective-action (Gamma^(2) / Tr ln T) derivation legitimizing eps,mu^-1 as the
     dynamical vacuum response; (2) the O_h-restoration computation (may null it). This is the
     same gauge effective-action + O_h work behind board #17/#18/#19. PM QUESTION: does 2.a
     need its own board issue, or ride #17-19?"
  - "SUBMISSION-READINESS: per the author's decision, SHIP the review-revised draft with the
     honest multi-channel map NOW; pursue 2.a as follow-on. Still-open polish (from
     2026-07-17-paper04-merge-complete): the reviewer's OTHER external references (anisotropic
     Maxwell media, lattice gauge actions, temporal plaquettes, constitutive closure) are NOT
     yet added -- only the SME/LV refs are; audit table not de-compressed; acknowledgements
     still a stub. None block the ship-with-caveats decision."
decisions:
  - "Executed do-both (2.b concrete, 2.a contingent) + the passed-prediction rebuttal, per
     handoffs 2026-07-18-paper04-falsifiability-do-both-decision and
     -birefringence-null-is-a-passed-falsifier (both consumed)."
consumed_by: PM (dcl-website session) — origin confirmed current (b27bea6); 2.a given its own board issue #27 (025, In Progress); dcl-website claim-map.qmd inconsistency surfaced to user (lists birefringence as a standing falsifiable prediction — now a passed null); ship-with-caveats noted
consumed_at: 2026-07-18
---

## Summary
The author's do-both falsifiability decision and the "birefringence null is a passed
falsifiable prediction" rebuttal are executed in the merged paper and pushed to origin.
Paper IV now has a dedicated Falsifiability section with a multi-channel map: the
birefringence null reframed as a passed test that excludes the birefringent rivals; the
kinematic massive dispersion as the concrete (Planck-suppressed, sidereal-signature)
falsifiable channel; the omega=0 filtering anisotropy as a real observable; and the
gauge-sector photon dispersion as an open, contingent follow-on. SME placement is verified
and cited. 2.a remains tracked follow-on (same program as the VIII revision).

## Shipped (paper-04, pushed)
- `ad10bb5` -- new falsifiability.tex (map + rebuttal + 2.b + 2.a); intro/conclusion/audit
  reframed; notes reconciled; bib (K-M 2009, LHAASO 2024, K-Russell).
- `b27bea6` -- claim-auditor fixes (external LHAASO bound framing; explicit guardrail (b)).

## Verification
Builds clean: make paper -> build/Paper.pdf, 23 pp, no undefined refs/citations. Claim-
auditor: no residual "not a falsifier" in rendered prose; both guardrails present; 2.a not
asserted; no detection/near-Planck claim; kinematic channel not conflated with the photon
dispersion; citations + a<~3e-28 m match the bib and notes.

## -> Consumer actions (PM)
- [ ] **Confirm origin/main current** for dcl-paper-04 (through the pushed falsifiability
      commits) -- it is now pushed (not the earlier unpushed state).
- [ ] **Decide 2.a board placement:** own issue, or fold into the gauge effective-action +
      O_h work already tracked under #17/#18/#19. It is the same program as the VIII revision.
- [ ] **Note submission-readiness:** ship-with-caveats is satisfied; the remaining polish
      (non-SME external references, audit-table de-compression, acknowledgements) is optional
      pre-deposit cleanup, not a blocker.
- [ ] **Program claim map:** reconcile it with the omega=0 finding -- the "kinematic dim-6
      photon falsifier" is retired; the dim-6 photon channel is the gauge sector's (open),
      and the kinematic channel is massive-sector + the omega=0 filtering anisotropy. (Paper
      note done: notes/falsifiability_and_sme_mapping.md carries the reconciliation banner.)
