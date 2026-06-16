## Formalism feature

**Affected repository** (check one or more)

- [x] other (proposed): `dcl-paper-04-optical-axis-birefringence` — Paper IV

**Repository status** (check one)

- [x] existing

**Concept to formalise**

The **multi-channel concordance (P9)**: that the kinematic and
gauge-sector birefringence channels predict a *shared* optical axis
$(1,1,-1)$, arising from a common geometric origin. Currently audit
status `STUB` ("pending both channels above").

**Definitions needed**

- The two channels' optical axes (from the kinematic $M_\text{eff}$ and
  the gauge-sector $\mathbf{Q}$ eigenstructures).
- A precise statement of cross-channel concordance: shared axis,
  direction-dependence relationship, and what would falsify it.

**Assumptions**

- Both channels derived to closed form (the two upstream formalism
  issues) and numerically confirmed (the two companion experiments).

**Target result**

A statement and proof that both channels share the $(1,1,-1)$ optical
axis — the multi-channel concordance P9 — making it one of the series'
standing falsifiable predictions in the claim map.

**Relation to existing formalism**

Capstone of the kinematic and gauge-sector channels; the concordance is
the cross-channel consistency claim (audit "Continuum/formal limit"
column: N/A). Connects to the claim map's standing-predictions table.

**Verification path**

- [x] structural argument only (cross-channel consistency)
- [x] numerical cross-check against `dcl-core` execution — both
  channels' experiments report the same optical axis

**Dependencies / related issues**

- Parent subproject: **#13** (Paper IV).
- **Blocked by** all four upstream issues: kinematic derivation +
  `exp_02`, gauge-sector derivation + `exp_03`.
- Unblocks only after both channels land.

**Success criteria**

Concordance stated and supported (both channels' optical axes coincide),
flipping the P9 audit row `STUB → PART/PASS` and feeding the claim map.

**Additional context**

Final link in the kinematic → gauge → concordance dependency chain. Per
the falsifiability framing rule, the standing-prediction commitment is
recorded in the claim map, not asserted in the paper prose.
