---
handoff: 2026-09-10-cubic-taxicab-notes-and-verification-scripts
from: PM
to: dcl-mathematics (focused)
repo: JackDMenendez/dcl-mathematics
branch: main
commits: [403227e]
pr: none
status: open
state: in-progress
semver: n/a (notes, figures and verification scripts; dcl-mathematics is not versioned software)
flags:
  - "THE SOURCE DOCUMENT IS NOT IN GIT. `notes/taxispacehops V1.1.md` through `V1.4.md` are UNTRACKED in the working tree -- `git ls-files` on that path returns nothing. Only `figures/Cubic-Space.drawio` is committed (403227e, pushed; main is level with origin/main). The entire reasoning for the new architecture exists on one machine, in one working tree, with no backup. This is the single most urgent item in this handoff and it costs one commit."
  - "NONE OF THE ELEVEN APPENDIX A SCRIPTS EXIST ANYWHERE UNDER j:\\dev. Searched by name: hop_fpd.py, both68.py, branch68.py, shells_6_12_8.py, greens.py, charge.py, lightcone.py, isotropy.py, confined.py, biased.py, reflbias.py -- all absent. V1.4 section 11.1 nevertheless lists ~14 results as 'already closed by exact computation; do not re-derive' (E[T]=4, the confined-cell rationals, the Green's function coefficient, the step-linear charge no-go, the per-shell moment table, the (ka)^2/18 dispersion anisotropy). Every one of those is currently UNREPRODUCIBLE. This violates the standing discipline that a derivation ships WITH the script that verifies it, and it blocks the whole E-program: until the scripts are back and re-run, section 11.1 is a list of unverified assertions, not closed results."
  - "THE DIAMOND COMPARISON THAT MOTIVATES THE SWITCH IS NOT IN THE DOCUMENT. The stated ground for moving off T^3_diamond is that it is not isotropic. V1.4 never computes T^3_diamond's moments. It computes the cubic 6/12/8 shells -- and what it finds is more nuanced than 'cubic isotropic, diamond not': degree 2 is EXACTLY isotropic for all three cubic shells (off-diagonal exactly 0), and only degree 4 fails. Worse for a naive reading, the pure 8-axis 3x3x3 cell is the WORST option on the board at -44.4%, because with every non-null hop a body diagonal there is no positively-deviating partner to cancel against; the recommended 5x5x5 reflecting cell wins at -0.14% precisely BECAUSE it keeps an axial component. Do not write the motivation up as 'the diagonals are isotropic' -- that is backwards."
  - "REFLECT MEANS s -> -s, NOT c -> c - 2d. V1.4's own 10 Sept correction: an earlier draft implemented 'reflect' as a coordinate mirror (a two-unit point reflection) rather than a wall bounce, and ON THAT BUG reflect produced ugly rationals and was recommended AGAINST. With the correct convention reflect is the best of the three and carries a theorem (section 5.8). Anyone re-deriving section 5.6 from scratch will reproduce the bug unless told. Same warning is on board issue #39."
  - "TWO GATE-ZERO ITEMS REACH PUBLISHED WORK. E0.1 (board #34): the walk gives P(T odd):P(T even) = 2/5 : 3/5 while the framework's tick alternation wants 1/2 : 1/2 (f_beat = 0.5 - f_zitt); if they are the same object, a published claim is wrong. E0.3 (board #36): the hop clock is coordinate time and does NOT dilate -- null-hop rate falls as 1 - 4v^2 where relativity needs 1 - v^2/2, a flat factor of 8 that no reparametrisation of the clock repairs; any published result treating tick count as proper time needs rewriting. Papers I, II and IV are all live on Zenodo. If either fires, the Zenodo re-version protocol applies (new version, revision notice by the abstract, changes table, metadata notice on the old record -- never a silent replace)."
  - "MICHELSON-MORLEY DOES NOT FALSIFY THIS. V1.4 carries a dated correction retracting an earlier draft's claim of falsification at 10^-18; that claim compared the single-tick reachable-set anisotropy against a bound derived from long-wavelength optics, which are different quantities. The observable anisotropy is (ka)^2-suppressed, turning the experiment into a DERIVED BOUND on lattice spacing (a < 0.34 fm at 10^-18) which any Planck- or nuclear-scale lattice satisfies with room to spare. Present it as a strength. Do not let the retracted version propagate into the paper."
decisions:
  - "Code home for the E-program is a NEW core_nd module in dcl-core, not core3d (user, 2026-09-10). core3d stays frozen for reproducibility. Companion handoff: 2026-09-10-core-nd-geometry-as-data-standup."
  - "Board shape is epic + one item per E-item: epic #31 (board 030) plus children #32-#44 (031-043), all Todo on project 6."
  - "Existing In-Progress board items (#7/#8 delta-p-min, #9 core3d upgrade, #27 gauge effective action) were deliberately left untouched. User: 'we will have to review them and sort that out after; some are still appropriate; the main goals stay the same.'"
  - "PUBLICATION GATE (user, 2026-09-10): the math paper and the essay are written AFTER the tests pass, not alongside them. Nothing in this program is written up for publication until the E-program returns verdicts."
consumed_by:
consumed_at:
---

## Summary
The user has defined a new architecture -- the **cubic taxicab sphere**, i.e. the 3x3x3
stencil / BCC 14-neighbourhood -- to replace `T^3_diamond`, on the ground that the old
architecture is not isotropic. The full reasoning, with an ordered validation program, is
in `notes/taxispacehops V1.4.md`; the figure is `figures/Cubic-Space.drawio`, committed
and pushed as 403227e. PM has put the validation program on board 6 as epic **#31
(board 030)** with thirteen children **#32-#44**.

This handoff hands dcl-mathematics the items that live in this repo. The first two are
not research tasks -- they are the reason the rest of the program cannot start.

## Shipped
- `403227e` — `figures: Cubic-Space -- the cubic step-vector figure, dated`. The figure is
  committed and pushed; `main` is level with `origin/main`. It renders the step-vector
  set: `V1..V4` and their negations as the eight body diagonals, plus the axial and face
  labels. This is the only part of the new architecture currently in version control.

## Verification
PM verified the following from the repos themselves, not from the document:

- `git ls-files` on `notes/taxispacehops*` and `figures/Cubic-Space.drawio` returns
  **only** the figure — the four notes files are untracked.
- `git status -sb` on dcl-mathematics reports `## main...origin/main` with no unpushed
  commits, so the figure really is on origin.
- All eleven Appendix A script names searched under `j:\dev` with `find`: **zero hits**.
- `dcl-core/src/dcl_core/` contains `core` and `core3d` only — **no `core_nd`**.

No test suite was run; this is a document-and-scripts state audit, not a code change.
Semver verdict: `n/a` — notes and verification utilities in a non-versioned repo.

## Remaining
Everything in the E-program. Gate zero (board #32, #34, #35, #36) costs hours and needs no
new code. Board #33 (`core_nd`) gates E2 onward and is handed to dcl-core separately. E2
must precede E3: if hydrogen breaks under the confined cell the hop rule changes, and E3
is weeks-to-months of work on that geometry.

## Decisions & flags
See frontmatter; all six flags are load-bearing. The two that must not be skimmed:

**The notes are not in git.** This is not a process nit. Every computed result, every
correction, and the entire argument for the architecture change exist as untracked files
in one working tree. A disk failure or an errant `git clean` ends the program. One commit
fixes it and it should happen before anything else in this handoff.

**Section 11.1 is currently false.** It says fourteen results are closed and must not be
re-derived. With no scripts, none of them can be checked by anyone — including a referee,
including the user in six months, including the next session. The document's own review
discipline (all AIs, multi-round, audit tables that exist to make overclaims visible)
cannot operate on numbers nobody can regenerate. Until the scripts are back and their
output diffed against the document, treat every `[computed]` tag as `[unverified]`.

The third flag is the one most likely to cost a review: the motivation for the switch is
**asserted, not measured**, because the diamond's moments were never computed. Board #37
exists to close that, and it should close before the paper is drafted rather than after a
referee asks.

## → Consumer actions
- [ ] **Board #32 (031), first, before any research work:** commit
      `notes/taxispacehops V1.4.md` to `dcl-mathematics`. Include V1.1-V1.3 if the
      revision history is worth keeping — note V1.4 carries two dated corrections (the
      reflect-convention bug and the Michelson-Morley retraction) whose history is itself
      evidence of the review discipline working.
- [ ] **Board #32 (031), second:** recover the eleven Appendix A scripts if they survive in
      a session workspace; otherwise rewrite them from the document's stated methods.
      Re-run each, diff against the document's published numbers, and commit with a pinned
      environment. Where the document claims exact rationals (the denominator-210
      confined-cell probabilities, `E[T] = 4`, the multinomial first-passage rule), the
      script must emit exact rationals, not floats.
- [ ] **Gate:** do NOT let any downstream work cite a section 11.1 result as closed until
      that re-run reproduces it. If a number fails to reproduce, it comes off the
      do-not-re-derive list and anything resting on it pauses. Report failures to PM.
- [ ] **Board #37 (036):** compute `T^3_diamond`'s degree-2 and degree-4 moments on the
      same footing as the cubic shells — same estimator, same normalisation, same code
      path — and put the number next to the existing table. This is the missing half of
      the switch motivation.
- [ ] **Board #34 (033) — E0.1, hours, no code:** compare the walk's
      `P(T odd):P(T even) = 2/5 : 3/5` against the framework's `f_beat = 0.5 - f_zitt`.
      Same object or not? While the numbers are in hand, also resolve the section 9.5
      near-miss: the exact degree-4 cancelling mixture is *also* 2/5 : 3/5 but with the
      shells **swapped**. Inverted identification, or coincidence of small rationals?
- [ ] **Board #36 (035) — E0.3, hours, no code:** inventory every claim, published or in
      draft, that treats the tick count as proper time or reads the null-hop rate as a
      rest mass. Check Papers I, II and IV (all live on Zenodo), plus dcl-core docs and
      the website.
- [ ] **Escalate to PM immediately if #34 or #36 fires.** Either one triggers the Zenodo
      re-version protocol, which is PM's to run, not the focused session's.
- [ ] **Board #42 (041) and #44 (043)** are formalism items that live here: `pi/3` from the
      `C_3v` stabiliser halved by tick parity, and direction-space vs position-space parity
      independence. Both are late in the sequence — do not start them before gate zero
      clears. Note #42 leans on the tick-parity structure #34 may overturn.
- [ ] **Gate — publication:** do NOT begin drafting the math paper or the essay until the
      E-program returns verdicts. User directive, 2026-09-10: "once we pass the tests, then
      we will write the math paper and an essay." The essay in particular is user-directed,
      and the standing discipline is that a DOI is permanent — PM holds the tempo.
- [ ] **Memory (dcl-mathematics session):** record that the reflect convention is `s -> -s`
      and that the coordinate-mirror implementation is a known bug with a known wrong
      conclusion attached; record that core3d is frozen and `core_nd` is the new code home.
- [ ] **When the scripts land, file a handoff back to PM** stating which section 11.1
      results reproduced and which did not. That verdict gates the rest of the board.
