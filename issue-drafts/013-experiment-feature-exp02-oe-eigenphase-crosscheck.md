## Experiment feature

**Affected repository** (check one or more)

- [x] other (planned): `dcl-paper-04-optical-axis-birefringence` — Paper IV

**Repository status** (check one)

- [x] existing

**Experiment ID**

`exp_02_optical_axis_eigenphase_split` (new). `exp_01` is the only
existing experiment; this is the next free `NN`. May alternatively
extend `exp_01`, but a dedicated experiment keeps the eigenphase
measurement separable from the real-space spreading observable.

**Experiment goal**

Confirm that the closed-form ordinary/extraordinary speed split
$v_o(\theta,\omega), v_e(\theta,\omega)$ (companion formalism issue)
matches the **propagator eigenphases** extracted numerically. Where
`exp_01` measured the real-space spreading dual (variance flattening),
this measures the mode speeds directly via the eigenphases of the
discrete propagator.

**Motivation**

Serves the kinematic audit row in `paper/sections/audit_table.tex`
(currently `PART`). `exp_01` confirmed the optical axis and that the
anisotropy survives A=1 renormalization, but the audit row's documented
gap is the *closed-form speed split*. This experiment is the numerical
half of closing that gap.

**Inputs / parameters**

- Lattice $129^3$ (quick check $41^3$); $\omega \in \{0\ (\text{photon}),\
  0.1019\ (\text{free particle})\}$; range of propagation directions
  $\theta$ from the optical axis $(1,1,-1)$ through a perpendicular
  direction; both engines (`core3d` primary, `core` cross-check).

**Expected outputs**

- [x] `.npy` / `.npz` arrays under `data/`
- [x] stdout log under `data/exp_02*.log`
- [ ] figures under `paper/figures/` (eigenphase / speed-vs-angle plot)
- [x] new audit-table row in `paper/sections/audit_table.tex` — no;
  updates the existing kinematic row evidence cell.

**Metrics / evaluation**

PASS if measured eigenphase speeds match the closed-form
$v_o(\theta), v_e(\theta)$ within stated tolerance across $\theta$ and on
both engines, $\omega$-independent. PART if the trend matches but a
quantitative gap remains. FAIL if the eigenphases contradict the closed
form.

**Audit-table impact** (if applicable)

- New row? `[ ] yes / [x] no`
- Existing row affected: **Kinematic birefringence along $(1,1,-1)$**
- Expected status: `[x] PASS` (jointly with the formalism derivation)

**Resource estimate**

- Wall-clock per run: comparable to `exp_01` (~minutes at $41^3$, longer
  at $129^3$).
- Hardware: CPU; $129^3$ lattice.
- Determinism: seeded.

**Reproducibility notes**

Reuse the `exp_01` engine-config harness (`core3d` integer-token and
`core` float-amplitude) so the eigenphase result is shown not to be an
artefact of one A=1 scheme.

**Dependencies / related issues**

- Parent subproject: **#13** (Paper IV).
- **Blocked by** the closed-form derivation (companion formalism issue);
  this validates that formula.

**Success criteria**

Numerically extracted eigenphase speeds match the closed-form
$v_o(\theta), v_e(\theta)$ on both engines — completing, with the
derivation, the kinematic row's flip to `PASS`.

**Additional context**

The dispersion is *flat* along $(1,1,-1)$ (infinite effective mass), so
— as in `exp_01` — care is needed near the optical axis where transport
contrast vanishes.
