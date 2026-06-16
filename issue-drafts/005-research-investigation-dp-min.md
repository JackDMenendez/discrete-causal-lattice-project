## Research investigation

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

A *research investigation* is a forward-looking thread that may
span multiple experiments, papers, packages, and notes.  It is
**not** a single deliverable -- the eventual output may be one
paper, several papers, a section of an existing paper, an audit
row, a new module, a memory entry, or some combination, and
which one isn't known yet.

> *Status update (2026-05-21):* the investigation has been
> elevated to a full subproject and now lives in the
> [`dcl-delta-p-min`](https://github.com/JackDMenendez/dcl-delta-p-min)
> repository.  This research-investigation issue remains valid as
> the *research-thread* shape (open question, phased program, expected
> outputs); the companion new-subproject issue
> (`006-new-subproject-dcl-delta-p-min.md`) is the *vehicle* shape
> (repo, audit-table-from-day-one, deliverables).  Both are filed in
> parallel; status: `in progress` rather than `proposed`.

**Investigation title**

*Minimum-Delta-Probability ($\delta p_\min$) -- Structural Parameter and
Paper~III v1.0 Prerequisite*

**Research question / hypothesis**

Does $\delta p_\min$ (a minimum quantum of probability in the A=1
framework -- whether a probability floor on continuous amplitudes, an
intrinsic granularity from token discretisation, or both) have a
non-zero value that materially affects the framework's predictions?
Specifically:

- Does the Arnold-tongue width $\Delta\omega_\text{tongue}$ have a
  $\delta p_\min$-set floor?
- Does Paper~III's quantum Roche limit
  $M_\text{min}(d) = \Delta\omega_\text{tongue} \cdot d^3 / R_1$
  inherit a $\delta p_\min$ prefactor, or does it change shape entirely?
- Does the atomic ISCO redefine under a "per-direction probability
  drops below $\delta p_\min$" criterion?
- At what $\delta p_\min$ do already-`PASS` audit rows (exp_12 hydrogen
  Bohr radius, exp_09 Arnold-tongue width) stop being recoverable?

The investigation has both a *physics* leg (does $\delta p_\min$ matter?)
and a *publication* leg (does Paper~III v1.0 ship as-is, with a
footnote, or with the $\delta p_\min$ machinery built in?).

**What's known so far** (upstream from existing papers / notes / memory)

- Papers / sections that already establish the prerequisite:
  Paper~I (`exp_09` Arnold-tongue width measurement; `exp_12` hydrogen
  ground-state Bohr-radius agreement); Paper~II (orthogonal -- gauge
  derivation; not directly affected); Paper~III v0.1
  (`notes/quantum_roche_limit.md` analytical thread).
- Audit rows that are already `PASS` and that this depends on:
  hydrogen as joint two-session Arnold-tongue lock-in (Paper~I);
  gradient detuning breaks the joint resonance (Paper~I);
  $\Delta\omega_\text{tongue}$ as a measured quantity (Paper~I).
- Existing notes / memory entries that frame the thread: this issue
  motivates new artefacts -- the memory entry
  `project-delta-p-min-investigation` (drafted alongside this issue)
  and the notes file
  `dcl-paper-03-tidal-ionization/notes/dp_min_investigation.md`
  (drafted alongside this issue).
- Follow-on catalogue entry (if any) in Paper~I's
  `notes/follow_on_implications.md`: not yet catalogued; this issue
  may motivate adding one.

**What's unknown** (the productive gaps)

- *Operational meaning of $\delta p_\min$.*  Probability floor (clamp
  on continuous amplitudes)?  Phase-quantum floor?  Token-budget
  granularity?  All three?  Phase~1 deliverable.
- *Natural value (if any).*  Speculative "$\delta p_\min = 1/4$" comes
  from somewhere -- possibly a token-conservation constraint that the
  planned discrete-probability paper makes precise.  If pinned, Paper~III
  gains a parameter-free sharper prediction.
- *Cross-engine equivalence.*  "$\delta p_\min$ = clamp at $\epsilon$
  in `dcl_core.core`" vs "$\delta p_\min$ = $1/N$ in `dcl_core.core3d`"
  -- physically equivalent or measuring different things?  Determines
  whether the 4-cell investigation grid is true cross-validation or
  two separate experiments.
- *Impact shape on Paper~III.*  Optimistic case: $\delta p_\min$ enters
  as a multiplicative prefactor, $d^3$ scaling survives.  Pessimistic
  case: structural change in the atomic-ISCO derivation requiring
  Paper~III to be rewritten around $\delta p_\min$ from the start.
- *Upper bound from existing PASS rows.*  At what $\delta p_\min$ does
  exp_12's hydrogen-ground-state recovery break?  That number is an
  experimental upper bound on $\delta p_\min$ in the framework.
- *Joint-tick-rule interaction.*  Does $\delta p_\min > 0$ require any
  change to Paper~I's joint-tick rule?  Unlikely but unconfirmed.

**Connection to existing artefacts** (where this thread plugs in)

- Memory entry to extend / create: *new* --
  `project-delta-p-min-investigation`.
- Audit rows touched (which paper, which rows):
  - Paper~III (`paper/sections/audit_table.tex`): expand the existing
    `STUB` row "Numerical confirmation: monotone $T_\text{escape}(g)$
    + sharp drop near $g_\text{crit}$" into a 4-cell grid (2 engines
    $\times$ $\pm \delta p_\min$).  Similarly the
    tidal-displacement-signature row.
  - Paper~III: new audit row(s) for the cross-engine equivalence
    finding (PASS if cells agree; PART if equivalence holds within
    error bars; FAIL or new STUB rows if cells disagree).
  - Paper~III: possibly a new audit row for the Arnold-tongue width
    floor finding (Phase~1 / Phase~2 result).
- Modules touched:
  - `dcl_core` -- add `prob_floor` parameter to `dcl_core.core`
    (the continuous-amplitude engine).  Additive; minor release bump
    (e.g.\ v0.2.0).  `dcl_core.core3d` already has the parameter
    intrinsically via the token budget $N$.
- Cross-repo dependencies: this investigation triggers a `dcl-core`
  release (the `prob_floor` parameter addition) which then triggers
  a pin-bump in Paper~III's `virtual-env-requirements.txt` per
  `project-cross-repo-release-coordination`.

**Expected eventual output** (one or more -- the shape may evolve)

*A new paper in the series*:

- [ ] Proton internals (memory: `project-proton-internals-downstream`)
- [ ] Discrete-probability paper (memory:
      `project-discrete-probability-paper`) -- *plausible eventual
      cite-target for $\delta p_\min$'s natural value; the
      discrete-probability paper may be where $\delta p_\min$ is
      pinned by a token-conservation constraint*.
- [ ] `dcl-formalism` package paper (memory:
      `project-a1-formalism-package`)
- [ ] Hilbert-6th axiomatization (Paper~I follow-on \#18) -- *the
      capstone consumes dcl-mathematics's limit operators; if
      $\delta p_\min$ enters those structurally, the capstone surfaces
      it.*
- [ ] another Paper~I follow-on (cite #__): _______________________
- [ ] new paper not in the catalogue yet:
      _______________________

*Or a contribution to existing artefacts:*

- [x] new section in an existing paper: Paper~III paper-text section
      discussing the 4-cell grid results, cross-engine comparison, and
      $\delta p_\min$ sensitivity (Phase~4 deliverable).
- [x] new audit row(s) in an existing paper: 4-cell grid expansion of
      Paper~III's numerical-confirmation rows (see "Connection to
      existing artefacts" above).
- [x] new `notes/<topic>.md` file(s):
      `dcl-paper-03-tidal-ionization/notes/dp_min_investigation.md`
      (drafted alongside this issue);
      `dcl-paper-03-tidal-ionization/notes/dp_min_observational.md`
      (Phase~3 deliverable -- observational signatures of
      $\delta p_\min$);
      `dcl-mathematics/notes/discrete_to_continuum_limits.md` (may need
      $\delta p_\min$ subsection in Phase~1 if structural).
- [x] new memory entry: `project-delta-p-min-investigation` (drafted
      alongside this issue).
- [x] new module in `dcl_core` / `dcl_formalism`: `prob_floor`
      parameter on `dcl_core.core`.
- [ ] new experiment(s) `exp_NN`: not anticipated; the investigation
      uses existing experiments (exp_09, exp_12, exp_18) with the new
      `prob_floor` parameter.
- [ ] new figure / animation / research-artifact: possible Phase~2
      figure -- $g_\text{crit}(\delta p_\min)$ across the 4 grid cells
      -- would land in `paper/figures/` of Paper~III.
- [x] structural finding that doesn't fit any of the above: if
      cross-engine equivalence FAILS, that finding is itself
      load-bearing for both `dcl-core`'s architecture and
      `dcl-mathematics`'s discrete-to-continuum-limit treatment;
      escalation path TBD.

**Investigation program** (phased plan; expand as the thread matures)

- [ ] **Phase~1: Theoretical pass** (~1-2 days).  Pin $\delta p_\min$'s
      precise meaning; verify consistency with PASS audit rows
      (exp_12, exp_09 must not become FAIL); work out cross-engine
      equivalence between `dcl_core.core`'s clamp and
      `dcl_core.core3d`'s token granularity.  Lock the audit-row
      taxonomy choice for the Phase~2 grid.
- [ ] **Phase~2: Numerical probe** (~3-5 days).  Coordinate with
      `dcl-core` to add `prob_floor` parameter on `dcl_core.core`;
      release v0.2.0 (or equivalent).  Run the 4-cell grid on both
      engines, sweeping $\delta p_\min$ from $10^{-10}$ to $1/4$.
      Run exp_12 with varying $\delta p_\min$ to find the upper bound
      from the existing hydrogen-ground-state PASS row.  Flip
      Paper~III audit rows from STUB to PART/PASS as evidence lands.
- [ ] **Phase~3: Observational signatures** (parallel, longer).
      Identify experiments that could pin $\delta p_\min$ externally
      (CMB small-angular scales; quantum precision tests; single-photon
      counting).  Non-blocking for Paper~III v1.0; populates
      `notes/dp_min_observational.md` for a future follow-on.
- [ ] **Phase~4: Paper~III stance decision and revision**.  Decide
      whether Paper~III incorporates $\delta p_\min$ as a parameter or
      assumes $\delta p_\min \to 0$ with a footnote.  Revise paper-text
      and audit table accordingly.  Bump `dcl_core` pin to the v0.2.0
      tag in Paper~III's `virtual-env-requirements.txt`.  Deposit v1.0
      per `project-cross-repo-release-coordination`.

**Notes that may be created or updated**

- *New:* `dcl-paper-03-tidal-ionization/notes/dp_min_investigation.md`
  -- the working document; drafted alongside this issue.  Updated as
  the investigation proceeds.
- *New (Phase~3):*
  `dcl-paper-03-tidal-ionization/notes/dp_min_observational.md` --
  observational signatures of $\delta p_\min$; entry point for a future
  follow-on paper.
- *Possibly updated:*
  `dcl-mathematics/notes/discrete_to_continuum_limits.md` -- if
  $\delta p_\min$ has structural role in the limit; cross-cite
  upstream of the Hilbert-Sixth capstone.

**Tools / resources needed** (anything not currently in hand)

- [ ] better CPU (specify): _______________________
- [ ] better GPU (specify): _______________________
- [ ] more memory / disk
- [x] longer wall-clock budget (estimate): ~5-7 days total for
      Phases~1-2 (theoretical + numerical); Phase~3 is parallel and
      non-blocking.
- [ ] dataset access (specify): _______________________
- [ ] subscription / paid software (specify): _______________________
- [ ] collaborator with specific expertise (specify):
      _______________________
- [x] sympy / `dcl_formalism` primitive that doesn't exist yet: the
      `prob_floor` parameter on `dcl_core.core`'s amplitude-update
      primitives.  Additive; minor release.
- [x] other: a `dcl-core` v0.2.0 (or equivalent) release before
      Phase~2 numerics begin in earnest.

**Dependencies / blockers**

- *Productively start:* nothing blocks Phase~1.  Theoretical pass uses
  only existing material (Paper~I, Paper~III v0.1, `dcl-core` v0.1.0-dev).
- *Phase~2 numerics:* requires `dcl-core` v0.2.0 (or equivalent) with
  the `prob_floor` parameter on `dcl_core.core`.  Coordinated release
  per `project-cross-repo-release-coordination`.
- *Phase~4 Paper~III deposit:* requires Phase~1-2 outcomes plus the
  pin-bump workflow described in Paper~III's
  `release_notes/README.md`.
- *Phase~3 observational work:* non-blocking; can run anywhere on the
  calendar.

**Status**

- [x] proposed (idea-stage; question is interesting but unscoped)
- [x] scoped (the productive question and rough program are written
      down here)
- [ ] in progress (active work happening in some repo / memory file)
- [ ] paused (waiting on a dependency from another thread)
- [ ] mature (about to graduate into a paper / module / audit row)

*(Status note: at issue-filing time, the investigation is `scoped`.
Phase~1 starts as soon as the user begins the theoretical pass;
flip to `in progress` then.  Phase~4 graduation is when Paper~III
v1.0 deposit lands with the $\delta p_\min$ stance committed.)*

**Additional context**

- *Why this is a Paper~III v1.0 prerequisite, not a follow-on.*  The
  central derivation has multiple load-bearing places where
  $\delta p_\min$ could enter (5 impact channels enumerated in
  `notes/dp_min_investigation.md` and `project-delta-p-min-investigation`
  in memory).  Publishing v1.0 with $\delta p_\min$ implicit risks a
  $\delta p_\min$-aware correction six months later -- avoidable now
  with ~1 week of focused investigation.
- *Why investigation, not paper-enhancement or experiment-feature.*  The
  thread spans multiple repos (`dcl-core`, Paper~III, possibly
  `dcl-mathematics`), multiple existing experiments (exp_09, exp_12,
  exp_18), and produces multiple outputs (audit rows, a new engine
  parameter, paper-text sections, possibly a follow-on paper on
  observational signatures).  The research-investigation template is
  shaped for that multi-output, multi-repo structure; the narrower
  templates would force a premature framing decision.
- *Speculative downstream cite-target.*  The planned discrete-probability
  paper may be where $\delta p_\min$'s natural value gets pinned (e.g.\
  by a token-conservation constraint).  If so, the order is:
  (1) this investigation surfaces $\delta p_\min$ as load-bearing;
  (2) the discrete-probability paper fixes its value;
  (3) Paper~III's prediction sharpens to a parameter-free numerical
  bound; (4) the Hilbert-Sixth capstone synthesises the chain.  This
  ordering is speculative at issue-filing time but worth holding open.
- *Risks.*  (a) Cross-engine equivalence may fail, forcing two separate
  experiments and a longer paper-text discussion.  (b) Phase~2 may
  reveal that $\delta p_\min$ has *no* effect on $g_\text{crit}$ within
  measurement precision, leaving the framework's natural value
  undetermined; Paper~III then ships with the footnote and the
  investigation continues as a longer thread.  (c) The "1/4" speculation
  may be wrong; the discrete-probability paper may pin a different
  value (or none).  Each risk is captured here so future-self / future
  Claude can revisit framing without rediscovering the trade.
