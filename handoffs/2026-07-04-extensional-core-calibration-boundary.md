---
handoff: 2026-07-04-extensional-core-calibration-boundary
from: PM
to: dcl-core (focused)
repo: JackDMenendez/dcl-core
branch: main   # directive targets the upcoming unreleased cut; interacts with feature/v0.3.0-peierls-gauge
commits: []    # PM directive — no code shipped
pr: none
status: open
state: in-progress   # directive; design + refactor to be done by dcl-core before the CuPy release
semver: 0.2.2 -> 0.3.0/0.4.0 (level per api-stability-reviewer; UNRELEASED). Landing the boundary BEFORE this cut keeps it a pre-release reshape, not a break of a shipped API — that IS the timing gate.
flags:
  - "TIMING GATE (the whole reason for this handoff NOW): the extensional-core / calibration-boundary refactor must land BEFORE the CuPy/v0.3.0 core3d cut. core3d's last SHIPPED version is v0.1.0 and the new API is unreleased, so reshaping it now is FREE; once released, drawing the wall becomes a breaking change to a shipped contract. Do NOT cut the CuPy release first."
  - "Interacts with the UNMERGED Peierls branch feature/v0.3.0-peierls-gauge (5f816ce code, 0c7ab8f doc; not merged, no PR — see handoff 2026-07-03-paper04-gauge-peierls-cpu-build). Sequence deliberately: merge Peierls first THEN apply the boundary refactor, or fold both into the same cut. Do not let the two collide."
  - "SCOPE (open decision; PM recommends): core3d ONLY now — it is unreleased and free to reshape. `core` is RELEASED at v0.2.2 and is what the Bell (Paper VI) and delta-p-min (Paper III) work pins; retrofitting the wall there is a breaking change to a shipped API, so defer it to `core`'s next MAJOR bump. Confirm core3d-now / core-later."
  - "Most calibration lives DOWNSTREAM today (Bohr/hydrogen calibration in Paper III / dcl-delta-p-min), not inside core3d — which is already an integer-token/tick/hop engine, i.e. largely extensional. So the audit likely finds few leaks; the deliverable is the EXPLICIT typed boundary + a canonical `dcl_core.calibration` module downstream uses instead of ad-hoc constants, NOT a big code rip-out. Do not over-scope."
  - "OVER-ENGINEERING risk: enforcement can be as light as a naming + module convention or as heavy as a full typed-units library. Pick the LIGHTEST thing that (a) makes every calibration crossing explicit and (b) makes the count of independent constants auditable at one boundary. Do NOT block the release on a heavy type-system build."
  - "Easy to get BACKWARDS (the PM did, in the originating discussion): entropy (log W) and distance (hop-count) are EXTENSIONAL — they belong in core, they need no constant. time / energy-in-physical-units / velocity-in-m·s⁻¹ are INTENSIONAL — behind the boundary. Definition of record: dcl-mathematics/notes/extensional_vs_intensional_lattice.md. Enforce it in types; do not rely on memory."
decisions:
  - "PM recommends core3d-only NOW, `core` at its next MAJOR bump. dcl-core to confirm."
  - "PM recommends lightest-viable enforcement (a `dcl_core.calibration` module + naming discipline, optionally phantom/units types), not a heavy typed-units dependency. dcl-core to confirm."
consumed_by: dcl-core (focused) — see return handoff 2026-07-06-v0.3.0-calibration-boundary-landed
consumed_at: 2026-07-06
---

## Summary
Architectural directive to `dcl-core`: before the CuPy/v0.3.0 core3d release cut,
adopt an **extensional-core / calibration-boundary** architecture — keep the engine
**constant-free** (it emits only extensional quantities: ticks, hops, tokens, counts,
amplitudes, and the pure-count derivations entropy/log W and hop-distance), and
**quarantine every calibration behind one explicit, typed boundary** (a
`dcl_core.calibration` module) that is the *only* place a physical-unit conversion
(tick→second, quantum→energy) may happen. This encodes the A=1 program's
extensional/intensional discipline (defined in `dcl-mathematics/notes/extensional_vs_intensional_lattice.md`)
as a machine-checked wall instead of a mental rule — which matters because
calibrations demonstrably "sneak across the boundary in our thinking" (the PM did so
in the very discussion that produced this). Now is the moment because the core3d API
is still unreleased: drawing the wall is free today and a breaking change after the cut.

## Shipped
(n/a — PM directive; no code shipped. Conceptual basis: the DCTT sorting note above,
plus the "one calibration number" thread in
`physics-research/notes/clock_density_entropy_identity.md`.)

## Verification
(n/a — directive.) The api-stability-reviewer and physics-naming-reviewer should be
run on the resulting refactor, and the semver level set from their verdict.

## Remaining (all for dcl-core, before the release cut)
- A design doc capturing the architecture (three layers + enforcement + debt audit).
- An audit of the core3d public API for calibrated/physical-unit leaks.
- A `dcl_core.calibration` module as the single home for constants.
- The scope confirmation (core3d-now / core-later) and sequencing with the Peierls branch.
- The ~3 downstream repos' minor API updates (user: "not a big deal").

## Decisions & flags
See frontmatter. The load-bearing points:
1. **Timing gate** — land the boundary BEFORE the CuPy cut, or it becomes a breaking
   change. This is why the handoff is filed now rather than "someday."
2. **The three layers** (from the DCTT note): (a) **extensional core** = directed
   graph + primitive counts, no constants; (b) **derived-extensional** = entropy
   (log W), decoherence (adjacency − coherence), distance (hop-count), winding —
   *derived but still constant-free*, so they sit WITH core, not in the calibration
   library; (c) **calibration boundary** = the one guarded place constants live,
   converting extensional quantities into physical units (time, energy, length).
3. **The debt audit is the prize** — with every constant forced to one boundary, the
   *count of independent constants there = the count of calibration debts*, and the
   program's thesis is that it should be **one** (the energy-to-coherence number doing
   tick→second and quantum→Joule). A second independent constant appearing at the
   boundary is then a visible flag (a real new scale, or a sneak), not a silent
   assumption. Make "is it really one number?" mechanically auditable.
4. **Don't get it backwards, don't over-build** — entropy/distance are extensional
   (core side); time/energy are intensional (boundary side); use the lightest
   enforcement that makes crossings explicit.

## → Consumer actions
- [ ] **Design doc:** write `dcl-core/docs/design/NN_extensional_core_calibration_boundary.md`
      — the three layers, the enforcement mechanism (module + naming, optionally
      phantom/units types), and the constant-count audit. Cross-link
      `dcl-mathematics/notes/extensional_vs_intensional_lattice.md`.
- [ ] **Audit:** sweep the core3d public API for any physical-unit / calibrated
      quantity; confirm the engine emits ONLY extensional quantities (ticks, hops,
      tokens, counts, amplitudes). List every leak found (expected: few).
- [ ] **Calibration module:** create `dcl_core.calibration` as the ONE home for
      calibration constants; expose them at a single boundary so their count is
      readable (goal: one).
- [ ] **Scope decision:** confirm **core3d-only now / `core`-later** (flag 3). If
      `core` is included, plan its breaking bump separately — do NOT break released
      v0.2.2 that Paper VI / delta-p-min pin.
- [ ] **Sequence:** coordinate with the unmerged `feature/v0.3.0-peierls-gauge` branch
      — merge-then-refactor or fold-into-one-cut; don't collide (flag 2).
- [ ] **Downstream:** enumerate the dependent repos (dcl-delta-p-min / Paper III,
      dcl-paper-04, dcl-paper-06-Bell-test) and the minor API updates each needs; move
      their ad-hoc calibration to `dcl_core.calibration`.
- [ ] **Board:** record on issue **#20** (`018 Core Software core3d v0.3.0`, project 6)
      the timing gate — "extensional-core / calibration-boundary must land before the
      CuPy cut" — or open a dedicated architecture issue and link it to #20.
- [ ] **Gate — do NOT cut the CuPy/v0.3.0 release** until the extensional/calibration
      boundary is in place; releasing first turns a free reshape into a breaking change.
- [ ] **Return handoff to PM** when the design doc + audit land (before the release cut),
      confirming scope and the constant-count found at the boundary.
