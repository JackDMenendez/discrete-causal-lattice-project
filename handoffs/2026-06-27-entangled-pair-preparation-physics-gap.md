---
handoff: 2026-06-27-entangled-pair-preparation-physics-gap
from: dcl-paper-06-Bell-test (focused)
to: dcl-core (focused)
repo: dcl-paper-06-Bell-test
branch: main
commits: []                         # physics design question; no code shipped
pr: none
status: open
state: blocked
semver: n/a (physics/design question; may yield ONE additive core primitive, create_entangled_pair)
flags:
  - "MAKE-OR-BREAK: joint normalization of two independently-initialised spinors is a DIRECT SUM (C^2 (+) C^2), not a TENSOR PRODUCT (C^2 (x) C^2). A direct-sum joint norm does NOT create tensor-product entanglement, so measure_pair(mode=joint) over such a pair is expected to give CHSH <= 2 EVEN WITH prob_floor>0. The current prepare_pair() placeholder is exactly this direct-sum case."
  - "Therefore the gate result hinges on the PREPARATION, not just the measurement primitives. P1-P4 (handoff 2026-06-27-core-spin-measurement-primitives) are necessary but NOT sufficient; without a correct entangled preparation the experiment will read S<=2 and look like a null result for the wrong reason."
  - "Open physics question for the author: is prob_floor's nonlinearity the mechanism that converts a joint-normalized (direct-sum) coupling into a genuinely non-factorizable joint distribution, or is an additional structural coupling (shared cone support / overlapping lattice region / a defined birth-split spinor) required?"
decisions:
  - "Author/physicist to define the canonical entangled-pair birth event (annihilation -> two photons) and whether it belongs in core as create_entangled_pair(...) or stays an experiment-level preparation."
consumed_by:
consumed_at:
---

## Summary
Paper 06's CHSH gate needs more than measurement primitives: it needs a
PREPARATION that produces a genuinely entangled photon pair on the lattice.
The provisional `prepare_pair()` in `exp_01_chsh_bell.py` just calls
`enforce_joint_unity` on two independently-initialised massless sessions —
which is a direct-sum joint normalization and (by construction) cannot encode
tensor-product entanglement. This handoff asks the author to pin the physics
of the entangled birth event, because the gate's verdict depends on it.

## The gap (precise)

The chirality qubit of a session is the `(psi_R, psi_L)` Bloch vector. Two
sessions A, B have a joint state. For a CHSH violation, `P(s_A, s_B | a, b)`
must NOT factorize. But:

- `enforce_joint_unity([A, B])` rescales `(psi_RA, psi_LA, psi_RB, psi_LB)` by
  a single scalar — it normalizes a 4-complex-dim DIRECT SUM. The marginal
  Bloch vectors are unchanged in direction; the pair stays a product up to a
  shared scale. Measuring A does not steer B's Bloch vector.
- A maximally entangled pair lives in the TENSOR PRODUCT `C^2 (x) C^2`. Joint
  normalization alone does not reach it.

So `measure_pair(mode=joint)` over the placeholder prep is expected to give
`S <= 2` regardless of `prob_floor`. That would be a null result caused by the
preparation, not by the discrete-collapse mechanism — a false negative.

## The questions for the author

1. **Birth event.** What is the canonical annihilation/pair-creation event in
   the A=1 framework that yields two outgoing photon sessions whose chirality
   DOFs are non-factorizably correlated? (See
   `c:\dev\dcl\notes\entanglement_as_shared_cone_harmonic.md` §"The Stronger
   Case: Photon Pair Creation" — the joint-normalization-from-birth argument —
   and make it operational.)
2. **Where does the tensor structure come from?** Candidates: shared/overlapping
   cone support at birth (the two sessions occupy a common lattice region so
   their joint amplitude is not separable); a defined birth-split of the parent
   spinor across the two children; or prob_floor's nonlinearity acting on a
   shared budget. Which is load-bearing?
3. **Does discreteness do the work?** Is `prob_floor>0` the ingredient that
   makes the joint floored collapse non-factorizable (the paper's thesis), or
   is it only a refinement on top of an already-entangled preparation?
4. **API placement.** If a preparation primitive is warranted, should core ship
   `create_entangled_pair(...)` (additive), or does this stay in the Paper 06
   experiment layer?

## Remaining / dependencies
- Pairs with handoff `2026-06-27-core-spin-measurement-primitives` (the P1-P4
  measurement primitives). That handoff is necessary; this one determines
  whether the gate can return a TRUE result rather than a preparation artifact.
- Paper 06 harness + reference control are built and green; the lattice gate is
  blocked on BOTH this preparation answer and the P1-P4 primitives.

## → Consumer actions
- [ ] Physics: define the canonical entangled-pair birth event (Q1-Q3 above);
      record it as a dcl-core note and/or a Paper 06 design note.
- [ ] Decide API placement (Q4): `create_entangled_pair` in core (additive) vs
      experiment-level prep. If core, fold into the same MINOR as P1-P4.
- [ ] Confirm/deny the thesis framing: is CHSH>2 expected to require prob_floor>0
      GIVEN a correct preparation, or does the preparation alone already entangle?
- [ ] Reply via a return handoff (dcl-core -> focused) so Paper 06 can wire
      `prepare_pair()` to the real birth event before running the gate.
