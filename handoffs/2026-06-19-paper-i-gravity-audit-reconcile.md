---
handoff: 2026-06-19-paper-i-gravity-audit-reconcile
from: PM
to: dcl (focused / Paper I author)
repo: dcl
branch: main
commits: []
pr: none
status: consumed
state: complete
semver: n/a (paper / manuscript)
flags: [audit-table-oversells-einstein-field-equations]
decisions: []
consumed_by: dcl (Paper I) — focused session
consumed_at: 2026-07-20
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
- [x] `notes/deriving_gravity_from_clock_density.md` §"The Honest Gap"
      (lines ~171-206): mark the `exp(−φ/c²)`-from-lattice-dynamics gap
      **CLOSED**, pointing to §7.3 (`boltzmann_clock`) + the detailed-balance
      inputs in §7.6:436-451. The note predates the v1.0 closure.
- [x] `paper/sections/audit_table.tex:124`: soften the target column from
      **"Einstein field equations (§\ref{sec:clock_fluid})"** to match what
      §8.6 admits is open — e.g. **"Continuity equation (Einstein limit
      conjectured, §8.6)"** — OR downgrade the row `PASS → PART`. This aligns
      the authoritative source with the already-conservative site
      `claim-map.qmd:62`.
- [x] If the audit row is reworded, confirm the site claim map still matches
      (it already uses the conservative wording — no site edit expected).

## → Consumed (2026-07-20, dcl focused session)
Done in dcl commit `6d0dec5` on `main` (see `git log -- paper/sections/audit_table.tex`):
- Note "The Honest Gap" marked **CLOSED**, pointing at §7.3
  (`eq:boltzmann_clock`) + the detailed-balance chain. The derivation was
  verified present before marking it closed, not taken on faith.
- Audit target column softened to "Continuity equation; Einstein limit
  *conjectured* (Open questions, §clock_fluid)". Status left `PASS` — correct
  for what `exp_07` shows. Chose the reword over the `PASS → PART` downgrade
  because the row's *evidence* was never in question, only its target.
- Site claim map checked: `dcl-website` already reads "Clock-density
  conservation / continuity equation | Proven | PASS | exp_07". Conservative
  wording confirmed; **no site edit made or needed.**

**Timing caveat:** consumed *after* the Paper I v2.0 Zenodo deposit
(originally 10.5281/zenodo.21460564, 2026-07-20 — that record was later
DELETED and re-deposited as **10.5281/zenodo.21464971**). The *first* v2.0
PDF did **not**
carry these two changes — they land on `main` for the next version. This
handoff was open since 2026-06-19 and was missed at the start of the v2.0
release session. **Recovered by luck:** the v2.0 deposit was redone under a
new DOI after this fix landed, so the *live* v2.0 PDF (21464971) DOES carry
the corrected "Einstein limit conjectured" wording. Only the deleted deposit
shipped the overselling target column.
