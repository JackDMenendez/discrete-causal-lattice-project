---
handoff: 2026-07-18-papers-i-ii-zenodo-reversion-procedure
from: PM (dcl-website session)
to: dcl (Paper I) + dcl-paper-02-sm-derivation (Paper II) — focused
repo: [JackDMenendez/discrete-causal-lattice, JackDMenendez/dcl-paper-02-sm-derivation]
branch: main
commits: []                         # procedure/protocol; no code handed off
pr: none
status: consumed
state: complete
semver: n/a (publication-workflow procedure)
flags:
  - "VERSION, DO NOT SILENTLY REPLACE. Paper IV v1.0's single-domain no-go is a substantive scientific correction to Papers I & II. Zenodo best practice: create a NEW VERSION of each record (own DOI, chain preserved), NOT a file swap under the same DOI and NOT a fresh unrelated upload. Preserve the earlier PDFs unchanged; do NOT withdraw/delete the originals (they document the reasoning that led to the falsifying result)."
  - "PAPER II IS GATED: do NOT start Paper II edits until the paper-04 session files the parked 'shared O_h-average root' handoff (author still deciding Paper II's direction). That handoff also decides Paper II's version bump: v1.1 (add warning + cross-ref) vs v2.0 (revise SM conclusions), depending on whether the SM results materially require the single-domain gauge construction. Paper I is NOT gated by this."
  - "CITE THE CONCEPT DOI: revision notices + bib must cite Paper IV's Zenodo CONCEPT DOI 10.5281/zenodo.21435951 (always resolves to latest), NOT the v1.0 version DOI 10.5281/zenodo.21435952."
  - "THE NO-GO IS BOTH SECTORS: gauge induced-photon common-mode speed anisotropy (O(1)/dim-4, excluded by cavity/MM) AND the matter sector (excluded-as-constructed; the earlier 'matter dim-6-safe' reading is RETRACTED). Revision notices must cover both, not just the gauge anisotropy. Root of both = omission of the 4th cube diagonal V_4=(1,1,-1)."
  - "SCOPE / WHAT SURVIVES: A=1 conservation is NOT falsified (failure traces to the hop-set realization); the adjugate theorem + null birefringence are RETAINED, conditional on the blocks; Bell + other program results untouched. Qualify only the claims that require the single-domain three-diagonal vacuum's phenomenological viability."
decisions:
  - "Author's stated next step: publish new versions of Papers I & II citing Paper IV. This handoff carries the accepted Zenodo re-version procedure (author-provided advice, PM-relayed + DCL-reconciled). Version-number choice is the author's; Paper II's is gated on the O_h-root handoff."
consumed_by: dcl-paper-02-sm-derivation (focused) — Paper II half
consumed_at: 2026-07-21
---

## Summary
Paper IV v1.0 (DOI 10.5281/zenodo.21435952; concept 10.5281/zenodo.21435951) is a
single-domain **no-go** that materially corrects Papers I & II. This handoff carries
the accepted procedure for re-versioning them **honestly on Zenodo** — new versions,
conspicuous revision notices, a changes table, metadata notices on the old records,
explicit record links — reconciled to the DCL facts. Paper I may proceed; **Paper II
is gated** on the parked O_h-average-root handoff.

## Procedure (per record)
1. **New version, not a replacement.** From the existing Zenodo record → *New
   version*; import the earlier files, add the revised PDF, bump the version,
   publish. Never swap the file under the same DOI; never open an unrelated upload.
2. **Conspicuous revision notice inside the PDF**, immediately before/after the
   abstract (not in an appendix). It must distinguish: results that remain
   mathematically valid; claims now made conditional; claims withdrawn; and the
   precise implementation that fails. Cite Paper IV by its **concept DOI**.
3. **"Changes from previous version" table** (one page) — see below.
4. **Metadata status notice on every prior version** (Zenodo allows metadata edits
   without changing the DOI): a prominent first paragraph flagging it is superseded,
   pointing to the new version + Paper IV. This catches readers arriving via the
   old version-specific DOI.
5. **Link the records:** revised I/II cite Paper IV (concept DOI); old records list
   Paper IV as related; Paper IV cites the exact version DOIs it qualifies.
6. **Preserve all earlier PDFs; do not withdraw the originals.**

## Revision-notice text (adapt; both sectors)
**Paper I** (~v2.0 — the finding changes the claimed viability of the specific
three-diagonal construction):
> *Revision notice, July 2026.* Subsequent analysis of the optical-axis gauge
> response shows the original three-diagonal, single-domain A=1 construction
> produces an unsuppressed dimension-four common-mode photon-speed anisotropy,
> excluded as constructed by electromagnetic isotropy (cavity / Michelson–Morley)
> measurements; the matter sector is likewise excluded as constructed. The source
> is the omission of the fourth cube body diagonal V_4=(1,1,-1). The A=1
> conservation formalism and the identified mathematical results are not withdrawn,
> but claims requiring the phenomenological viability of the original three-diagonal
> vacuum are qualified. See Menendez, *Optical-Axis Anisotropy on the A=1 Discrete
> Causal Lattice: Birefringence Cancellation and a Single-Domain No-Go*,
> DOI 10.5281/zenodo.21435951.

**Paper II** (v1.1 or v2.0 — gated; per the O_h-root handoff):
> *Revision notice, July 2026.* This paper identified the (1,1,-1) optical axis but
> did not follow its induced gauge-sector consequence. Subsequent work shows the
> original single-domain three-diagonal hop set yields an order-unity common-mode
> photon-speed anisotropy (and an excluded-as-constructed matter sector), so that
> vacuum construction is excluded as physical. Results depending on that specific
> gauge-sector realization should be read conditionally. See DOI 10.5281/zenodo.21435951.

## Changes-from-previous table (DCL-reconciled)
| Original claim | New status | Reason |
|---|---|---|
| Three-diagonal single-domain A=1 vacuum is phenomenologically viable | **Withdrawn** (as constructed) | Gauge common-mode speed is O(1)/dim-4 anisotropic; excluded by cavity/MM |
| Matter sector safe (dim-6-suppressed) | **Withdrawn / retracted** | Referee M1/M2 (verified exp_05): matter also excluded as constructed |
| Optical axis a suppressed lattice artifact | **Revised** | Enters the induced gauge action at dimension four |
| Adjugate closure + null birefringence | **Retained, conditional on the blocks** | Algebraic theorem valid; blocks-as-dynamical-action = PART |
| A=1 conservation principle | **Unresolved, not falsified** | Failure traces to the hop-set realization (V_4 omission), not A=1 |

## → Consumer actions
- [x] **Paper I session:** prepare the v2.0 revision (notice before/after abstract,
      changes table, bib citing concept DOI 10.5281/zenodo.21435951). The author
      cuts the Zenodo *New version* + the metadata notice on prior records.
      **DONE 2026-07-20** — commit `eef75e3`, tag `v2.0`, GitHub Release cut.
      Notice + changes table placed **immediately before the abstract** (author's
      instruction in the 07-20 addendum). **DOI deviation, author-approved
      2026-07-20:** the notice and bib print the **VERSION** DOI
      `10.5281/zenodo.21435952`, not the concept DOI this handoff's flag
      specified — the author chose version to pin the exact deposit carrying the
      falsifying result. Also folded in the never-deposited v1.03 erratum, and
      added an audit-table row "Single-domain gauge viability → FAIL".
      **Remaining and author-only: the Zenodo *New version* deposit itself** plus
      the superseded-metadata notices on prior records (checklist in
      `release_notes/v2.0.md`).
- [x] **Paper II session — HOLD** until the paper-04 O_h-average-root handoff lands;
      then prepare v1.1/v2.0 per its verdict.
      **DONE 2026-07-21 — but the GATE WAS NOT SATISFIED AS WRITTEN.** The
      paper-04 O_h-average-root handoff was **never filed** (still absent from
      `handoffs/` as of this date; `2026-07-18-paper04-2a-order-result-oh-decision`
      is a different, already-consumed paper-04→PM handoff). The **author
      overrode the gate directly on 2026-07-21**, selecting **v2.0** and
      supplying the pre-reserved DOI. See the successor handoff
      `2026-07-21-paper02-v2.0-published` for the full deviation record.
      Commit `f90447e`, tag `v2.0`, GitHub Release cut, Zenodo new version
      published at **10.5281/zenodo.21477781**.
- [x] Both: preserve prior PDFs; add the metadata status notice to every old Zenodo
      version; link records both ways.
      **DONE 2026-07-21 (author, via Zenodo UI)** — author confirmed the new
      version is published and prior-version metadata carries the notice.
      Not independently verifiable from this session (no Zenodo API access);
      recorded on the author's statement.
- [x] Back to PM when versions are cut (DOIs) so the dcl-website papers pages +
      claim map cite the correct records.
      **DONE 2026-07-21** — filed as `2026-07-21-paper02-v2.0-published`.
      Paper I v2.0 = 10.5281/zenodo.21464971; Paper II v2.0 =
      10.5281/zenodo.21477781.
