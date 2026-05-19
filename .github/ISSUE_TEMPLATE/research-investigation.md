---
name: Research investigation
about: Capture a forward-looking research thread -- multi-experiment, multi-paper, no single deliverable yet
labels: research, investigation
---

## Research investigation

> *Checkbox tip:* `[ ]` = unchecked, `[x]` = checked.  Click the box in GitHub's rendered view to toggle, or hand-edit the markdown (copy `[x]` from here to paste over any `[ ]`).

A *research investigation* is a forward-looking thread that may
span multiple experiments, papers, packages, and notes.  It is
**not** a single deliverable -- the eventual output may be one
paper, several papers, a section of an existing paper, an audit
row, a new module, a memory entry, or some combination, and
which one isn't known yet.

Examples already in this project's memory:

- *Proton internals* -- consumes Paper~II's SU(3) machinery + the
  generator zoo; eventual paper TBD.
- *Discrete-probability paper* -- empirical companion to
  `dcl_core.core3d`; centerpiece showcase is closing Paper~II's
  open gauge-coupling prefactor.
- *Hilbert-6th axiomatization* (Paper~I follow-on \#18) --
  capstone tying the framework's methodological claim together.

For a paper section / appendix / audit-row enhancement, use
`paper-enhancement`.  For a single experiment, use
`experiment-feature`.  For a runnable artefact, use
`research-artifact`.

**Investigation title**

Short phrase naming the thread.

**Research question / hypothesis**

The substantive question.  Be specific enough that "yes / no /
partial / falsified" is a meaningful eventual answer.

**What's known so far** (upstream from existing papers / notes /
memory)

- Papers / sections that already establish the prerequisite:
  _______________________
- Audit rows that are already `PASS` and that this depends on:
  _______________________
- Existing notes / memory entries that frame the thread:
  _______________________
- Follow-on catalogue entry (if any) in Paper~I's
  `notes/follow_on_implications.md`: #_______________________

**What's unknown** (the productive gaps)

The specific structural / numerical / observational questions
this investigation would close.  List as openly as possible;
the gap is more interesting than the early guess at how to close it.

**Connection to existing artefacts** (where this thread plugs in)

- Memory entry to extend / create: _______________________
- Audit rows touched (which paper, which rows): _______________________
- Modules touched (`dcl_core`, `dcl_formalism`, etc.):
  _______________________
- Cross-repo dependencies: _______________________

**Expected eventual output** (one or more -- the shape may evolve)

*A new paper in the series* (check if this investigation may produce
its own paper, then which slot):

- [ ] Proton internals (memory: `project-proton-internals-downstream`)
- [ ] Discrete-probability paper (memory:
      `project-discrete-probability-paper`)
- [ ] `dcl-formalism` package paper (memory:
      `project-a1-formalism-package`)
- [ ] Hilbert-6th axiomatization (Paper~I follow-on \#18)
- [ ] another Paper~I follow-on (cite #__): _______________________
- [ ] new paper not in the catalogue yet:
      _______________________

*Or a contribution to existing artefacts:*

- [ ] new section in an existing paper: _______________________
- [ ] new audit row(s) in an existing paper: _______________________
- [ ] new `notes/<topic>.md` file(s): _______________________
- [ ] new memory entry: _______________________
- [ ] new module in `dcl_core` / `dcl_formalism`: _______________________
- [ ] new experiment(s) `exp_NN`: _______________________
- [ ] new figure / animation / research-artifact: _______________________
- [ ] structural finding that doesn't fit any of the above:
      _______________________

**Investigation program** (phased plan; expand as the thread
matures)

- [ ] Phase 1: _______________________
- [ ] Phase 2: _______________________
- [ ] Phase 3: _______________________
- [ ] Phase 4: _______________________

**Notes that may be created or updated**

`notes/<topic>.md` files this investigation would touch -- even
stub notes that just capture the question are useful for
upstream flow to `external/research/Notes/`.

**Tools / resources needed** (anything not currently in hand)

- [ ] better CPU (specify): _______________________
- [ ] better GPU (specify): _______________________
- [ ] more memory / disk
- [ ] longer wall-clock budget (estimate): _______________________
- [ ] dataset access (specify): _______________________
- [ ] subscription / paid software (specify): _______________________
- [ ] collaborator with specific expertise (specify):
      _______________________
- [ ] sympy / `dcl_formalism` primitive that doesn't exist yet:
      _______________________
- [ ] other: _______________________

**Dependencies / blockers**

What has to land before this investigation can productively start
or finish?  (e.g. "Paper~III v0.1 deposited", "`dcl_core.core3d`
runnable", "the formalism package's `PathAlgebra` exists".)

**Status**

- [ ] proposed (idea-stage; question is interesting but
      unscoped)
- [ ] scoped (the productive question and rough program are
      written down here)
- [ ] in progress (active work happening in some repo /
      memory file)
- [ ] paused (waiting on a dependency from another thread)
- [ ] mature (about to graduate into a paper / module / audit
      row)

**Additional context**

Anything worth recording.  In particular: speculative
connections to other threads, framing alternatives you're
deliberately holding open, and risks (e.g. "may fail in a way
that's still publishable").
