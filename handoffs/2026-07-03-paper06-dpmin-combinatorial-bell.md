---
handoff: 2026-07-03-paper06-dpmin-combinatorial-bell
from: dcl-core (author)
to: PM
repo: JackDMenendez/dcl-core        # author-reasoning home; recorded in dcl-core memory
branch: main
commits: []                         # physics/design finding; no code shipped
pr: none
status: open
state: blocked                      # Paper 06 CHSH run still blocked, but the MECHANISM is now identified
semver: n/a (physics/design finding; may later yield a core3d joint-session capability — future MINOR, TBD)
flags:
  - "REFRAMING (supersedes any 'resolution window / parameter tension' language): dp_min is NOT a tunable parameter in tension with the Bell requirement — it IS the mechanism that satisfies it. A shared finite token budget partitioned over the JOINT product configuration space is a combinatorial (multinomial) object; the joint collapse is a combinatorial RECOUNT of that budget = a single function of the current state = INSTANTANEOUS = exactly the nonlocal, non-dynamical joint projection a CHSH violation needs."
  - "ROOT CAUSE of the CHSH gap is the REPRESENTATION, not the collapse. Paper 06's core_measurement_requirements.md uses ONE global chirality Bloch vector per session + a scalar enforce_joint_unity — that is a product / direct-sum state, so P(A,B|a,b) factorizes and S<=2 with or without prob_floor. The P1-P4 measurement primitives are correct and useful but the fix is UPSTREAM of them."
  - "The partition MUST be over JOINT product cells (ONE shared budget). Marginal per-session budgets can never entangle, regardless of prob_floor. This is the surviving piece of the entangled-pair-preparation-gap: the preparation must be a joint-combinatorial shared-budget object, not two independently-normalized sessions."
  - "Continuum limit dp_min -> 0 dissolves the mechanism (joint object -> continuum, recount -> integral) => S -> 2. So the CHSH violation is INTRINSICALLY a discrete-probability effect — this is the paper's thesis, now with a reason, not a coincidence."
  - "Engine-placement fork is OPEN (author decision pending): a new core3d joint-session capability (large; core3d has NO pairwise/multi-session coupling today) vs a reduced 2-qubit shared-budget object layered above sessions. Gates whether min-dp can host the Bell test."
decisions:
  - "Author (Jack) confirmed 2026-07-03: dp_min solves the Bell requirement because the discrete joint distribution is combinatorial and therefore the joint collapse is instantaneous. This answers the two long-open questions from handoff 2026-06-27-entangled-pair-preparation-physics-gap: Q2 (tensor structure comes FROM the combinatorics of one shared discrete budget over the product grid) and Q3 (yes, discreteness does the work)."
  - "The 2026-06-27 hypothesis ('prob_floor on a shared budget makes the joint collapse non-factorizable') is correct IN SPIRIT, but only when the budget is joint-combinatorial (product cells). Applied to marginal per-session budgets (the current placeholder) it cannot work."
consumed_by:
consumed_at:
---

## Summary
This is the author's return answer to the open Paper 06 physics gap (handoff
`2026-06-27-entangled-pair-preparation-physics-gap`), recovered and sharpened
after a crash ate the original session. Headline: **the minimum probability
quantum `dp_min` (= 1/N; `prob_floor` in `core`) is not a parameter to tune
against the Bell test — it is the very thing that MAKES the Bell test
expressible on the A=1 lattice**, because a discrete joint distribution is a
combinatorial object and a combinatorial joint collapse is instantaneous
(nonlocal, non-dynamical) by construction. This unblocks the conceptual design
of Paper 06's CHSH gate and means `dcl-delta-p-min` CAN host a CHSH column in
its 4-cell grid — once the joint-combinatorial preparation + measurement exist.

## The finding (precise)
1. **Combinatorial joint state.** In A=1, `N` indistinguishable tokens spread
   over the JOINT (product) configuration space is a finite multinomial object,
   finite because `dp_min = 1/N > 0`. Genuine entanglement (e.g. the singlet,
   zero RR/LL over the 4 joint chirality cells) is a non-product partition of
   that one shared budget.
2. **Instantaneous joint collapse.** Measuring A and repartitioning the shared
   floored budget is a combinatorial RECOUNT — one evaluation of the current
   joint state, not a signal propagated by causal hops. Combinatorial ⇒
   instantaneous ⇒ the nonlocal projection CHSH needs (with a no-signalling
   check on marginals). Causal-hop propagation would be a local-hidden-variable
   model (S<=2) and would signal — so it must NOT be built dynamically.
3. **`dp_min` supplies both.** Discreteness makes the joint object finite-
   combinatorial and the collapse a finite recount. `dp_min -> 0` ⇒ continuum ⇒
   integral ⇒ mechanism gone ⇒ `S -> 2`. The violation is a discrete-probability
   effect by construction (paper's thesis, explained).
4. **Why today's design can't show it.** Two global per-session Bloch vectors +
   a scalar joint-norm keep MARGINAL budgets — a product state. No joint recount
   happens; it factorizes; `S <= 2` regardless of `prob_floor`. Root cause is the
   representation, not the collapse rule. P1-P4 stay correct; the gap is upstream.

Durable record: dcl-core memory `entangled-pair-preparation-gap` (updated
2026-07-03 with this reconstruction). Cross-refs Paper 06
`notes/core_measurement_requirements.md` and the `dcl-delta-p-min` 4-cell grid.

## Remaining
- **Author decision:** the engine-placement fork (core3d joint-session capability
  vs reduced 2-qubit shared-budget object above sessions).
- **Then implement:** a joint-combinatorial shared-budget PREP (singlet over
  product cells) + an INSTANTANEOUS `measure_pair(mode=joint)` = combinatorial
  recount + no-signalling check. CHSH estimator / angles / figures stay in
  Paper 06.
- **Then:** `dcl-delta-p-min` can add the CHSH column (Paper 06 becomes a
  `dp_min` cell) — the thing this whole thread was blocking.

## Decisions & flags
See frontmatter. The load-bearing correction for any downstream reader: **do not
carry the earlier 'resolution window / dp_min-in-tension' framing** (an
intermediate wrong turn). The right statement is dp_min-IS-the-mechanism.

## → Consumer actions
- [ ] **Board:** on the Paper 06 Bell issue (#21, prefix 019 "Core Software core
      spin-measurement primitives", project 6), record: (a) `dp_min` is the
      mechanism (combinatorial ⇒ instantaneous), (b) root cause is the
      representation (product/direct-sum), not the collapse — P1-P4 are correct
      but insufficient, (c) the CHSH gate is blocked on a joint-combinatorial
      shared-budget prep + instantaneous joint measure, NOT on P1-P4.
- [ ] **Board:** open (or note on #21) the OPEN engine-placement decision —
      core3d joint-session capability vs reduced 2-qubit shared-budget object —
      as the load-bearing fork; link to the `dcl-delta-p-min` investigation.
- [ ] **Memory:** the finding lives in dcl-core memory
      (`entangled-pair-preparation-gap`); PM record the durable fact in project
      memory and cross-link `project-delta-p-min-investigation` (the 4-cell grid
      that gains a CHSH column once the joint prep lands).
- [ ] **Gate:** do NOT wire `prepare_pair()` to the current direct-sum
      placeholder and run the gate expecting `S>2` — it reads `S<=2` for the
      wrong reason. The prep must be the joint-combinatorial shared-budget object.
- [ ] **Relay:** notify the Paper 06 and `dcl-delta-p-min` sessions that the
      return answer to `2026-06-27-entangled-pair-preparation-physics-gap` is
      delivered (dp_min mechanism), and that min-dp can host the Bell test as a
      combinatorial cell once the joint prep + measure are implemented.
