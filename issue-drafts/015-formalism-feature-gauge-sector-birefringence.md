## Formalism feature

**Affected repository** (check one or more)

- [x] other (proposed): `dcl-paper-04-optical-axis-birefringence` — Paper IV

**Repository status** (check one)

- [x] existing

**Concept to formalise**

The **gauge-sector birefringence** anisotropy, derived from the
$\mathbf{Q}$ eigenvalues $\{4,4,16\}$ — the same geometric origin as the
kinematic channel. Currently audit status `STUB` ("analytical; not yet
derived to closed form").

**Definitions needed**

- The induced gauge-response operator $\mathbf{Q}$ and its eigenvalues
  $\{4,4,16\}$.
- The gauge-sector anisotropy (analogue of the kinematic $v_o/v_e$
  split) as a function of direction, and its optical axis.

**Assumptions**

- A=1 per-tick enforcement; same long-wavelength regime as the
  kinematic derivation; $O_h$-symmetric continuum limit as the
  isotropy check.

**Target result**

A closed-form gauge-sector anisotropy from the $\mathbf{Q}$ eigenvalues,
exhibiting an optical axis aligned with $(1,1,-1)$ — establishing the
second of the two channels and setting up the concordance claim (P9).

**Relation to existing formalism**

Companion to the kinematic closed-form split (its sibling formalism
issue); shares the same geometric origin. Gauge sector traces to Paper
II. Catalogue parent: follow-on entry 14 (*Balanced Equations*).

**Verification path**

- [x] numerical cross-check against `dcl-core` execution — companion
  experiment (separate issue)
- [x] paper-text proof

**Dependencies / related issues**

- Parent subproject: **#13** (Paper IV).
- **Blocked by** the kinematic closed-form split (reuses its framing).
- Paired with the gauge-sector companion experiment.
- Feeds the multi-channel concordance (P9) issue.

**Success criteria**

Closed-form gauge-sector anisotropy derived and numerically confirmed,
flipping the gauge audit row `STUB → PART/PASS`.

**Additional context**

Second link in the kinematic → gauge → concordance dependency chain.
