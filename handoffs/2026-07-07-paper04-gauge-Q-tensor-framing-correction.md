---
handoff: 2026-07-07-paper04-gauge-Q-tensor-framing-correction
from: PM (dcl-website session)
to: dcl-paper-04 (focused)
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: []                         # directive; no paper-04 commits yet — the focused session makes them
pr: none
status: open
state: complete                     # directive is fully specified; execution is the paper-04 session's
semver: n/a (notes/docs; no software change)
flags:
  - "AUTHORITATIVE, not conjecture: this correction is sourced from dcl-core RUNNING CODE (experiment exp_04, `data/exp_04_induced_gauge_Q_tensor.log`), which reproduces Paper I App. B's induced gauge action tensor Q=[[8,4,-4],[4,8,-4],[-4,-4,8]] EXACTLY — max|Q - Paper_I_Q| = 0, eigenvalues {4,4,16}, optical axis (1,1,-1). The existing 'test #4 is N-limited/GPU-bound' wording in notes/gauge_sector_structural_conclusion.md is therefore FACTUALLY WRONG and must be corrected, not softened."
  - "THE CONFLATION (the substance): the {4,4,16} verdict is the induced-ACTION Wilson-loop tensor (bipartite plaquette holonomy 1-Re W_ab = F^T Q F), which is EXACT in the lattice interior for a uniform field — no large N, no GPU. The 'N-limited' belief came from measuring a DIFFERENT observable, the wavepacket DENSITY response (|psi(+B)|^2+|psi(-B)|^2-2|psi(0)|^2), which robustly gives a 2:1 axis:planar ratio (NOT 4:1) across N/width/momentum/parity. Two different observables were conflated. Do not describe test #4 as GPU/large-N in the notes."
  - "STILL OPEN / STILL GPU-BOUND — do not over-claim: only test #5, the full E+B photon-DISPERSION birefringence-ORDER verdict (O(1) dim-4 vs (ka)^2-suppressed vs null), is genuinely GPU/large-N and remains UNRESOLVED. That is the load-bearing physics question (paper-04 §2.3, E+B observability). Falsifiability discipline: the operator-level Q tensor is exact, but observable birefringence is NOT yet established — keep §2.3 framed as the open question."
  - "RELEASE-LIVE: dcl-core v0.3.0 is now published and already installed in the shared virtual environment. Paper IV can use the tagged release directly; do not treat core release availability as a blocker."
  - "CROSS-DOC: the same stale 'test #4 N-limited' wording also lives in dcl-core `docs/design/04` — that is NOT the paper-04 session's file to edit. Flag it for coordination; the PM will relay a design-doc-04 fix to a dcl-core session separately."
decisions:
  - "Relay chosen over PM directly editing paper-04: this session (dcl-website/PM) owns only dcl-project + dcl-website. paper-04 notes/docs are the province of a paper-04 focused session, reached by this handoff."
consumed_by:
consumed_at:
---

## Summary
Relays the gauge-sector framing correction from dcl-core handoff
`2026-07-07-gauge-Q-tensor-observable-correction` to the Paper IV / dcl-paper-04
session. The {4,4,16} induced-gauge Q-tensor verdict (design-doc-04 acceptance
**test #4**, the magnetic cross-check) is **landed and exact** — reproduced by
running code, not deferred, and never actually N-limited/GPU-bound. The
"N-limited" label was attached while the verdict was being probed with the wrong
observable (density response, 2:1) instead of the induced action (Wilson loop,
4:1 = {4,4,16}). Paper IV's notes carry the now-incorrect wording and must be
corrected. Only **test #5** (the E+B photon-dispersion birefringence *order*)
remains genuinely GPU/large-N and open. `dcl-core v0.3.0` is now live and already
installed in the shared virtual environment, so the focused Paper IV session can
use the tagged release directly.

## Shipped
Nothing in paper-04 yet — this is a PM directive. Upstream evidence (in dcl-core,
now released at `v0.3.0` and already available in the shared virtual environment):
`exp_04` extracts Q from the engine's Peierls plaquette holonomy and cross-checks
`dcl/src/utilities/induced_gauge_action.py`; the previously-xfailed
`test_magnetic_response_reproduces_Q_eigenvalues_4_4_16` is now a passing test.

## Verification
Upstream (dcl-core): full suite 299 passed / 1 skipped / 26 xfailed (the one
moved test is the de-xfailed verdict); `exp_04` log records Q exact, eigenvalues
{4,4,16}, axis (1,1,-1), cross-check PASS. No paper-04 verification yet (docs).
Release availability: `dcl-core v0.3.0` is present in the shared virtual
environment.

## Remaining
- The paper-04 doc edits below.
- Test #5 (E+B dispersion order) stays open and GPU-bound — the real remaining
  gauge deliverable; not this handoff's scope to resolve, only to frame correctly.
- No local install step is needed for the focused session; use the shared
  environment's already-installed `dcl-core v0.3.0`.

## Decisions & flags
See frontmatter. Load-bearing: the correction is authoritative (running code,
max|Q-Paper_I_Q|=0); the density (2:1) vs induced-action (4:1, {4,4,16})
observable distinction is the whole substance; and #5 must stay framed as the
open question so the notes do not over-claim observable birefringence.

## → Consumer actions
- [ ] Edit `notes/gauge_sector_structural_conclusion.md`: **remove/correct** the
      "test #4 is N-limited / GPU-bound" wording. State that the magnetic `Q`
      cross-check is **reproduced exactly by running code** (dcl-core `exp_04`,
      max|Q - Paper_I_Q| = 0, eigenvalues {4,4,16}, axis (1,1,-1)) and is
      **confirmatory-and-done, not deferred**. Make the OPEN gauge question
      **solely** the E+B observability (§2.3, the dispersion-order / test #5).
- [ ] Add the density-response (2:1) vs induced-action/Wilson-loop
      (4:1, {4,4,16}) **observable distinction** to the note so the
      "N-limited" framing does not creep back — it was an observable mix-up,
      not a scale limit.
- [ ] Optionally cite dcl-core `exp_04` / `data/exp_04_induced_gauge_Q_tensor.log`
      as the source (note: the dcl-core commit is currently UNPUSHED — cite as
      internal until the v0.3.0 branch is pushed).
- [ ] Falsifiability check: keep §2.3 (E+B observability) framed as the OPEN
      question; the exact result is the operator-level Q tensor only, not
      observable birefringence.
- [ ] Do NOT edit dcl-core `docs/design/04` from the paper-04 repo — the PM will
      relay that design-doc fix to a dcl-core session separately (cross-doc flag).
