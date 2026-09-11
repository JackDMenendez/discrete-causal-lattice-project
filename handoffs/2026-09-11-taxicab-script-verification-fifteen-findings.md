---
handoff: 2026-09-11-taxicab-script-verification-fifteen-findings
from: PM
to: dcl-mathematics (focused)
repo: [JackDMenendez/dcl-mathematics, JackDMenendez/dcl-cubic-taxicab]
branch: main
commits: [5141d4a, b85f3ab]
pr: none
status: open
state: complete
semver: n/a (notes + verification scripts; neither repo is versioned software yet)
flags:
  - "EVERY NUMERICAL RESULT IN ALL ELEVEN SCRIPTS REPRODUCED EXACTLY. Not one computed value in V1.4 failed, including the exact rationals (1/21, 4/7, 8/21, 31/7; the denominator-210 confined-cell probabilities; E[T] = 4 from the quotient chain). Section 11.1's fourteen 'do not re-derive' entries are now genuinely closed. All fifteen findings below are in the SURROUNDING LAYER -- prose, provenance tags, cross-references, docstrings, and two moment-weighting errors. That is the good failure mode, but it means the copy needs work in fifteen places before drafting."
  - "F8 -- §8.5's no-go has a FALSE MIDDLE STEP. 'Restoring nonzero charge requires an inversion-breaking subset, and every such subset carries a net drift' is refuted: exhausting all 255 non-empty subsets of the 8-body shell finds 2 inversion-breaking subsets with drift exactly (0,0,0). THE CONCLUSION SURVIVES AND GETS STRONGER. Because every stencil component is in {-1,0,1}, sign(v_i) = v_i, so q(V) = (1,1,1).V EXACTLY -- the charge functional is just the linear functional dotting with the body diagonal. Hence net charge = (1,1,1).(vector sum) for every subset, so charge != 0 <=> the drift has a nonzero (1,1,1) component. Charge IS the (1,1,1)-component of the drift. Replace the asserted universal with this identity."
  - "F11 [MOST CONSEQUENTIAL] -- §9.5's 'Route to §9.4 option 3' NULLS THE WRONG MOMENT, and board #43 (E6) was specified to solve for it. §9.5's table is computed on UNIT VECTORS, but the dispersion's quartic term is Sum p(s)(k.s)^4 = Sum p(s)|s|^4(k.n)^4, weighting each shell by |s|^4 = 1 : 4 : 9. The documented 2/5 : 3/5 axial:body mixture nulls the unit-vector moment exactly and leaves dispersion anisotropy +0.0808 -- LARGER than pure axial's -0.0556, i.e. it makes the observable WORSE. Correct nulling solves (a+3b)/(a+9b) = 3/5, giving 6/7 axial : 1/7 body (confirmed numerically at ~1e-6). Correction already posted to issue #43."
  - "F15 -- §5.8's theorem is stated for 'a confining region of ANY shape', but the reflect rule s -> -s is well-defined exactly on BOXES. On the L1 ball it is undefined: at p = (-3,0,0) a transverse step s = (0,1,0) gives |p+s|_1 = 4 AND |p-s|_1 = 4, because when a coordinate is zero |0+1| = |0-1| -- the norm rises either way. 72 such cases across 48 transient sites. Verified always-legal on cube R=2, the slab, and an asymmetric 3x5x7 box; NOT on the L1 or L2 ball. §5.6 is already careful ('for unit steps in a box'); §5.8 must match it. The recommendation survives -- the 5x5x5 cell is a box -- but the generality that makes it sound 'natural rather than tuned' needs narrowing."
  - "TWO SCRIPT DOCSTRINGS WERE STALE AND ARE NOW FIXED (no numbers changed). lightcone.py carried the RETRACTED falsification-at-1e-18 claim verbatim; reflbias.py claimed 'the induced quotient walk is untouched and E[T] = 4 exactly' for both wall models, which its own output refutes (3.959316 and 4.022767). THE BATCH IS MIXED-VINTAGE -- confined.py is post-correction and carries its own fix note, lightcone.py predates the 10 Sept corrections -- so docstrings must be checked INDIVIDUALLY, never by inference from a sibling."
  - "PUBLICITY RESOLVED (author, 2026-09-11): PUBLIC IS INTENDED. The author's ruling is that the cube should be recorded history, so dcl-cubic-taxicab was flipped to PUBLIC and dcl-mathematics staying public is correct. This SUPERSEDES the earlier caution raised at filing time. The standing embargo distinction (publishable epistemology vs not-yet-publishable architecture) does NOT bind this material -- do not re-raise it for the cubic taxicab work. Note what public means here: the repo README and VERIFICATION-LOG state plainly that this is validation, not adoption, and that the E-program can still kill the architecture. Keep that framing on anything added -- public recorded history is not a publication claim."
decisions:
  - "Author (2026-09-11): dcl-cubic-taxicab is PUBLIC -- the cube is to be recorded history. Created private, flipped public the same day."
  - "Author (2026-09-11): the eleven scripts get a NEW PAPER REPO rather than going into dcl-mathematics. Created as JackDMenendez/dcl-cubic-taxicab (private, main). Rationale: dcl-mathematics' CLAUDE.md scopes the no-code rule to Python numerics and the repo is deliberately paper + Lean (no tracked .py at all), while the program-wide discipline says a derivation ships WITH its verification. A new paper repo satisfies both."
  - "NO PAPER SCAFFOLD was created. dcl-paper-experiment-template still carries the defects its open fix handoff describes -- verified 2026-09-11 that common.mak still has build_dir := build, stage_dir := stage, and VENV := .venv (a venv that was deleted). Deriving from it now would import three known bugs into a new repo. Scaffold lands when 2026-07-22-paper-template-build-discipline is consumed."
  - "Notes committed to dcl-mathematics as 5141d4a (V1.1-V1.4 plus taxicab_as_tensor_product.md). Earlier versions kept deliberately: the revision history containing the reflect-bug fix and the Michelson-Morley retraction IS the review record."
---

## Summary
Board **#32** is complete on both halves. The `taxispacehops` notes are committed and
pushed to `dcl-mathematics` (**5141d4a**), ending a state where the entire argument for
the new architecture existed only as untracked files in one working tree. All eleven
Appendix A scripts were recovered, run, and committed to a new repo
**`JackDMenendez/dcl-cubic-taxicab`** (**b85f3ab**).

**Every number reproduced exactly.** Fifteen findings, none of them a failed computation.
The full log, with the reproducing command for each finding, is `VERIFICATION-LOG.md` in
the new repo.

## Shipped
- `5141d4a` (dcl-mathematics) — `notes:` the five `taxispacehops` files plus
  `taxicab_as_tensor_product.md`. Only those six paths staged; the session's other
  modified files (`CLAUDE.md`, `paper/main.tex`, `notes/accounting_rules.md`,
  `.gitignore`) were deliberately left alone.
- `b85f3ab` (dcl-cubic-taxicab) — the eleven scripts under `src/utilities/`, ten
  independent cross-checks under `src/verification/`, `VERIFICATION-LOG.md`, README.

## Verification
Run on the canonical interpreter `C:\Users\jackd\.venv-win` (Python 3.14.7, numpy 2.5.0,
scipy 1.18.0, sympy 1.14.0). Section-by-section:

- **§5.1** `hop_fpd.py` — 1/21, 4/7, 8/21, E[T] = 31/7, overshoot 0 exactly; weighted
  corner share 3017/18471 = 0.163337. Multinomial rule confirmed: p x 126 = 1 / 3 / 6.
- **§5.3–5.5** `branch68.py` — all eight-decimal figures. Waiting law
  P(T=t) = (1/3)(2/3)^(t-2) confirmed as **exact rationals to t = 14** (document claimed
  t = 8).
- **§5.6** `confined.py` — 3x3x3 E[T] = 5 / 4 / 4 at -44.44% = -4/9; 5x5x5 reflect
  2/5, 61/210, 47/210, 8/105, 1/105 with E[T] = 4 exactly and **-0.1364%**.
- **§5.8** all fifteen table entries, via `check_shape_independence.py` and
  `check_reflect_definedness.py` — but see F15.
- **§6** `both68.py` — 8 + 6 = 14 facets, 24 vertices, {4: 6, 6: 8}, permutohedron 24/14.
- **§7** `shells_6_12_8.py` — Kac 4/4/1/4/4; all five branching rows; all three cells.
- **§8.2/8.3** `greens.py` — G(0) = 1.50933032, all four field rows; coupling 6:3:2.
- **§8.5** `charge.py` — q-multisets, both drift subsets, the sublattice dead end.
- **§9.2/9.3** `lightcone.py` — sqrt(3), cone shapes, all four covariances exactly isotropic.
- **§9.5** `isotropy.py` — direction table, moment table, both mixtures, +4.3410%.
- **§9.6** `biased.py` — every row of both tables, including beta = 6 giving
  **E[T] = 4.000000 at v = 0.990170**.
- **§9.7** `reflbias.py` — tilt covariance 1.1276 / 1.5431 / 3.7622 all STRETCHED;
  wall bias 3.959316 / 0.009596 and 4.022767 / 0.002851.

Semver: `n/a`.

## Remaining
The fifteen findings must be applied to V1.4 before drafting. Board #33 (`core_nd`) and
the E-program are unaffected except #43, already corrected.

## Decisions & flags
See frontmatter. Beyond the five flagged there, ten smaller findings are in
`VERIFICATION-LOG.md`: F1 (the §6 cell *does* close — it fails on volume/tiling, 4.5 vs
the required 4), F2 (Voronoi volume 4 = lattice index = E[T], a new cross-check worth
adding), F3 (retag the permutohedron `[standard]`), F4 (linprog float note), F5 (§5.6
mis-cites §5.4 for the 16% tail), F6 (resolved), F7 (§8.2 **underclaims** — the
coefficient is good to six figures, not three, which settles §8.3's coupling-is-1/D),
F9 (the two drift-free inversion-breaking subsets **are** T^3_diamond's four tetrahedral
directions), F12 (§5.6's -0.14% is measure-dependent; +0.53% under |v|^4 — the
recommendation survives, the superlative does not), F13 ("thirty times better than stay
or resample" is 13.6x; 31x is against the *unconfined* row).

F11 and F12 are **the same error twice** — degree-4 anisotropy computed on unit vectors
then used to reason about observable dispersion. It does NOT recur in §9.7, which works
within the single axial shell where the two measures coincide. So it is specific to
multi-shell mixtures, and the paper wants one explicit statement of which measure answers
which question rather than three local patches.

## → Consumer actions
- [ ] **Apply F8 to §8.5.** Replace "every such subset carries a net drift" with the
      identity `q(V) = (1,1,1).V`, hence `net charge = (1,1,1).(vector sum)`, hence
      charge != 0 <=> nonzero (1,1,1) drift component. Cite
      `src/verification/check_charge_nogo_universal.py`.
- [ ] **Apply F11 to §9.5.** State the `|s|^4` weighting and correct the nulling mixture
      to 6/7 : 1/7. Board #43 already carries the correction; the notes must match.
- [ ] **Apply F15 to §5.8.** "Any box", or "any region on which the reflection is
      defined" — not "any shape". State the L1-ball fallback (reflect-else-stay) that
      actually produced its 4.000000.
- [ ] **Apply F1, F3, F5, F12, F13** — wording, tags and baselines; see the log.
- [ ] **Add F2 and F9 as new content.** F2 (Voronoi volume = lattice index = E[T]) is a
      geometric confirmation of §7.1 from a different direction. F9 reframes board #37:
      T^3_diamond is not a rival architecture outside this one, it is the maximal
      drift-free inversion-breaking subset *inside* the body shell.
- [ ] **Strengthen §8.2 per F7** — six figures, not three. This is what converts
      §8.3's coupling-is-1/D from suggestive to settled, and it is the one result that
      bites on the calibration gap rather than relocating it.
- [ ] **Gate:** do NOT begin drafting the math paper or the essay until the E-program
      returns verdicts (author directive, 2026-09-10). These corrections are for the
      notes, not a licence to start writing.
- [ ] **Board:** #32 (031) can move to Done — both halves are committed and pushed.
- [ ] **Memory (dcl-mathematics session):** record that the verification scripts live in
      `dcl-cubic-taxicab`, not here, and why (this repo's no-Python scoping); and that
      docstring vintage must be checked per-file, never inferred from a sibling.
