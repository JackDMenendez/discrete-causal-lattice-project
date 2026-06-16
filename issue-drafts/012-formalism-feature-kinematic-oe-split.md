## Formalism feature

**Affected repository** (check one or more)

- [x] other (proposed): `dcl-paper-04-optical-axis-birefringence` — Paper IV (paper-only repo)

**Repository status** (check one)

- [x] existing

**Concept to formalise**

The closed-form **ordinary/extraordinary speed split** along the optical
axis $(1,1,-1)$ on the A=1 discrete causal lattice. This is the single
gap explicitly named in the Paper IV audit table (kinematic row, status
`PART`) and in `CLAUDE.md`: the structure-factor *magnitude* is already
characterised, but the two distinct mode speeds $v_o, v_e$ from the
propagator *eigenphases* are not yet derived in closed form.

**Definitions needed**

- Spinor-propagator structure factor
  $H_\text{RGB}(\mathbf{k}) = \tfrac13\sum_\text{RGB} e^{i\mathbf{k}\cdot\mathbf{V}}$,
  with $|H_\text{RGB}(\mathbf{k})|^2 = 1 - \mathbf{k}^T M_\text{eff}\mathbf{k}$
  and $M_\text{eff}$ eigenvalues $\{4/3, 4/3, 0\}$ (flat along
  $(1,1,-1)$, curved coeff. $4/3$ perpendicular).
- Ordinary/extraordinary mode speeds $v_o(\theta,\omega)$,
  $v_e(\theta,\omega)$ as functions of propagation direction $\theta$
  (angle to the optical axis) and frequency $\omega$.

**Assumptions**

- A=1 per-tick enforcement (exact integer identity on `core3d`).
- Small-$\mathbf{k}$ / long-wavelength regime where the dispersion is
  the leading geometric anisotropy; $O_h$-averaged isotropic $c$ in the
  $a\to 0$ limit as the consistency check.

**Target result**

A closed-form expression for the two mode speeds (or the split
$\Delta v = v_e - v_o$) as a function of direction and $\omega$, derived
from the **propagator eigenphases** — not merely from $|H|$. The
formula must (i) reduce to isotropic $c$ under $O_h$ averaging, (ii) be
$\omega$-independent to leading order (matching `exp_01`), and (iii)
reproduce the $v_\parallel/v_\perp \to 0.01$ flattening seen
numerically.

**Relation to existing formalism**

Direct continuation of the kinematic-channel mechanism in
`paper/sections/audit_table.tex`. Parent follow-on catalogue entry 14
(*Balanced Equations and Birefringent Channels*). Builds on Paper I
(Dirac/Lorentz structure). The gauge-sector channel (Q eigenvalues
$\{4,4,16\}$) shares the same geometric origin and reuses this framing.

**Verification path**

- [x] numerical cross-check against `dcl-core` execution — companion
  experiment `exp_02` (separate issue) confirms the closed-form
  $v_o(\theta), v_e(\theta)$ matches the propagator eigenphases.
- [x] paper-text proof

**Dependencies / related issues**

- Parent subproject: **#13** (Paper IV).
- Validated by the `exp_02` cross-check experiment (companion issue).
- **Critical path:** gauge-sector derivation and concordance (P9) both
  depend on the framing this establishes.

**Success criteria**

Closed-form $v_o, v_e$ derived from the eigenphases, matching the
`exp_01` numerical targets and the new `exp_02` eigenphase check within
stated precision — at which point the kinematic audit row flips
`PART → PASS`.

**Additional context**

`exp_01_optical_axis_isotropy` (run 2026-06-12, both engines) already
supplies the numerical target: optical axis confirmed at align
$=1.0000$, $\omega$-independent, anisotropy survives A=1 renormalization.
