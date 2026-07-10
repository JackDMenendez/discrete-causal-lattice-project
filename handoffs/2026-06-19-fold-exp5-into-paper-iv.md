---
handoff: 2026-06-19-fold-exp5-into-paper-iv
from: PM
to: dcl-paper-04 (focused)
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: []
pr: none
status: consumed
state: in-progress
semver: n/a (paper / manuscript)
flags: [exp5-redundant-fold-as-restatement-not-new-claim, spreading-half-must-survive-continuum-limit]
decisions: [exp5-not-a-falsifier-repo]
consumed_by: dcl-paper-04 (focused)
consumed_at: 2026-07-09
---

## Summary
Forward directive (PM → Paper IV author): **fold the proposed post-v1.0
"Experiment 5 — Vacuum Birefringence & Wave-Packet Spreading" into existing
work rather than standing it up as its own falsifier.** Decision basis: Exp 5
is largely redundant — both halves collapse onto physics already owned.
Full analysis in PM memory `post-v1-experiment-program.md` (Exp 5 entry).
This is a directive (nothing shipped); the manuscript edit is the Paper IV
author's call — left to that session deliberately, not done by PM.

## Shipped
(n/a — directive, not a code change.)

## Verification
Redundancy decomposition (basis for the fold):
- **Birefringence half** = Paper IV's own subject (optical-axis birefringence)
  + the propagation-face of post-v1 Exp 2's `O_h` scattering anisotropy. Third
  restatement of the `SO(3)→O_h` thread.
- **Spreading half** = post-v1 Exp 1 (LIV dispersion) in real space: packet-
  spread rate = group-velocity dispersion `d²E/dp²`, a derived consequence of
  `E²=p²+m²+α p⁴/M²`. Same `α`, real-space readout. Not independent.

## Remaining
The manuscript fold + the two pointers below.

## Decisions & flags
- **`exp5-redundant-fold-as-restatement-not-new-claim` (FLAG).** Present the
  birefringence content as the SAME kinematic `O_h` channel Paper IV already
  treats — NOT a new independent prediction. Inflating it to a 5th falsifier
  invites the redundancy critique.
- **`spreading-half-must-survive-continuum-limit` (FLAG).** "Spreads faster
  than continuum QFT" ≈ numerical-dispersion ERROR. Free packets already
  spread; the lattice excess must be stated as the `a→0`-surviving residual,
  else it's an artifact, not physics (same trap as the cross-validation
  reframing).
- **`exp5-not-a-falsifier-repo` (decision).** Program = **4 falsifiers + 1
  demonstrator**; Exp 5 is the demonstrator, not a peer repo.

## → Consumer actions
- [ ] Paper IV manuscript: fold Exp 5's vacuum-birefringence framing
      (polarization-dependent speed tied to lattice orientation) into the
      EXISTING optical-axis treatment, as the same kinematic `O_h` channel —
      keep gauge-channel birefringence PASS-structural, kinematic the
      falsifiable handle.
- [ ] Record a pointer that the wave-packet-SPREADING half belongs to post-v1
      **Exp 1 (LIV dispersion)** as its real-space demonstrator — NOT Paper IV —
      so it is not lost when Exp 1 stands up.
- [ ] Honor the continuum-limit caveat on any "faster spreading" wording
      (see flag).
- [ ] Do NOT create an Exp 5 falsifier-repo.
- [ ] Keep framing at capability / falsifiability-sought (tier-2).
