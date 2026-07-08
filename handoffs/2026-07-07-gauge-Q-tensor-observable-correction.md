---
handoff: 2026-07-07-gauge-Q-tensor-observable-correction
from: dcl-core (focused)
to: PM
repo: JackDMenendez/dcl-core
branch: feature/v0.3.0-peierls-gauge
commits: [599be5e, 0405c36]   # Q-tensor verdict + the GPU kernel it rode on. UNPUSHED (see flag 4).
pr: none
status: open
state: in-progress   # test #4 landed; test #5 (E+B dispersion order) still ahead
semver: 0.2.2 -> 0.3.0 (MINOR, UNRELEASED). exp_04 + a de-xfailed test; no public-API change beyond the v0.3.0 additions already logged.
flags:
  - "FRAMING CORRECTION (the finding): the {4,4,16} Q-tensor verdict (doc test #4) was NOT N-limited / GPU-bound, as design doc 04 and tests/test_peierls.py claimed. That belief came from measuring it via the wavepacket DENSITY response, which robustly gives a 2:1 axis:planar ratio (stable across N, width, momentum, parity) -- a DIFFERENT observable. {4,4,16} is the induced-ACTION (Wilson-loop) tensor: 1-Re W_ab ~= (a^4/2)(V_a.F.V_b)^2 summed over bipartite plaquette planes = F^T Q F. It is a property of the engine's Peierls LINK PHASES and is EXACT in the lattice interior for a uniform field -- no large N. This corrects the doc-04 / Paper IV 'N-limited' language for test #4."
  - "WHAT IS STILL GPU/large-N: only doc test #5 -- the full E+B photon-DISPERSION birefringence-ORDER verdict (O(1) dim-4 vs (ka)^2-suppressed vs null). That one genuinely needs the fused kernel + orientation sweep at scale, and is the load-bearing physics question. Do not conflate it with #4 (now done, exact)."
  - "PAPER IV DOC IMPACT: dcl-paper-04's notes/gauge_sector_structural_conclusion.md and dcl-core/docs/design/04 both carry the 'test #4 is N-limited/GPU-bound' framing. The engine now reproduces Paper I's Q exactly (max|Q-Paper_I_Q|=0) from running code; the 'exp_03 magnetic cross-check' is CONFIRMATORY-and-done, not deferred. The OPEN gauge question is now solely #5 (E+B observability)."
  - "UNPUSHED: commits 599be5e (Q-tensor verdict) and 0405c36 (GPU RawKernel + parity), plus b1a7d35 (gitignore) and 6f940c8 (calibration boundary), are LOCAL on feature/v0.3.0-peierls-gauge; remote is at 0c7ab8f. Nothing has been pushed since. Release stays gated (v0.3.0 not cut)."
  - "REFERENCE PATH: Paper I lives at j:\\dev\\dcl (NOT c:\\dev\\dcl); the cross-check reference is dcl/src/utilities/induced_gauge_action.py. External junctions under dcl-core/external were not present this session."
decisions:
  - "PM to decide whether to fold the framing correction into design doc 04 and relay it to dcl-paper-04 (recommended) -- the 'test #4 N-limited' wording is now factually wrong."
consumed_by:
consumed_at:
---

## Summary
The gauge-sector Q-tensor verdict (Paper IV `exp_03` magnetic cross-check /
design-doc-04 acceptance test #4) is **landed and exact**: core3d's Peierls
coupling reproduces Paper I App. B's induced gauge action tensor
`Q=[[8,4,-4],[4,8,-4],[-4,-4,8]]`, eigenvalues `{4,4,16}`, optical axis
`(1,1,-1)`, with `max|Q - Paper_I_Q| = 0`. The load-bearing finding is a
**correction to how the verdict is measured**: it is a Wilson-loop / induced-
action quantity (exact from the link geometry), not the wavepacket density
response (a distinct observable that gives 2:1, not 4:1) -- so it was never
N-limited/GPU-bound. Only the E+B *dispersion-order* verdict (test #5) still is.

## Shipped (commits, UNPUSHED -- flag 4)
- `599be5e` -- `experiments/exp_04_induced_gauge_Q_tensor.py` extracts Q from
  the engine's Peierls plaquette holonomy and cross-checks
  `dcl/src/utilities/induced_gauge_action.py`; `tests/test_peierls.py`'s
  previously-xfailed `test_magnetic_response_reproduces_Q_eigenvalues_4_4_16`
  is now a real PASSING test. (`exp_04`, not `exp_03`: dcl-core's `exp_03` slot
  is the `prob_floor` diagnostic.)
- `0405c36` -- the fused GPU `hop_average` RawKernel + `tests/test_gpu_matches_cpu.py`
  (CPU/GPU parity, green on a GTX 1060; 4-13x faster than `cp.roll`). Context:
  this is the kernel that DOES unblock test #5; it is not what unblocked #4.

## Verification
- Full suite **299 passed / 1 skipped / 26 xfailed** (was 298 / 27 -- the one
  moved test is the de-xfailed verdict).
- `exp_04` run recorded to `data/exp_04_induced_gauge_Q_tensor.log` (tracked):
  Q exact, eigenvalues `{4,4,16}`, axis `(1,1,-1)`, O_h avg `8I`, `Q_aniso
  {-4,-4,8}`, cross-check PASS.
- Reviews: none additionally run (additive experiment + a test flip; no public
  re-export change beyond the already-reviewed v0.3.0 surface).

## The finding in one paragraph (for relay)
Two different observables were being conflated. (1) The **density response** --
`|psi(+B)|^2 + |psi(-B)|^2 - 2|psi(0)|^2` after a hop -- is uniaxial about
`(1,1,-1)` but has axis:planar ratio ~**2:1**, robust across N/width/momentum/
parity, and is NOT the Q-tensor. (2) The **induced action** -- the bipartite
plaquette holonomy `1 - Re W_ab` of the same Peierls links -- is `F^T Q F` with
eigenvalues `{4,4,16}` = **4:1**, exact in the interior for a uniform field.
Paper I's Q is object (2). The "N-limited/GPU-bound" label was attached to the
verdict while it was being probed with object (1); with object (2) it is exact
and cheap. The genuinely N-bound question is the *full E+B photon dispersion*
(test #5), which asks a different thing (the observable birefringence ORDER),
not the operator-level tensor.

## Remaining
- Doc test **#5** -- the E+B dispersion birefringence-order verdict -- is the
  remaining gauge deliverable; genuinely GPU/large-N (the RawKernel + orientation
  sweep at scale). Not started.
- Release stays gated: v0.3.0 not cut; `_version.py`/`CITATION.cff` still 0.2.2.

## -> Consumer actions
- [ ] Board: on issue **#20** (`018 Core Software core3d v0.3.0`, project 6,
      `discrete-causal-lattice-project`), record that gauge acceptance **test #4
      ({4,4,16}) is DONE exactly** (exp_04, cross-checked vs Paper I), and that
      the remaining gauge item is **test #5** (E+B dispersion order), still
      GPU/large-N. Correct any '#4 is N-limited' note.
- [ ] Relay to **dcl-paper-04**: update `notes/gauge_sector_structural_conclusion.md`
      (and flag `dcl-core/docs/design/04`) -- the magnetic `Q` cross-check is now
      reproduced by running code (not deferred); the OPEN question is solely the
      E+B observability (their §2.3). Optionally cite `exp_04`.
- [ ] Memory (dcl-core session dir): record the density-response (2:1) vs
      induced-action/Wilson-loop (4:1, {4,4,16}) observable distinction, and that
      test #4 is exact from link geometry. Link `[[extensional-calibration-boundary]]`.
- [ ] Gate: do NOT cut v0.3.0; the E+B verdict (#5) and the release flow remain
      ahead. Push decision for the four local commits is the user's.
