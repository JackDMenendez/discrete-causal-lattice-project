---
handoff: 2026-07-20-paper02-revision-notice-text
from: PM (dcl-website session)
to: dcl-paper-02-sm-derivation (Paper II author) — focused
repo: JackDMenendez/dcl-paper-02-sm-derivation
branch: main
commits: []                         # exact author-approved revision-notice text; no code handed off
pr: none
status: open
state: in-progress
semver: n/a (paper revision content)
addendum_to: 2026-07-18-papers-i-ii-zenodo-reversion-procedure
flags:
  - "AUTHOR-APPROVED VERBATIM TEXT. Insert the revision notice below IMMEDIATELY BEFORE THE ABSTRACT (not in an appendix); place the changes table on its OWN PAGE. Reproduce verbatim; do not paraphrase."
  - "PAPER II STILL GATED on version + scope: the re-version CUT waits on the paper-04 'shared O_h-average root' handoff, which decides whether Paper II is v1.1 (warning + cross-ref, this notice) or v2.0 (SM conclusions materially reworked because they require the single-domain gauge construction). Prepare the notice + table now; do NOT cut the Zenodo new version until that handoff lands and the author confirms the version bump."
  - "DOI: notice cites the VERSION DOI 10.5281/zenodo.21435952 (author's consistent choice across Papers I & II; defensible — points to the exact v1.0 establishing the result). Concept DOI 10.5281/zenodo.21435951 remains the always-latest alternative if the author prefers."
  - "TABLE ROWS: this is the shared changes table (same as Paper I) WITH the matter row (author-confirmed 2026-07-20). Some rows originate in Paper I / Paper IV (e.g. adjugate closure); the Paper II session should keep each row mapped to an actual Paper II claim, trimming/annotating any that do not apply to Paper II specifically."
decisions:
  - "Author (2026-07-20): place this exact revision notice immediately before Paper II's abstract, with the shared changes table (incl. matter row) on its own page, as part of the Paper II re-version (per the 2026-07-18 procedure handoff)."
consumed_by:
consumed_at:
---

## Summary
The author's exact revision notice for **Paper II**, to sit **immediately before the
abstract**, with the shared changes table (now including the matter row) on its own
page. Concrete content for the procedure in
`2026-07-18-papers-i-ii-zenodo-reversion-procedure`. Paper II's version bump and any
deeper SM-conclusion revision remain **gated** on the paper-04 O_h-average-root
handoff — prepare now, cut the Zenodo version after it lands.

## Revision notice — VERBATIM, place immediately before the abstract
> **Revision notice, July 2026.** This paper identified the (1,1,−1) optical axis
> but did not follow its consequences through the induced gauge-sector response.
> Subsequent work shows that the original single-domain three-diagonal hop set
> yields an order-unity common-mode photon-speed anisotropy and is excluded as a
> physical vacuum construction. Results depending on that specific gauge-sector
> realization should therefore be read conditionally. See
> DOI 10.5281/zenodo.21435952.

## Changes-from-previous table — on its own page (incl. matter row)
| Original claim | New status | Reason |
|---|---|---|
| Three-diagonal A=1 vacuum is phenomenologically viable | Withdrawn | Gauge common-mode speed is O(1) anisotropic |
| Matter sector safe (dimension-six-suppressed) | Withdrawn / retracted | Referee M1/M2 (verified `exp_05`): matter also excluded as constructed |
| Optical axis is a suppressed lattice artifact | Revised | It enters the gauge action at dimension four |
| Adjugate closure and null birefringence | Retained, conditional on blocks | Algebraic theorem remains valid |
| A=1 conservation principle | Unresolved, not falsified by this result | Failure traces to hop-set realization |

## → Consumer actions (Paper II session)
- [ ] Insert the revision notice verbatim immediately before the abstract; place the
      changes table on its own following page.
- [ ] Keep each table row mapped to an actual Paper II claim; annotate/trim rows that
      are Paper-I/IV-specific.
- [ ] HOLD the Zenodo re-version cut until the paper-04 O_h-average-root handoff lands
      and the author confirms v1.1 vs v2.0.
- [ ] On cut: new Zenodo version, metadata notice on the prior record, preserve the
      original PDF (per `2026-07-18-papers-i-ii-zenodo-reversion-procedure`); hand
      back to PM with the new version DOI.
