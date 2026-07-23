---
handoff: 2026-07-22-paper-template-build-discipline
from: PM (dcl-website session)
to: dcl-paper-template + dcl-paper-experiment-template (focused) first; then each paper-family repo session (rollout)
repo: [JackDMenendez/dcl-paper-template, JackDMenendez/dcl-paper-experiment-template, JackDMenendez/discrete-causal-lattice, JackDMenendez/dcl-paper-03-tidal-ionization, JackDMenendez/dcl-paper-04-optical-axis-birefringence, JackDMenendez/dcl-paper-06-Bell-test, JackDMenendez/dcl-paper-02-sm-derivation]
branch: main
commits: []                         # discipline + sync spec; reference implementation is dcl-paper-02 f90447e
pr: none
status: open
state: in-progress
semver: template bump at fix (template's call); per-repo syncs are chore commits
flags:
  - "ROOT CAUSE (author-observed, 2026-07-22): focused sessions did NOT discover the Makefile — they built with bare pdflatex inside paper/, and when told 'use the build directory' they INVENTED paper/build/, never learning .build/, .stage/, or versioned PDF naming. A Makefile is not self-discovering; the only thing every session reads at startup is CLAUDE.md. The fix is a CLAUDE.md build contract + standardized machinery + gitignore tripwires — in that order of importance."
  - "REFERENCE IMPLEMENTATION EXISTS: dcl-paper-02-sm-derivation commit f90447e repaired its common.mak — build_dir := .build, stage_dir := .stage, VERSION variable, `promote` emits .stage/<DOC_TITLE>-v<VERSION>.pdf, `clean` removes .build/ ONLY (the old clean would have deleted every released PDF once stage held the durable archive), .build/ gitignored. Port THAT into the template; do not re-derive."
  - "KNOWN-WORST REPO: dcl (Paper I) still carries all three latent defects (build_dir := build / stage_dir := stage; .build unignored; clean deletes the stage dir). Other paper repos: audit against the template — assume drifted until checked. Also fix `VENV := .venv-ucrt64` wherever present (that venv was DELETED; canonical interpreter is the shared C:\\Users\\jackd\\.venv-win per the global env doc / wcde repo-setup)."
  - "TWO TEMPLATES, ONE LINEAGE (author-confirmed 2026-07-22): dcl-paper-template (LaTeX-only scaffold) AND dcl-paper-experiment-template (paper + src/experiments + tests; the source for experiment-flavored repos like dcl-paper-06 and dcl-delta-p-min, and the pattern most paper repos actually follow). The EXPERIMENT template matters MOST here: it carries make env / make tests, which is exactly where the dead `VENV := .venv-ucrt64` bites. Both templates get the same CLAUDE.md contract + machinery; keep their shared common.mak IDENTICAL (byte-for-byte if possible) so there is one build truth, not two."
  - "SEQUENCING: fix dcl-paper-template FIRST (machinery + the CLAUDE.md section below + gitignore), version/tag it; PROPAGATE the identical machinery + contract to dcl-paper-experiment-template (plus its env/tests-specific VENV fix), version/tag it; THEN sync each repo to whichever template it derives from. Per-repo sync = chore commit citing the template version, so drift is detectable later ('reconciled to template vN')."
decisions:
  - "Author (2026-07-22): fix this problem — sessions must stop building ad hoc. PM routing the canonical contract + rollout; wording tweaks are the template session's, but the CONTRACT ITEMS (make-only, .build/.stage, versioned promote, clean-safety, flag-drift-instead-of-improvising) are load-bearing."
consumed_by:
consumed_at:
---

## Summary
Focused sessions keep building papers ad hoc because nothing they read at
startup tells them the build contract: bare `pdflatex` in `paper/`, invented
`paper/build/` dirs, no knowledge of `.stage/` or versioned artifact naming.
Fix at the template: (1) a canonical **CLAUDE.md "Building the paper" section**
every paper repo carries, (2) the **repaired `common.mak`** from Paper II
`f90447e` as the standard machinery, (3) **gitignore tripwires** so stray
in-tree builds are loud. Then a per-repo sync sweep (Paper I is known-worst).
Tracked on the board (project 6).

## The canonical CLAUDE.md section (paste into the template's CLAUDE.md; wording may be polished, items may not be dropped)

```markdown
## Building the paper — READ BEFORE BUILDING ANYTHING

- **`make paper` is the ONLY sanctioned build.** Never run pdflatex / bibtex /
  latexmk by hand, and never build inside `paper/`. Output lands in `.build/`
  (dot-prefixed, gitignored, safe to delete).
- **Release artifacts are versioned and staged:** `make promote` copies the
  built PDF to `.stage/<DOC_TITLE>-v<VERSION>.pdf`. `.stage/` is the durable
  archive — it is what gets attached to GitHub Releases and deposited to
  Zenodo. `VERSION` is set in the Makefile; bump it there, nowhere else.
- **Never create your own build directory** (`build/`, `paper/build/`, etc.).
  The canonical directories are exactly `.build/` (scratch) and `.stage/`
  (durable; `make clean` must never touch it).
- **If this repo's Makefile disagrees with this section**, the repo has drifted
  from `dcl-paper-template` — do NOT improvise around it; flag the drift via a
  handoff in `j:\dev\dcl-project\handoffs\`.
```

## Machinery spec (port from dcl-paper-02 `f90447e`; verify each item)
1. `build_dir := .build`, `stage_dir := .stage` (dot-prefixed, matching the
   on-disk layout actually in use).
2. `VERSION` variable in the Makefile; `promote` emits
   `.stage/$(DOC_TITLE)-v$(VERSION).pdf`.
3. `clean` removes `.build/` ONLY — never `.stage/` (the old behavior would
   have destroyed every released PDF).
4. `.gitignore`: `.build/` ignored; add `paper/*.pdf` (and `paper/*.aux` etc.
   if not already covered) so an ad-hoc in-tree build screams in `git status`
   instead of slipping into a commit.
5. `VENV` → the canonical shared interpreter (`.venv-win` convention per wcde
   repo-setup), not the deleted `.venv-ucrt64`.

## Rollout
- [ ] **dcl-paper-template:** apply the machinery spec + the CLAUDE.md section +
      gitignore; commit, tag/version the template state.
- [ ] **dcl-paper-experiment-template:** propagate the identical machinery +
      CLAUDE.md contract (common.mak kept identical to the paper template), plus
      the env/tests-side fix: `VENV` → the canonical shared `.venv-win`
      convention (never `.venv-ucrt64`, which was deleted). Tag/version it.
- [ ] **dcl (Paper I):** known-worst — all three latent defects present. Sync;
      verify `.stage/` contents (released PDFs) are preserved and ignored-not-
      tracked correctly; chore commit "reconciled to template vN".
- [ ] **dcl-paper-02:** machinery already repaired (`f90447e`) — add the
      CLAUDE.md section + confirm gitignore/tripwires; sync any residue.
- [ ] **dcl-paper-03, dcl-paper-04, dcl-paper-06:** audit against the template;
      sync each (same chore-commit convention). (dcl-paper-08 is archived —
      skip.)
- [ ] **dcl-delta-p-min** (from the experiment template) + repos that borrowed
      the scaffolding (dcl-mathematics?): audit opportunistically when a session
      is next in them; not blocking.
- [ ] Hand back to PM when the template is fixed and again when the sweep is
      done, so the board item can close.
