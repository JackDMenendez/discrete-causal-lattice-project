---
handoff: 2026-07-18-paper04-gauge-tension-publish-honestly
from: dcl-paper-04 (focused)
to: PM
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: [28564c2]
pr: none
status: open
state: in-progress
semver: n/a (paper content: gauge-sector tension stated honestly; panel/website update)
flags:
  - "RESOLVED + DECIDED: the 2.a gauge-channel question (board #27) is characterized and the
     author's decision is to PUBLISH Paper IV with the tension honestly stated. The induced
     photon common-mode speed anisotropy v^2=k^T eps k, eps={1,4,4}, is O(1) and DIMENSION-4
     (NOT suppressed) -- three routes (geometric holonomy; Ward-safe physical-band vacuum
     polarization, traceless/iso ~0.5 q-independent; density response exp_03a). So for the
     single fixed trigonal domain it is a marginal CPT-even k_F Lorentz violation EXCLUDED by
     cavity/Michelson-Morley isotropy bounds (~1e-18). NOT 'may be null / under investigation'
     anymore -- it is a computed, excluded-as-constructed TENSION."
  - "ROOT (author insight): the anisotropy is the single tensor sum_a V_a V_a^T = {1,4,4},
     O(1) only because the hop set is THREE of the four cube body-diagonals (omitting
     V_4=(1,1,-1)); the FOUR-diagonal set = 4*I (isotropic). The optical axis (Paper IV's
     subject) and this tension share ONE origin -- the arbitrary V_4 exclusion / single-domain
     choice. Matter survives it (leading term a SCALAR -> dim-6 anisotropy, viable); the
     induced photon does not (a TENSOR -> dim-4, O(1)). Emergent Lorentz invariance doesn't
     descend to the induced gauge sector."
  - "RESOLUTION IS OPEN + FOUNDATIONAL (do NOT advertise as fixed). dcl-math admits four-axis /
     higher-dimensional / polygonal hop topologies; a four-orientation VACUUM would restore
     O_h for the induced gauge loop while matter keeps its dim-6 axis (decoupling). Whether it
     preserves A=1 + Dirac is a Paper-I-level open question. The author suggests this
     structural derivation is foundational (a 'Paper-01 / research project'). Candidate for its
     own paper; keep board #27 open as the tracker."
  - "SCOPE (must be honored on the panel/website): the tension is SPECIFIC to the gauge-sector
     common-mode speed. It does NOT touch the birefringence null (passed), the adjugate
     theorem, the kinematic directional dispersion, the Bell-test / quantum results, or the
     broader program. Do not let 'gauge sector in tension' read as 'the DCL is falsified'."
decisions:
  - "Publish Paper IV with the gauge-sector tension honestly stated, root cause and structural
     resolution direction included, cleanly scoped (author, 2026-07-18). Submission-readiness:
     this completes the honest account; the resolution is tracked follow-on, not a blocker."
consumed_by:
consumed_at:
---

## Summary
The gauge-sector 2.a question is settled enough to state honestly, and the author's call is
to publish Paper IV with the tension in the open. The induced photon speed anisotropy is an
O(1), dimension-4 Lorentz violation that, for the single-domain construction, is excluded --
and its root is the arbitrary omission of the fourth cube diagonal that also creates the
optical axis. The paper now says so plainly (abstract, falsifiability section, conclusion,
audit table), traces the root, gives the structural (four-axis / four-orientation) resolution
as an open foundational direction, and scopes the tension tightly. The panel/website need to
reflect this: the gauge common-mode channel is a documented tension, not a clean prediction
and not merely "under investigation."

## Shipped (paper-04, commit 28564c2)
- falsifiability.tex: subsec:gauge_channel rewritten to a "stated tension" (O(1) dim-4;
  excluded as-constructed; root = V_4 exclusion; matter-vs-photon scalar/tensor; four-axis /
  four-orientation resolution open; scope). Map-table row iv updated.
- audit_table.tex: gauge common-mode row -> FAIL (as single domain; open otherwise);
  falsifiability map row entry iv updated.
- abstract.tex + conclusion.tex: honest tension, scoped.
- notes/gauge_anisotropy_root_and_resolution.md (foundational seed) + notes/gauge_common_mode_order.md.
- Builds clean (make paper, 25 pp).

## -> Consumer actions (PM)
- [ ] **Update board #27:** 2.a characterized -> O(1) dim-4, EXCLUDED as single-domain
      construction (not 'may be null'); root = V_4 exclusion; resolution = O_h-restoring
      construction (four-axis / four-orientation vacuum), OPEN foundational follow-on (candidate
      for its own paper). Keep #27 open as the tracker.
- [ ] **Update the dcl-website claim map / project panel:** the gauge-sector common-mode speed
      channel = a documented TENSION (excluded for the single-domain construction), with a known
      structural resolution direction that is open. NOT a clean prediction, NOT 'under
      investigation / may be null'. Keep the birefringence row as the passed/corroborated null.
- [ ] **Honor the scope on the site:** state clearly that this tension is specific to the gauge
      common-mode speed and does NOT affect the birefringence null, the kinematic channel, the
      Bell-test results, or the rest of the program. Avoid any 'DCL falsified' framing.
- [ ] **Note the foundational thread:** the author flags that the structural derivation (which
      sector inherits which symmetry; V_4 inclusion / polygonal topologies) may warrant a
      dedicated foundational paper ('Paper-01 / research project'). Flag for roadmap if wanted.
- [ ] Paper IV is now honest and (per the author) publishable with the tension stated; the
      resolution is follow-on, not a blocker.
