---
handoff: 2026-07-16-dpmin-derived-or-fitted-gate
from: PM (dcl-website session)
to: dcl-delta-p-min (focused)
repo: JackDMenendez/dcl-delta-p-min
branch: main
commits: []                         # no code handed off — this routes a research gate for dcl-delta-p-min to answer
pr: none
status: open
state: blocked                      # blocks Paper IV §9 publication; awaits dcl-delta-p-min's derive-or-fit verdict
semver: n/a (research gate, not a software change)
flags:
  - "CIRCULARITY RISK: the Paper IV dimensional-selection novelty claim d_max = 1/δp_min − 1 (δp_min=1/4 → d_max=3) is a TAUTOLOGY if δp_min = 1/4 was chosen to make d_max = 3. The whole novelty (per dcl-mathematics' adversarially-verified sweep) is CONDITIONAL on δp_min being pinned independently of d=3. Answer THIS before Paper IV §9 publishes."
  - "Novelty verdict is NEGATIVE evidence — absence across surveyed reviews, NOT exhaustive. The holographic / entropy-bound (information-per-site) literature was NOT swept and is the likeliest place a closer precedent to a per-node probability-slot dimension argument hides."
decisions:
  - "PM will not let Paper IV §9's dimensional-selection novelty publish until this gate clears (verdict: derived → claim stands; fitted → claim is circular and must be reframed or dropped)."
consumed_by:
consumed_at:
---

## Summary
The dcl-mathematics session (handoff `2026-07-16-dcl-mathematics-lean-formalism-and-dpmin-gate`) ran an adversarially-verified novelty sweep (5 angles, 21 sources, 25 verified claims) and found the **δp_min dimensional-selection mechanism genuinely novel**: no prior work ties spatial dimension to a minimum probability quantum / per-node slot / coordination bound via `d_max = 1/δp_min − 1`. That novelty is **load-bearing but conditional** — it holds only if `δp_min = 1/4` is *derived* (empirically or from first principles), not *fitted* to force `d_max = 3`. This handoff routes the derive-or-fit question to the one repo that can answer it: **dcl-delta-p-min**. Until it answers, Paper IV Section 9's dimensional-selection novelty claim is held.

## Shipped
- None (no code). This is a gate routed from dcl-mathematics → PM → dcl-delta-p-min. The originating evidence lives in dcl-mathematics `notes/prior_work_dimension_from_adjacency.md` (commit `41ab08f`).

## Verification
- n/a for this handoff. The upstream sweep: 75 claims → 25 adversarially verified (2-of-3-refute), 23 confirmed, 2 refuted; `lake build` + `checkdecls` green in dcl-mathematics.

## Remaining
- **dcl-delta-p-min must render the verdict:** is `δp_min = 1/4` pinned *independently* of the d=3 target, or back-solved from it?
  - If **derived** — cite the derivation/measurement; the Paper IV §9 novelty claim stands and can publish.
  - If **fitted** — `d_max = 1/δp_min − 1` is circular; Paper IV §9 must reframe (e.g. as a consistency relation, not a selection prediction) or drop the novelty framing.

## Decisions & flags
See frontmatter. The circularity flag is the entire reason this handoff exists: a fitted δp_min turns a headline novelty into a definitional identity. The negative-evidence flag is secondary but real — even a *derived* δp_min leaves the "no prior art" claim resting on an unswept holographic/entropy-bound corner; tightening that is a related-work follow-up (board issue filed separately), not a blocker on the derive-or-fit verdict itself.

## → Consumer actions
- [ ] **Verdict (the gate):** in dcl-delta-p-min, establish whether `δp_min = 1/4` is derived (empirically / from first principles) or fitted to `d_max = 3`. Write the answer with its justification into the repo, and hand it back to PM (handoff or board comment).
- [ ] Do NOT treat `d_max = 1/δp_min − 1` as an independent dimensional-selection prediction in any Paper IV §9 draft until this verdict is "derived".
- [ ] Board: this is tracked as issue `022` in `discrete-causal-lattice-project` (project 6); update it with the verdict when reached.
- [ ] If helpful to the derivation, coordinate with dcl-mathematics — it now carries the Lean 4 / Mathlib formalism (`src/dcl_formalism/`) where the `d_max` relation and δp_min could be stated as a checked theorem once the input is pinned.
