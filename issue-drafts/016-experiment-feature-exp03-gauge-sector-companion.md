## Experiment feature

**Affected repository** (check one or more)

- [x] other (planned): `dcl-paper-04-optical-axis-birefringence` — Paper IV

**Repository status** (check one)

- [x] existing

**Experiment ID**

`exp_03_gauge_sector_birefringence` (new). Next free `NN` after the
kinematic `exp_02`.

**Experiment goal**

Numerically confirm the closed-form gauge-sector anisotropy derived from
the $\mathbf{Q}$ eigenvalues $\{4,4,16\}$ (companion formalism issue),
and verify its optical axis aligns with $(1,1,-1)$ — the gauge-channel
analogue of `exp_01`/`exp_02` for the kinematic channel.

**Motivation**

Serves the gauge-sector audit row (currently `STUB`). A closed-form
result alone leaves the row at `STUB`/`PART`; the companion experiment
provides the numerical confirmation needed to flip it.

**Inputs / parameters**

- Both engines (`core3d` primary, `core` cross-check); $129^3$ lattice
  (quick check $41^3$); directions spanning the optical axis to
  perpendicular; $\omega$ as in `exp_01`.

**Expected outputs**

- [x] `.npy` / `.npz` arrays under `data/`
- [x] stdout log under `data/exp_03*.log`
- [ ] figures under `paper/figures/`
- [x] updates existing gauge-sector row in
  `paper/sections/audit_table.tex`

**Metrics / evaluation**

PASS if the measured gauge-sector anisotropy and optical axis match the
closed form on both engines; PART if mechanism is shown but a
quantitative gap remains; FAIL if disconfirmed.

**Audit-table impact** (if applicable)

- New row? `[ ] yes / [x] no`
- Existing row affected: **Gauge-sector birefringence ($\mathbf{Q}$
  eigenvalues $\{4,4,16\}$)**
- Expected status: `[x] PART` → `[x] PASS` jointly with the derivation

**Resource estimate**

- Wall-clock per run: comparable to `exp_01`.
- Hardware: CPU; $129^3$ lattice.
- Determinism: seeded.

**Reproducibility notes**

Reuse the dual-engine A=1 harness from `exp_01`/`exp_02`.

**Dependencies / related issues**

- Parent subproject: **#13** (Paper IV).
- **Blocked by** the gauge-sector closed-form derivation (companion
  formalism issue).
- Feeds the multi-channel concordance (P9) issue.

**Success criteria**

Numerical gauge-sector anisotropy + shared optical axis confirmed on
both engines, completing the gauge row's flip with the derivation.

**Additional context**

Third link in the kinematic → gauge → concordance chain.
