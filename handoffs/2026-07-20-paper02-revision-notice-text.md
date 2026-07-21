---
handoff: 2026-07-20-paper02-revision-notice-text
from: PM (dcl-website session)
to: dcl-paper-02-sm-derivation (Paper II author) — focused
repo: JackDMenendez/dcl-paper-02-sm-derivation
branch: main
commits: []                         # exact author-approved revision-notice text; no code handed off
pr: none
status: consumed
state: complete
semver: n/a (paper revision content)
addendum_to: 2026-07-18-papers-i-ii-zenodo-reversion-procedure
flags:
  - "AUTHOR-APPROVED VERBATIM TEXT. Insert the revision notice below IMMEDIATELY BEFORE THE ABSTRACT (not in an appendix); place the changes table on its OWN PAGE. Reproduce verbatim; do not paraphrase."
  - "PAPER II STILL GATED on version + scope: the re-version CUT waits on the paper-04 'shared O_h-average root' handoff, which decides whether Paper II is v1.1 (warning + cross-ref, this notice) or v2.0 (SM conclusions materially reworked because they require the single-domain gauge construction). Prepare the notice + table now; do NOT cut the Zenodo new version until that handoff lands and the author confirms the version bump."
  - "DOI: notice cites the VERSION DOI 10.5281/zenodo.21435952 (author's consistent choice across Papers I & II; defensible — points to the exact v1.0 establishing the result). Concept DOI 10.5281/zenodo.21435951 remains the always-latest alternative if the author prefers."
  - "TABLE ROWS: this is the shared changes table (same as Paper I) WITH the matter row (author-confirmed 2026-07-20). Some rows originate in Paper I / Paper IV (e.g. adjugate closure); the Paper II session should keep each row mapped to an actual Paper II claim, trimming/annotating any that do not apply to Paper II specifically."
decisions:
  - "Author (2026-07-20): place this exact revision notice immediately before Paper II's abstract, with the shared changes table (incl. matter row) on its own page, as part of the Paper II re-version (per the 2026-07-18 procedure handoff)."
consumed_by: dcl-paper-02-sm-derivation (focused)
consumed_at: 2026-07-21
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
- [x] Insert the revision notice verbatim immediately before the abstract; place the
      changes table on its own following page.
      **DONE 2026-07-21** — `paper/sections/revision_notice_v2.tex`, input from
      `main.tex` before `\begin{abstract}`. Text reproduced **verbatim**; the
      author reconfirmed on 2026-07-21 that it stays verbatim and points the
      reader to Paper IV. Notice p1, changes table p2, abstract p3 (verified in
      the built PDF).
- [x] Keep each table row mapped to an actual Paper II claim; annotate/trim rows that
      are Paper-I/IV-specific.
      **DONE 2026-07-21** — rows 1–2 annotated as inherited from Paper I / a
      Paper I+IV claim. The shared table's *adjugate closure and null
      birefringence* row was **dropped** (Paper II makes no such claim) and
      **replaced** with a Paper-II-specific row on the non-abelian
      bipartite-plaquette birefringence corollary (the Q-tensor `{4,4,16}`
      inherited from Paper I). A sixth row, *Substrate geometry of the
      derivation → Superseded*, was added at the author's direction.
      Independently confirmed by the repo's `claim-auditor` agent.
- [x] HOLD the Zenodo re-version cut until the paper-04 O_h-average-root handoff lands
      and the author confirms v1.1 vs v2.0.
      **NOT SATISFIED AS WRITTEN — author override, 2026-07-21.** The
      O_h-average-root handoff was never filed. The author elected **v2.0**
      directly and supplied the pre-reserved DOI, on the stated grounds that
      the derivation is obsolete because the architecture leaves an optical
      axis that is observable but not observed. See
      `2026-07-21-paper02-v2.0-published` flags.
- [x] On cut: new Zenodo version, metadata notice on the prior record, preserve the
      original PDF (per `2026-07-18-papers-i-ii-zenodo-reversion-procedure`); hand
      back to PM with the new version DOI.
      **DONE 2026-07-21 (author, via Zenodo UI)** — v2.0 published at
      **10.5281/zenodo.21477781**; prior-version metadata notice applied.
      Handed back to PM as `2026-07-21-paper02-v2.0-published`.
