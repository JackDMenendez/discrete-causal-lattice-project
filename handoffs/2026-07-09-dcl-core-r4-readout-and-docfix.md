---
handoff: 2026-07-09-dcl-core-r4-readout-and-docfix
from: PM (dcl-website session)
to: dcl-core (focused)
repo: JackDMenendez/dcl-core
branch: main
commits: []                         # directive; dcl-core session makes the commits
pr: none
status: open
state: complete                     # directive fully specified; execution is the dcl-core session's
semver: MINOR (additive: new R4 induced-response readout capability in core3d; no removals/renames). Doc-fix is n/a.
flags:
  - "USER RULING (scope): R4 — the E+B induced-response readout / cancellation-screen estimator — is to be built as a REUSABLE, TESTED dcl_core capability, NOT left as a paper-04-only experiment script. This overrode the paper-04 session's 'compose it experiment-side, no new engine feature' recommendation. Paper IV's exp_03 driver will CONSUME this engine feature."
  - "ASYMMETRIC E/B COUPLING (load-bearing, from paper-04 exp_03a, commit a238896): magnetic B is a spatial link phase (clean holonomy → the exact {4,4,16} Q-tensor), but electric E enters as an on-site mass-like `delta_phi = omega + V(x)` — so there is NO electric Wilson-loop analog. The R4 readout must therefore measure a SAME-FOOTING induced response (density/token diffs vs a zero-field baseline + small-field susceptibility fit), which is exactly the reference estimator pattern already in `tests/test_peierls.py`. Do NOT assume an electric holonomy exists."
  - "SCOPE BOUNDARY: R4 is the STATIC, SMALL-N induced-response readout (the cancellation screen; exp_04 ran N=20 — CPU-cheap). It is NOT the later k-resolved dispersion-ORDER sweep (test #5), which is the GPU/large-N job (measured 41.5x at 128^3). Build the static readout now; the k-resolved sweep is a separate later item."
  - "DOC-FIX is a SEPARATE, SMALLER action bundled here (action 2): `docs/design/04_gauge_field_and_vacuum_response.md` still carries the stale 'test #4 is N-limited/GPU-bound' wording and the 'test #5 deferred' note. Test #4 is now exact/done (exp_04, {4,4,16}, max|Q-Paper_I_Q|=0) and test #5 is GPU-cheap, not deferred-for-hardware. Correct both. This was flagged pending in handoffs 2026-07-07-gauge-Q-tensor-observable-correction and 2026-07-09-exp03-driver-scope-and-gpu-feasibility."
  - "ELECTRIC ACTION BLOCK IS OUT OF SCOPE HERE: the covariant electric/permittivity ACTION block (the epsilon that would let exp_03 render a photon-dispersion VERDICT) is genuinely new theory, absent from Paper I and Paper II, and is being spun into its own paper (Paper VIII). This handoff is ONLY the R4 induced-response readout capability + the doc fix — not the electric-action derivation."
decisions:
  - "R4 as engine feature vs paper-04 script: user chose the reusable-engine-feature path (heavier but reusable). Filed to a dcl-core session accordingly."
consumed_by:
consumed_at:
---

## Summary
Two dcl-core actions arising from the Paper IV exp_03 escalation
(`2026-07-09-exp03-driver-scope-and-gpu-feasibility`, consumed). **(1)** Build the
**R4 induced-response readout** as a reusable, tested `dcl_core.core3d` capability (per
user ruling), which Paper IV's exp_03 driver will consume. **(2)** Fix the stale
`test #4 N-limited` / `test #5 deferred` wording in design-doc-04. The electric ACTION
block (permittivity) is explicitly NOT here — that is new theory, now Paper VIII.

## Context
- v0.3.0 already ships the primitives R4 sits on: Peierls hop, `uniform_B_potential`,
  spatial+temporal potential threading, GPU RawKernel, and a reference induced-response
  estimator inside `tests/test_peierls.py`.
- paper-04 `exp_03a` (commit `a238896`) is the working prototype of the static E+B
  cancellation screen; its estimator is the thing to promote to a supported engine API.
  Spec: paper-04 `notes/exp_03_R4_cancellation_screen_spec.md`.

## → Consumer actions
- [ ] **Build R4 as a reusable core3d capability.** Promote the static E+B
      induced-response readout (density/token diffs vs zero-field baseline + small-field
      susceptibility fit; combine magnetic + electric sectors into the effective
      response) from the paper-04 prototype + the `test_peierls.py` reference estimator
      into a supported, documented, tested `dcl_core.core3d` API. Additive MINOR;
      preserve A=1 exactness; CPU-cheap/small-N (no GPU dependency for the static screen).
      Cross-check it reproduces exp_04's magnetic `{4,4,16}` on the B-only sub-case.
- [ ] **Fix design-doc-04 wording.** In `docs/design/04_gauge_field_and_vacuum_response.md`:
      (a) remove/correct "test #4 is N-limited/GPU-bound" — it is exact in the lattice
      interior for a uniform field (Wilson-loop holonomy), reproduced by `exp_04`
      (max|Q - Paper_I_Q| = 0, eigenvalues {4,4,16}, axis (1,1,-1)); (b) reframe "test #5
      deferred" — it is GPU-cheap now (41.5x at 128^3), not hardware-blocked; what gates
      the gauge *verdict* is the electric ACTION block (Paper VIII), not compute.
- [ ] **Do NOT derive the electric action block here.** That is Paper VIII scope.
- [ ] Consume this handoff (set `status: consumed`, fill `consumed_by`/`consumed_at`).
