---
handoff: 2026-06-19-paper-iv-note-spec-revised
from: PM
to: dcl-paper-04 (focused)
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: []
pr: none
status: consumed
state: in-progress
semver: n/a (tracking note)
flags: [claude-md-note-asserts-stale-blocker]
decisions: []
consumed_by: dcl-paper-04 (focused)
consumed_at: 2026-07-09
---

## Summary
Paper IV's `CLAUDE.md` carries a stale tracking note that asserts a blocker
which no longer exists: it says the dcl-core gauge spec still needs revising
before implementation. The spec was revised 2026-06-16 and implementation
(v0.3.0 Phases 1–2) already proceeded against the corrected premise.

## Shipped
(n/a — directive.)

## Verification
- `dcl-core/docs/design/04_gauge_field_and_vacuum_response.md` header (lines
  3-6) + §1.1 (40-48) retract the "vacuum-average → isotropy" premise
  (dated 2026-06-16); acceptance tests #4/#5 require **both E+B** and target
  the birefringence **order** on a **uniaxial** lattice.
- v0.3.0 Phase 2 (handoff `2026-06-19-v0.3.0-phase2`, consumed) reports test #4
  uniaxial+prolate about (1,1,-1) — i.e. built on the corrected premise.

## Decisions & flags
- **`claude-md-note-asserts-stale-blocker` (FLAG).** `CLAUDE.md:117-120` reads
  "the spec still carries the old 'vacuum-average → isotropy' premise … needs
  revising before implementation." FALSE now — a reader treats a closed
  owner-gated item as an open blocker.

## → Consumer actions
- [ ] `CLAUDE.md` ~:114-126: update the owner-gated list — mark item **(1)
      review + revise the spec** as **done** (spec revised 2026-06-16: isotropy
      premise dropped, E+B required, target = birefringence order). Remove/soften
      the ":117-120" claim that the spec "still carries the old premise — needs
      revising before implementation."
- [ ] (Note: items (2) R4 readout, (3) GPU/parallelism provisioning, (4) green
      light remain as-is — only item (1)'s "spec stale" claim is wrong.)
