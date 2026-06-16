## Paper enhancement

**Affected paper** (check one or more)

- [x] other: `dcl-paper-04-optical-axis-birefringence` — Paper IV
  (*Optical-Axis Birefringence on the A=1 Discrete Causal Lattice*)

**Description**

Draft the **abstract** and **introduction** for Paper IV. The body is
still all template stubs (`abstract.tex`, `introduction.tex`,
`conclusion.tex` not yet written). The framing must state the **two
channels** — kinematic and gauge-sector — and the predicted
**multi-channel concordance (P9)**: that both channels share the same
$(1,1,-1)$ optical axis from a common geometric origin.

**Objectives** (what success looks like, as a list)

- [ ] abstract states the two channels + P9 concordance, with audit
      status semantics (`PASS`/`PART`/`STUB`/`FAIL`)
- [ ] introduction motivates optical-axis birefringence as a standing
      falsifiable prediction of the series (claim map)
- [ ] introduction situates Paper IV relative to Papers I/II and seed
      catalogue entry 14 (*Balanced Equations and Birefringent Channels*)

**Requirements**

- [x] revise existing section: `paper/sections/abstract.tex`,
      `paper/sections/introduction.tex`
- [x] revise existing section: `paper/sections/conclusion.tex` (sketch)
- [ ] new audit-table row(s): none (rows already exist)

**Sections that may be updated**

- `paper/sections/abstract.tex`
- `paper/sections/introduction.tex`
- `paper/sections/conclusion.tex`

**Notes that may be created or updated**

- `notes/optical_axis_renormalization_test.md` (existing; reference for
  the kinematic-channel result)

**Audit-table impact** (if applicable)

- New audit row? `[ ]` yes / `[x]` no
- Existing row(s) affected: none (text only)

**Motivation**

The paper cannot cohere until the framing is set. Per the sequencing
note, the closed-form kinematic split establishes the framing that the
abstract/introduction then state; the gauge-sector and concordance
sections build on it. Falsifiability framing rule applies: present the
prediction as *sought*, asserting capability — the standing-prediction
commitment lives in the claim map, not the paper prose.

**References / related material**

- Follow-on catalogue entry 14 (*Balanced Equations and Birefringent Channels*).
- Papers I (Dirac/Lorentz structure) and II (gauge sector).
- `exp_01_optical_axis_isotropy` result.

**Dependencies / related issues**

- Parent subproject: **#13** (Paper IV).
- Best drafted **after** the closed-form kinematic split (companion
  formalism issue) sets the framing.

**Status**

- [x] scoped (this template filled in fully)

**Additional context**

Provisioned 2026-06-13 from `dcl-paper-template`; build-verified.
