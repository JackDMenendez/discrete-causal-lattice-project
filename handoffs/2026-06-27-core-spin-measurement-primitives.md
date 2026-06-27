---
handoff: 2026-06-27-core-spin-measurement-primitives
from: dcl-paper-06-Bell-test (focused)
to: PM
repo: dcl-paper-06-Bell-test
branch: main
commits: []                         # requirements request; nothing shipped yet
pr: none
status: consumed
state: blocked
semver: dcl_core core line, next MINOR (maintainer's call) — additive primitives, unreleased
flags:
  - "Version: dcl_core v0.3.0 changes core3d ONLY (confirmed by author), so these core measurement primitives are an INDEPENDENT additive change on the core line. Version is the maintainer's call; not blocked by the in-flight v0.3.0/core3d work."
  - "apply_phase_map is NOT a valid Bell measurement (global U(1); leaves the Z-Bloch projection invariant). An implementer must NOT wire measurement to it."
  - "Mechanism is a hypothesis under test: CHSH>2 is expected to require prob_floor>0 and vanish in the continuum. If the joint+floor primitive still yields S<=2, the paper headline flips (primitive still correct/useful; physics claim changes)."
  - "core is a released, legacy-bearing package: primitives MUST be additive-only (no existing signature/default/numeric change; the 26 tests/core xfails must not change count)."
  - "measure_pair must expose mode in {joint, per_session} AND honor prob_floor on/off cleanly — the controlled comparison (violation switches ON with the floor) is the validity of the whole experiment."
decisions:
  - "Mechanism confirmed by author: discrete joint-collapse (measuring A repartitions the shared floored budget to B)."
  - "Primitives go in dcl_core.core (author's call), NOT hand-rolled in the experiment; author/maintainer implements, focused session specifies."
  - "Focused session is front-loading the CHSH harness + Bell-state validation + experiment skeleton against this interface while the primitives are built."
consumed_by: PM (dcl-website session)
consumed_at: 2026-06-27
---

> **PM consume note (2026-06-27):** board issue
> [#21](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/21)
> opened (prefix 019, "Core Software core spin-measurement primitives (Bell test, Paper VI)")
> and added to project 6. Durable facts recorded in the dcl-website memory
> (`bell-test-investigation`): qubit = spinor (R,L), discrete-joint-collapse
> mechanism, P1–P4, the `apply_phase_map` flag, and the gate (Paper 06 RUN
> blocked until primitives land). Core implementation / tests / release remain
> open and are tracked by issue #21, not by this handoff.

## Summary
Paper 06 (Bell/CHSH) needs four additive spin-measurement primitives in
`dcl_core.core` so it can run a real CHSH test on the lattice spinor and test
whether a Bell violation is a discrete-probability (`prob_floor`/δp_min) effect.
The continuous engine as released cannot express a measurement basis or a joint
pair collapse, so the experiment is blocked until these land. Full spec (the
authority for API + tests):
`dcl-paper-06-Bell-test/notes/core_measurement_requirements.md`.

## Shipped
- (none) — this is a forward requirements request, not shipped code.

## Verification
N/A yet. Acceptance tests specified in the requirements doc §8; the load-bearing
one is the `measure_pair` positive control: a textbook maximally-entangled state
at optimal angles must give S → 2√2 in "joint" mode, while product states /
"per_session" mode / prob_floor=0 give S ≤ 2, with a no-signalling check.

## Remaining
Maintainer implements P1–P4 in `dcl_core.core` (additive) + tests, then releases
(or editable-pins). Paper 06 then bumps its `.venv-ucrt64` pin and runs the gate
experiment. The CHSH estimator, pair preparation, prob_floor sweep, and figures
stay in Paper 06 (not core) — and are being built now against this interface.

## Decisions & flags
See frontmatter. Load-bearing: (1) version is the maintainer's call — 0.3.0 looks
taken by gauge work, so likely 0.4.0; (2) do not reuse `apply_phase_map`;
(3) the `mode` + `prob_floor` switches are mandatory and are the experiment's
control; (4) additive-only on a released package; (5) the physics claim is a
hypothesis — the primitive is correct regardless of whether S crosses 2, but the
paper's framing depends on the result.

## → Consumer actions
- [ ] Core: implement P1–P4 (`rotate_spinor`, `spin_expectation`, `measure_spin`,
      `measure_pair`) in `dcl_core.core` per
      `dcl-paper-06-Bell-test/notes/core_measurement_requirements.md`. Additive;
      pick the version (note 0.3.0 in-flight → likely 0.4.0).
- [ ] Core: add acceptance tests §8 — esp. the `measure_pair` Bell-state positive
      control (S→2√2 joint mode) and the no-signalling marginal check.
- [ ] Release: tag/deposit the new `dcl_core` MINOR (or provide an editable pin)
      and notify Paper 06 to update its `virtual-env-requirements` / venv pin.
- [ ] Board: open an issue in `discrete-causal-lattice-project` (project 6) for
      "core spin-measurement primitives (Bell test)", linked to Paper 06.
- [ ] Gate: Paper 06's experiment RUN is blocked until the primitives land; the
      harness/skeleton are being written now so it runs the moment they ship.
