---
handoff: 2026-07-17-paper08-to-paper04-ward-open-decision
from: dcl-paper-08 (focused)
to: dcl-paper-04 (focused)
repo: JackDMenendez/dcl-paper-08-electric-induced-action
branch: main
commits: [237d690, 039db72]
pr: none
status: open
state: complete
semver: n/a (paper VIII v0.1-DRAFT, unreleased)
flags:
  - "AUTHOR DECISION (2026-07-17): the single-object dynamical (momentum-space fermion-loop)
     extraction of the induced-action TENSOR is left FORMALLY OPEN -- candidate for a
     follow-on paper. It is methodological completeness, NOT correctness: methods (a)
     geometric-holonomy and (b) Tr ln T are the same induced action and must agree, and (a)
     already gives {4,4,16} (engine-verified). Not on the companion critical path."
  - "HONESTY IS THE OBLIGATION: since the single-object extraction is not achieved, IV's
     paper must NOT claim it. Frame the tensor as geometric-structure x scalar-magnitude,
     present the null split + A=1-survival as the dynamical confirmations, and acknowledge
     the momentum-space tensor assembly as a stated open item. Checklist below."
  - "TECHNICAL ANSWER already delivered in 2026-07-17-paper08-to-paper04-ward-safe-answer
     (diagnosis: intraband pole on the flat optical axis, Ward-cancelled; drop it, finite
     omega, no PV; verifier src/utilities/ward_safe_diagnosis.py). This handoff adds the
     DECISION + the honesty checklist; it does not change the technical answer."
decisions:
  - "Leave the single-object dynamical tensor extraction OPEN and be honest about it (author,
     2026-07-17). Possible follow-on paper to address the correct orbital-susceptibility
     (Berry-curvature + quantum-metric) assembly. Recorded in VIII
     notes/ward_safe_vacuum_polarization.md + CLAUDE.md."
consumed_by:
consumed_at:
---

## Summary

The author has decided to leave the single-object dynamical tensor extraction **open**, and
to be **honest** about it in the companion. This handoff records that decision and gives IV a
concrete honesty checklist for its paper. The technical Ward-safe answer (diagnosis + pole-
free prescription) was already delivered separately; nothing there changes. The birefringence
verdict is unaffected -- the null split (`1.8e-15`) and A=1-survival stand independently.

## Why open is safe (one line)

Methods (a) geometric-holonomy and (b) fermion-loop are the **same induced action** and must
agree; (a) already gives `{4,4,16}` (engine-verified). Finishing (b) would confirm a known
answer, not decide anything -- so it is scoped follow-on work, not a gap in the result.

## -> Consumer actions (Paper IV session)

Honesty checklist for IV's paper -- **DO:**

- [ ] Frame the induced-action tensor as **geometric STRUCTURE x scalar MAGNITUDE**: the
      anisotropic `{4,4,16}`/`{1,4,4}` structure is the plaquette holonomy computed from the
      engine's hop vectors (a genuine from-engine computation, `exp_04`-style, pole-free), and
      the physical-band trace supplies the isotropic scalar `1/g^2`.
- [ ] Present as the DYNAMICAL confirmations: the **null split** (Fresnel solver on VIII's
      `(P, Q_B)` blocks, `1.8e-15`, with the detuned `0.5` control) and the **A=1-survival**
      of the anisotropy (correct senses, B enhanced / E suppressed). These are IV's real,
      independent results.
- [ ] **Acknowledge as a stated open item**: the single-object momentum-space fermion-loop
      extraction of the tensor (the Ward-safe orbital-susceptibility / Berry-curvature +
      quantum-metric assembly), deferred -- possibly a follow-on paper. Cite VIII's
      `notes/ward_safe_vacuum_polarization.md` for the diagnosis.

**DO NOT:**

- [ ] Do NOT claim a from-scratch single-object dynamical extraction of the full induced-
      action tensor -- it was not achieved.
- [ ] Do NOT present the naive band-sum tensor (the symmetric interband current-current
      result -- uniaxial about `(1,-1,0)`, ratio ~9) as a result; it is the wrong object.
      Discard it.
- [ ] Do NOT imply the anisotropic STRUCTURE was derived from the fermion-loop dynamics; it
      is geometric (holonomy). "From the engine hop-vector geometry" is honest; "from the
      dynamical band sum" is not.

Other:

- [ ] Confirm you are content with this framing for the companion, or flag any wording you
      want VIII to mirror (VIII's held intro/conclusion will use the same geometric-structure
      x scalar-magnitude framing and the same open-item acknowledgement).
- [ ] On the large-N confirmation landing, file the return handoff to
      `dcl-paper-08-electric-induced-action` so VIII flips PART->PASS and writes its held
      sections for the joint release.
