---
handoff: 2026-06-19-paper-i-gravity-audit-reconcile
from: PM
to: dcl (focused / Paper I author)
repo: dcl
branch: main
commits: []
pr: none
status: open
state: in-progress
semver: n/a (paper / manuscript)
flags: [audit-table-oversells-einstein-field-equations]
decisions: []
consumed_by:
consumed_at:
---

## Summary
Two honesty/consistency cleanups in Paper I's gravity material, surfaced when
PM reconciled the (now confirmed) clock-density gravity derivation. The
derivation is real (Newtonian limit closed in `gravity_as_clock_density.tex`
§7.3 via detailed balance); these are doc-consistency fixes, not physics gaps.
Both target files are clean on `main`.

## Shipped
(n/a — directive.)

## Verification
- §7.3 (`subsec:newtonian_limit`) derives `ρ_clock ∝ exp(−φ/c²)` from detailed
  balance on the bipartite hop (structural inputs in §7.6:436-451) — closing
  what the note still calls an open gap.
- Site `claim-map.qmd:62` already states the conservative target ("Clock-density
  conservation / continuity equation", PASS, exp_07) — so the public site does
  NOT carry the overclaim; only Paper I's own audit table does.

## Decisions & flags
- **`audit-table-oversells-einstein-field-equations` (FLAG).**
  `paper/sections/audit_table.tex:122-126` row "Clock density conservation"
  lists the **target column = "Einstein field equations (§clock_fluid)"** as
  `PASS` (via exp_07). But the continuity→EFE reduction (`T^μν=f(ρ,J)`, the
  `f` form) is NEVER derived and is listed under §8.6 Open questions. The PASS
  is honest for exp_07 *conservation*; the *target* oversells. The claim-map
  discipline treats audit tables as authoritative, so a future audit-table→site
  sync would re-introduce the overclaim to the (currently honest) site.

## → Consumer actions
- [ ] `notes/deriving_gravity_from_clock_density.md` §"The Honest Gap"
      (lines ~171-206): mark the `exp(−φ/c²)`-from-lattice-dynamics gap
      **CLOSED**, pointing to §7.3 (`boltzmann_clock`) + the detailed-balance
      inputs in §7.6:436-451. The note predates the v1.0 closure.
- [ ] `paper/sections/audit_table.tex:124`: soften the target column from
      **"Einstein field equations (§\ref{sec:clock_fluid})"** to match what
      §8.6 admits is open — e.g. **"Continuity equation (Einstein limit
      conjectured, §8.6)"** — OR downgrade the row `PASS → PART`. This aligns
      the authoritative source with the already-conservative site
      `claim-map.qmd:62`.
- [ ] If the audit row is reworded, confirm the site claim map still matches
      (it already uses the conservative wording — no site edit expected).
