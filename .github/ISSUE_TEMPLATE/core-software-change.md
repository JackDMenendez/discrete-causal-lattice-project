---
name: Core software change (dcl-core)
about: Propose a change to the dcl-core Python package
labels: enhancement, core-software
---

## Core software change

This template is pre-routed to **`dcl-core`**
(<https://github.com/JackDMenendez/dcl-core>).  For other repos use
the relevant template (paper enhancement, experiment feature,
utility feature, formalism feature, etc.).

**Affected submodule** (check one)

- [ ] `dcl_core.core` (Paper~I's continuous-amplitude engine)
- [ ] `dcl_core.core3d` (integer-token engine; new design)
- [ ] both / cross-cutting
- [ ] new submodule

**Module / file affected**

e.g. `src/dcl_core/core3d/hop.py`, `tests/test_cross_validation.py`,
`pyproject.toml`.

**Current limitation**

Describe the current problem, limitation, or pain point.

**Proposed change**

Describe the change you want to make.

**Motivation**

Explain why this change matters.

**API / interface impact**

- [ ] No change to anything re-exported from
  `src/dcl_core/__init__.py` or a submodule `__init__.py`.
- [ ] **Public API addition** (minor version bump required).
- [ ] **Public API change or removal** (major version bump required).
- Affected re-exports:

**Performance / correctness impact**

Describe expected effects on performance, correctness, or
reliability.  Mention any tests in `tests/` that should be added
or updated.

**Test invariants touched**

- [ ] `test_smoke.py` -- API stability
- [ ] `test_conservation.py` -- A=1 integer equality
- [ ] `test_hop.py` -- hop-operator symmetries
- [ ] `test_remainder.py` -- Bresenham residual
- [ ] `test_continuum_limit.py` -- E^2 = m^2 + p^2 convergence
- [ ] `test_clifford.py` -- Clifford anticommutator
- [ ] `test_cross_validation.py` -- core <-> core3d convergence
- [ ] other:

**Dependencies / related issues**

List any dependencies, related issues, or upstream notes.

**Success criteria**

Describe what success looks like.  Cite test names, expected
output, or audit-table rows.

**Additional context**

Any other context.
