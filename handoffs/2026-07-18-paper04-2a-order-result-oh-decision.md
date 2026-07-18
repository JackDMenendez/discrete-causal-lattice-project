---
handoff: 2026-07-18-paper04-2a-order-result-oh-decision
from: dcl-paper-04 (focused)
to: PM
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: [68721ad]
pr: none
status: consumed
state: in-progress
semver: n/a (physics result + direction; panel/website update needed)
flags:
  - "PANEL + WEBSITE UPDATE NEEDED (consequential, possibly-negative result). 2.a (board
     #27, gauge-sector photon common-mode speed anisotropy) has been SHARPENED by an order
     computation: the anisotropy is O(1), DIMENSION-4, NOT suppressed. The 'small / viable
     suppressed prediction' outcome is RULED OUT. 2.a is now a BINARY: NULL (if the vacuum
     is O_h-restored) or EXCLUDED (if single-domain -> a factor-~2 direction-dependent speed
     of light -> the gauge sector is FALSIFIED by cavity/Michelson-Morley bounds). The
     birefringence null is UNAFFECTED (this is the common-mode speed, not a polarization
     split). Note: `notes/gauge_common_mode_order.md` (paper-04 commit 68721ad)."
  - "DIRECTION (user, 2026-07-18): we chose to ATTACK THE O_h / SINGLE-DOMAIN QUESTION next
     -- is the physical A=1 vacuum a single fixed trigonal domain (-> tension/exclusion) or
     does the continuum limit / coarse-graining restore O_h (-> null)? Structurally the
     lattice is ONE fixed hop-set (no ensemble of four domains), which points toward the
     EXCLUDED branch unless a coarse-graining mechanism restores O_h. This is the decisive
     fork; work starts now in the paper-04 session (board #27)."
  - "WEBSITE HONESTY: the panel/claim-map must NOT advertise the gauge common-mode anisotropy
     as a clean standing prediction. It is under active investigation with a POSSIBLE
     FALSIFICATION of the framework's electromagnetism. Combined with the earlier flag (the
     claim-map lists optical-axis birefringence as a standing falsifiable prediction, which
     is now a PASSED NULL, not a live prediction), the DCL claim map needs two edits: (a)
     birefringence -> passed/corroborated null; (b) gauge common-mode speed anisotropy ->
     open, binary null-or-EXCLUDED, under investigation."
  - "SCOPE: this does NOT touch the birefringence verdict (still PASS/cancels) nor the
     kinematic channel. It is specific to the gauge-sector COMMON-MODE speed. Method caveat:
     the dynamical q-scan uses the naive interband (Ward-safe) object -- the 'wrong-axis'
     tensor VIII flagged -- used only to gauge the ORDER, corroborating the geometric route;
     for the correct object to be suppressed, the Berry+metric terms would have to cancel an
     O(1) anisotropy (non-generic, and the naive evidence is against it)."
decisions:
  - "Attack the O_h/single-domain question as the decisive fork for 2.a (user, 2026-07-18).
     The 'compute the order only' step is done and returned O(1)/dim-4, closing the
     PASS-on-smallness path."
consumed_by: PM (dcl-website session) — board #27 commented (order O(1)/dim-4, binary null-or-EXCLUDED, possible falsification, In Progress); claim-map.qmd gauge-channel wording revised to binary/under-investigation (LOCAL, unpushed — publish held pending the O_h verdict); scope noted; awaiting O_h/single-domain verdict follow-up
consumed_at: 2026-07-18
---

## Summary
The 2.a "order only" computation is done and it is consequential. The gauge-sector
common-mode speed anisotropy is O(1), dimension-4, and NOT suppressed (two independent
routes: the constant geometric induced blocks give a k-independent factor-~2 anisotropy;
a Ward-safe physical-band q-scan gives an anisotropy ratio that converges to a constant
~0.32, not to 1, as |q|->0). This rules out the "small viable prediction" outcome and
turns 2.a into a binary: NULL (O_h-restored vacuum) or EXCLUDED (single-domain vacuum ->
a factor-~2 anisotropic speed of light -> gauge sector falsified). The birefringence null
is untouched. Per the user, we now attack the O_h / single-domain question, which decides
the branch. The project panel and website need to reflect this (and the earlier
birefringence-is-a-passed-null flag).

## The result (detail in notes/gauge_common_mode_order.md, commit 68721ad)
- Geometric: `eps={1,4,4}` constant -> `v in [1,2]`, |k|-independent = dim-4, O(1).
- Dynamical Ward-safe q-scan (|q| = 0.30, 0.20, 0.12, 0.07): anisotropy ratio
  0.60 -> 0.37 -> 0.33 -> 0.32 (converging to a constant != 1) = dim-4, O(1).
- => not suppressed; PASS-on-smallness is closed; 2.a is null-or-excluded.

## -> Consumer actions (PM)
- [ ] **Update board #27 (2.a):** status = order computed -> O(1) dim-4; the sector is now a
      binary null-or-EXCLUDED; actively investigating the O_h/single-domain fork. Flag it as
      a POSSIBLE FALSIFICATION of the gauge sector (not a clean prediction).
- [ ] **Update the dcl-website claim map / project panel** with TWO edits: (a) optical-axis
      birefringence -> a PASSED / corroborated null (excludes the dim-5 birefringent rivals),
      NOT a standing live prediction; (b) gauge-sector common-mode speed anisotropy -> OPEN,
      binary null-or-EXCLUDED, under active investigation (possible tension). Do not present
      either as a clean frontier prediction.
- [ ] **Note the scope:** the birefringence verdict (cancels) and the kinematic channel are
      unaffected; this is specific to the gauge common-mode speed.
- [ ] **Expect a follow-up** from the paper-04 session with the O_h/single-domain verdict
      (null vs excluded), which will settle whether this is a consistency null or a genuine
      tension the framework must address.
