---
handoff: 2026-06-19-gauge-spec-residual-isotropy-phrase
from: PM
to: dcl-core (focused)
repo: dcl-core
branch: feat/v0.3.0-peierls-phase1
commits: []
pr: none
status: open
state: in-progress
semver: n/a (design doc)
flags: []
decisions: []
consumed_by:
consumed_at:
---

## Summary
One residual stale phrase in the gauge spec, found while verifying (for Paper
IV) that `04_gauge_field_and_vacuum_response.md` had dropped the retracted
"vacuum-average → isotropy" premise. It HAS (header retraction + §1.1 +
tests #4/#5 all correctly uniaxial/order). The only leftover is a mislabel.

## Shipped
(n/a — directive.)

## Verification
Tests #4 (line 171-172) and #5 (line 178-179) already state "uniaxial — O_h not
restored" / "Not an isotropy test". Only §6 line 222 disagrees with them.

## Decisions & flags
(None — pure doc-consistency fix, no physics/risk.)

## → Consumer actions
- [ ] `docs/design/04_gauge_field_and_vacuum_response.md` §6, **line 222**:
      change "the **precision of the central isotropy result (acceptance test
      #5)**" → e.g. "the precision of the central **birefringence-order**
      result (acceptance test #5)", to match test #5's own definition
      (line 178: "Not an isotropy test — the lattice is uniaxial").
