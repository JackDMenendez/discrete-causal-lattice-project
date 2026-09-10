---
handoff: 2026-09-10-core-nd-geometry-as-data-standup
from: PM
to: dcl-core (focused)
repo: JackDMenendez/dcl-core
branch: feature/v0.3.0-peierls-gauge (current checkout; see flag 1 — branch base is an open decision)
commits: []
pr: none
status: open
state: blocked
semver: 0.3.0 -> 0.4.0 (MINOR, unreleased, PROPOSED — a new user-facing module is MINOR, not PATCH)
flags:
  - "origin/main DOES NOT CONTAIN THE v0.3.0 RELEASE. Verified: `git merge-base --is-ancestor 3175700 origin/main` fails. origin/main's head is 0de7553 ('Add core3d gauge-field requirements'), sitting on top of a CLAUDE.md that still says v0.2.2. The released, DOI-bearing v0.3.0 (3175700, DOI 10.5281/zenodo.21272238) lives only on `feature/v0.3.0-peierls-gauge`, which is EIGHT commits ahead of main and carries the calibration boundary, the U(1) Peierls gauge coupling, the GPU RawKernel path and the {4,4,16} Q-tensor result. BRANCHING core_nd OFF main WOULD BRANCH OFF A TREE WITHOUT ANY OF THAT. Resolve the branch base before writing a line of core_nd. PM recommends merging the feature branch to main first so the released state and main agree, but that is dcl-core's call and it may have a reason main was left behind."
  - "UNPUSHED AND UNCOMMITTED WORK ON THE FEATURE BRANCH. `feature/v0.3.0-peierls-gauge` is ahead of its own origin by one commit (1adbfad, 'core: complete type annotations; mypy --strict clean on py3.12'), and the working tree has modifications (release_notes/zenodo_references.txt, release_notes/zenodo_related_works.txt) plus untracked artifacts (data/exp_00_hop_drift.log, paper_II_v2.0.pdf). Land or park that before starting new work, so a core_nd branch does not inherit someone else's half-finished state."
  - "core3d IS FROZEN. V1.4 section 11.2 says the experiments run 'in core3d'. They must not. core3d is frozen for reproducibility — every published result that depends on it must stay bit-reproducible, and Papers I, II and IV are live on Zenodo. The user's decision (2026-09-10) is that the E-program gets a NEW core_nd module. If some core3d change looks unavoidable, stop and hand back to PM rather than editing the frozen module."
  - "THE ACCEPTANCE NUMBERS ARE NOT YET VERIFIED. V1.4's computed results (E[T] = 4 exactly, the denominator-210 confined-cell rationals, the per-shell moment table, the Green's function coefficient) are the obvious acceptance criteria for core_nd. But NONE of the eleven scripts that produced them exist anywhere under j:\\dev — see companion handoff 2026-09-10-cubic-taxicab-notes-and-verification-scripts, board #32. Do NOT harden a core_nd test suite against those numbers until dcl-mathematics has recovered the scripts and re-run them. If a number turns out not to reproduce, a test suite pinned to it would enshrine the error."
  - "REFLECT MEANS s -> -s, NOT c -> c - 2d. This is an implementation trap with a known wrong conclusion attached. V1.4's 10 Sept correction: an earlier draft implemented the reflecting boundary as a coordinate mirror (a two-unit point reflection) instead of a wall bounce; on that bug the reflecting cell produced ugly rationals and was recommended AGAINST. With the correct convention it is the best construction available and carries a theorem — reflection acts trivially on the Klein-four quotient Z^3/Lambda_BCC, so E[T] = 4 survives confinement of ANY shape. Get this right in the boundary-rule data or core_nd will reproduce the bug and the wrong recommendation."
  - "THE CALIBRATION WALL APPLIES TO core_nd FROM DAY ONE. v0.3.0 established that dcl_core.calibration is the single home for physical units, that core3d holds zero constants and exactly one free debt (tick_seconds), and that a CI tripwire enforces it. core_nd must inherit that discipline rather than re-import constants through the back door — a new module is exactly where such a leak would go unnoticed. The a = c*tick_seconds relation is on MAJOR-watch."
decisions:
  - "core_nd is the code home for the cubic taxicab / BCC E-program (user, 2026-09-10), NOT core3d. This is the era-2 multi-geometry plan being executed: geometry as data, core/core3d frozen for reproducibility."
  - "The cubic / BCC 14-neighbourhood stencil is core_nd's FIRST consumer. The point of geometry-as-data is that a second geometry can be COMPARED against a first rather than replacing it — which is the operational lesson of the single-domain no-go."
  - "Board shape: epic #31 (board 030) plus children #32-#44 (031-043), all Todo on project 6. core_nd is #33 (board 032)."
  - "PUBLICATION GATE (user, 2026-09-10): the math paper and the essay are written AFTER the tests pass. No write-up runs in parallel with the E-program."
---

## Summary
The user has defined a new architecture — the **cubic taxicab sphere** (3x3x3 stencil /
BCC 14-neighbourhood) — to replace `T^3_diamond`, and an ordered program to validate it
before adoption. Source of record is `dcl-mathematics` `notes/taxispacehops V1.4.md` plus
`figures/Cubic-Space.drawio` (403227e, pushed). The program is on board 6 as epic **#31
(board 030)** with thirteen children.

This handoff asks dcl-core for one thing: **stand up `core_nd`, a geometry-as-data module,
with the cubic/BCC stencil as its first consumer.** It is board **#33 (032)** and it gates
E2 onward — nothing in the experimental program past gate zero can run without it.

State is `blocked`, not `in-progress`, for two reasons named in the flags: the branch base
is unresolved, and the acceptance numbers are not yet verified.

## Shipped
Nothing. This is a request handoff — no code was written by PM, and PM does not commit to
dcl-core.

For context, the state core_nd must build on (all on `feature/v0.3.0-peierls-gauge`):
- `3175700` — `release: v0.3.0 (DOI 10.5281/zenodo.21272238)`
- `1adbfad` — `core: complete type annotations; mypy --strict clean on py3.12` (**unpushed**)

## Verification
PM verified the repository state directly:

- `dcl-core/src/dcl_core/` contains `README.md`, `__init__.py`, `_version.py`,
  `calibration.py`, `core`, `core3d` — **there is no `core_nd`**, so the era-2 module is
  still unbuilt.
- Current checkout is `feature/v0.3.0-peierls-gauge`, **8 commits ahead of `main`**.
- `git merge-base --is-ancestor 3175700 origin/main` → **fails**. origin/main head is
  `0de7553`; the commit below it is `238ab40 docs: update CLAUDE.md status -- v0.2.2
  released`. So main is documentation-current for **v0.2.2**, not v0.3.0.
- The `v0.3.0` tag exists locally.
- `git status -sb` → `[ahead 1]` against the feature branch's own remote; working tree has
  two modified `release_notes/` files and untracked artifacts.

No tests were run by PM. Semver verdict: adding a new user-facing module is **MINOR**
(0.3.0 → 0.4.0). Do not tag it PATCH — the program already has one PATCH-tagged release
that added a feature (wcde v0.3.1), and the lesson recorded there is not to sequence a
later bump off a mislabelled tag.

## Remaining
`core_nd` itself, then E2 (board #39) and everything downstream of it. E2 also needs the
frozen hydrogen baseline from board #35, which is dcl-mathematics/PM-side and independent
of this handoff.

## Decisions & flags
See frontmatter; all six flags are load-bearing. The one that will cost real time if
skimmed is the first.

**`origin/main` does not contain v0.3.0.** The released, DOI'd, publicly cited version of
dcl-core is not on the default branch. Anyone who clones dcl-core and branches from `main`
— which is the obvious thing to do when starting a new module — gets a tree with no
calibration boundary, no Peierls gauge coupling, and no GPU path, and will not notice until
something imports a symbol that is not there. This needs a deliberate resolution (merge the
feature branch to main, or record explicitly why main is intentionally behind) **before**
core_nd is branched, not after.

The fourth flag is the subtler trap. The natural way to build core_nd is to pin its test
suite to V1.4's exact rationals — `E[T] = 4`, the denominator-210 hop probabilities, the
moment table. But those numbers currently have **no script behind them anywhere on disk**.
Pinning tests to unverified numbers would convert a documentation claim into an enforced
invariant, which is the wrong direction of travel: the tests would then defend the error.
Wait for board #32.

## → Consumer actions
- [ ] **Resolve the branch base FIRST (flag 1).** Decide whether `feature/v0.3.0-peierls-gauge`
      merges to `main` so that main and the released v0.3.0 agree, or whether main is
      intentionally behind — and if the latter, record why, in `CLAUDE.md` or a handoff
      back to PM. Do not branch core_nd until this is settled.
- [ ] **Land or park the loose work (flag 2):** push `1adbfad`, and commit or stash the
      modified `release_notes/` files and the untracked `data/exp_00_hop_drift.log` /
      `paper_II_v2.0.pdf` before starting new work.
- [ ] **Board #33 (032):** build the `core_nd` geometry-as-data module. Geometry is a data
      record — step set, weights, boundary rule — not code. Express the three cubic shells
      (6 axial / 12 face / 8 body) and the 6/12/8/26 step-set combinations as geometry
      records, and the boundary conventions (stay / resample / reflect) as data.
- [ ] **Gate — the reflect convention (flag 5):** implement reflect as `s -> -s`, a wall
      bounce. NOT the coordinate mirror `c -> c - 2d`. Add a test that distinguishes them:
      under the correct convention the 5x5x5 cell gives `E[T] = 4` exactly and a
      body-diagonal share of exactly 2/5; under the bug it does not.
- [ ] **Cross-check core_nd against core3d on a geometry both can express**, and get that
      passing, before trusting core_nd on a geometry only it can express. This is the whole
      reason for building a second module rather than editing the first.
- [ ] **Gate — do NOT modify core3d (flag 3).** It is frozen for reproducibility and Papers
      I/II/IV depend on it. If a core3d change looks unavoidable, stop and hand back to PM.
- [ ] **Gate — do NOT pin core_nd's test suite to V1.4's numbers until board #32 lands
      (flag 4).** dcl-mathematics is recovering the eleven verification scripts; wait for
      its handoff reporting which section 11.1 results reproduced. Build the module against
      the *structure* meanwhile (Kac's lemma gives `E[T] = [Z^3 : Lambda_BCC] = 4` from the
      lattice index, which is a theorem and can be asserted independently).
- [ ] **Carry the calibration wall into core_nd (flag 6):** zero physical constants in the
      module, `dcl_core.calibration` remains the single unit home, and extend the existing
      CI tripwire to cover core_nd rather than exempting it.
- [ ] **Align with `DclFormalism.Geometry`** — the era-2 plan is Lean-first, so the geometry
      record's shape should follow the formalism rather than being retrofitted to it.
      Coordinate with dcl-mathematics if the two disagree.
- [ ] **Board:** move #33 (board 032) to In Progress on project 6 when work starts, and
      report the semver verdict back to PM (PM proposes 0.4.0 MINOR, unreleased).
- [ ] **Memory (dcl-core session):** record that origin/main does not contain v0.3.0 and
      what was decided about it; record that core_nd exists and that core3d is frozen;
      record the `s -> -s` reflect convention.
- [ ] **Gate — publication:** no paper or essay drafting until the E-program returns
      verdicts (user directive, 2026-09-10).
- [ ] **File a handoff back to PM** when core_nd is standing and the core3d cross-check
      passes. That unblocks board #39 (E2).
