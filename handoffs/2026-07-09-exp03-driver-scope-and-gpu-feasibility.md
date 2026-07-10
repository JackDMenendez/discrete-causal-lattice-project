---
handoff: 2026-07-09-exp03-driver-scope-and-gpu-feasibility
from: dcl-paper-04 (focused)
to: PM
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: []                         # decision-request; context commit is 3de7423 (paper-04, already handed off)
pr: none
status: open
state: blocked                      # complete as a finding; the ACTION (write exp_03) is gated on a PM scope call + owner R4 decision
semver: n/a (analysis + capacity benchmark; no software change)
flags:
  - "DRIVER DOES NOT EXIST ANYWHERE: the load-bearing gauge test -- the full E+B photon-dispersion / induced-response birefringence-ORDER sweep (Paper IV `exp_03`, dcl-core design-doc `test #5`) -- is NOT implemented in either repo. dcl-core ships only the MAGNETIC-ONLY cross-check `exp_04` (N=20, the exact {4,4,16} Q-tensor); `tests/test_peierls.py:21-27` explicitly states test #5 is 'GPU/large-N bound and not part of the CPU-first build'. So there is nothing to run yet -- the driver must be authored before any verdict exists."
  - "DECISIVE, NOT CONFIRMATORY: exp_03 decides whether the gauge sector is (a) unobservable [framework consistent], (b) (ka)^2-suppressed [a new dim-6-like prediction], or (c) O(1) dim-4 [excluded -> a real tension/near-falsification]. All three are live. Do not schedule it as a rubber-stamp; budget for a possible tension surfacing."
  - "NOT A v1.0 BLOCKER (recommendation): Paper IV's falsifiable result is the KINEMATIC channel (audit row PASS), independent of exp_03. The gauge row is honestly framed operator-exact / observable-OPEN (PART). A v1.0 deposit can ship with the gauge sub-question explicitly open. Recommend NOT gating the paper on exp_03."
  - "R4 READOUT DEFINITION now SETTLED (2026-07-09, user): chosen readout is the STATIC E+B induced-action CANCELLATION SCREEN (extend exp_04's magnetic Wilson-loop extraction to the electric/temporal-plaquette sector; combine into effective epsilon + mu-inverse; test whether the leading photon speed split Delta_v cancels). Spec: paper-04 `notes/exp_03_R4_cancellation_screen_spec.md`. KEY CONSEQUENCE: the screen is a STATIC, SMALL-N operator measurement (exp_04 ran N=20) -- CPU-cheap, does NOT need the GPU/large-N sweep. The 41.5x-GPU story applies to the LATER k-resolved order measurement, not this screen. User has GREEN-LIT implementation of the screen. GPU provisioning was already moot."
  - "SCHEDULING BASIS CHANGED: the '~5.5 h/axis' cost the plan carried is a CPU-path number. Measured GPU speedup on the real box is 41.5x at 128^3 (E+B hop) -> ~8 min/axis, whole sweep in hours not days. Any planning that used 5.5 h/axis CPU is obsolete. See memory `exp03-gpu-feasibility`."
decisions:
  - "RECOMMEND: exp_03 driver is Paper IV scope (this repo's experiment) consuming the already-SHIPPED dcl_core v0.3.0 primitives (Peierls hop, uniform_B_potential, vector/temporal potential threading, GPU RawKernel). NO new dcl-core engine capability is strictly required -- the R4 induced-response readout can be composed experiment-side (density/token diffs + small-field fit), as the reference estimator in dcl-core's test_peierls already does. PM to confirm this split rather than commissioning a new dcl-core feature."
consumed_by:
consumed_at:
---

## Summary
Escalation + capacity finding from the Paper IV focused session. While answering
"can exp_03 run on the existing box?", two facts surfaced that need a PM scope
call: (1) the exp_03 **E+B driver does not exist in either repo** -- only the
magnetic-only cross-check does -- so the load-bearing gauge verdict has nothing
to run yet; and (2) the experiment is now **cheap on the existing GPU** (~hours,
not days), so hardware is not the gate. The two questions for the PM: *do we need
to wait for exp_03*, and *is authoring it within Paper IV's scope?* My worked
recommendation is **no (not a v1.0 blocker)** and **yes (paper-04 scope, no new
engine work)** -- but both are PM calls to confirm.

## Shipped
Nothing committed by this handoff (it is a decision-request). Context/artifacts:
- Paper IV `3de7423` (already handed off): gauge framing corrected to
  operator-exact / observable-OPEN; audit row PART with explicit "why not PASS".
- This session's capacity benchmark: scratchpad `bench_exp03.py` (not committed;
  reproducible). Result recorded in paper-04 memory `exp03-gpu-feasibility`.

## Verification
Capacity benchmark on the real dev box (Ryzen 7 2700, 32 GB, GTX 1060 6 GB,
CuPy 14.1.1, dcl_core v0.3.0 code), Peierls **E+B** hop (uniform B along
(1,1,-1) + electric A_0), block-timed with device sync:

| shape | CPU ms/tick | GPU ms/tick | speedup |
|---|---|---|---|
| 64^3 gauge | 215.9 | 7.3 | 29.6x |
| 128^3 gauge | 1155.3 | 27.9 | **41.5x** |

Memory at the 129^3 design ceiling: ~few hundred MB working set (persistent
session state ~69 MB) -- fits in 6 GB VRAM, let alone 32/64 GB. **Memory is not
a constraint.** The "5.5 h/axis" figure reconciles as a CPU run (~17k ticks/axis);
same axis on GPU ~8 min. Driver-existence verified by exhaustive dcl-core search
(no test-#5 driver; only `exp_04`, N=20; `test_peierls.py:21-27` defers #5).

## Remaining
- **Author the exp_03 driver** (R4 induced-response readout + R5 orientation
  sweep) once scope + R4 definition are settled. With the GPU backend this is a
  hours-scale job.
- **Owner-gated (user):** settle the R4 readout definition (the estimator);
  green-light. (GPU provisioning is done -- GPU works.)
- **Cross-doc (dcl-core session, PM to relay):** design-doc-04 still carries the
  stale "test #4 N-limited" wording and the "test #5 deferred" note; both want
  updating now that #4 is exact/done (`exp_04`) and #5 is GPU-cheap.

## Decisions & flags
See frontmatter. The load-bearing points:

**Do we need to wait for exp_03?** -- *Recommend NO.* Paper IV's clean
frontier-testable falsifiable result is the kinematic dim-6 dispersion (audit row
**PASS**), which does not depend on exp_03. The gauge sector is already framed
honestly as operator-exact / observable-OPEN (**PART**), and a v1.0 deposit can
ship with that sub-question open. exp_03 is the single biggest open item and is
**decisive** (could confirm consistency, yield a new suppressed prediction, or
surface an excluded O(1) tension), so it should be done -- but *because it is now
a ~hours GPU job*, the sensible sequencing is "do it soon, ideally before or just
after v1.0", not "block the paper on it".

**Is it within Paper IV scope?** -- *Recommend YES, as a paper-04 experiment
consuming the shipped engine.* The engine primitives it needs (Peierls hop,
`uniform_B_potential`, temporal+spatial potential threading, GPU RawKernel) all
landed in dcl_core **v0.3.0**. The R4 induced-response readout is composable
experiment-side (density/token diffs vs a zero-field baseline + a small-field
susceptibility fit) -- dcl-core's reference estimator already does this in a test.
So **no new dcl-core engine capability is strictly required**; exp_03 is this
repo's driver against v0.3.0. The alternative (make R4 a reusable, tested dcl-core
engine feature) is defensible but heavier -- PM's call which split we want.

## → Consumer actions
- [ ] **Decide sequencing:** confirm exp_03 does NOT gate Paper IV v1.0 (deposit
      with the gauge sector honestly OPEN), or rule that it does. Recommendation:
      not a blocker; schedule exp_03 soon given it is now GPU-cheap.
- [ ] **Confirm scope split:** exp_03 driver + R4 readout authored in **paper-04**
      consuming dcl_core v0.3.0 primitives (no new engine feature). If instead you
      want R4 as a reusable dcl-core engine capability, file a dcl-core spec/handoff.
- [x] ~~Relay the R4 readout-definition gate to the user~~ **DONE 2026-07-09:**
      R4 settled = static E+B induced-action cancellation screen (Choice 1); spec
      in paper-04 `notes/exp_03_R4_cancellation_screen_spec.md`; user green-lit
      implementation. GPU provisioning dropped (GTX 1060 verified, 41.5x). The
      screen is CPU-cheap/small-N; the GPU sweep is only for the later k-resolved
      order measurement (out of scope for the screen).
- [ ] **Update planning cost basis:** the "5.5 h/axis" is CPU; real GPU cost is
      ~8 min/axis (whole sweep hours). Fix any schedule/ledger that used the CPU
      number.
- [ ] **Board:** update/append the Paper IV gauge-sector issue (repo
      `discrete-causal-lattice-project`, project 6) to reflect: operator Q
      exact/done; exp_03 driver unwritten but GPU-cheap and paper-04-scoped;
      not a v1.0 blocker (pending your ruling).
- [ ] **Cross-doc:** relay a dcl-core design-doc-04 fix (stale "test #4 N-limited"
      + "test #5 deferred") to a dcl-core session -- already noted in the
      2026-07-07 gauge-Q-tensor handoff; this reconfirms it is still pending.
