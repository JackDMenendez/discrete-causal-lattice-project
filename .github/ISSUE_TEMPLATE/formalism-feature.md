---
name: Formalism feature
about: Propose a new formalism, definition, or proof; or a dcl-formalism module
labels: enhancement, formalism
---

## Formalism feature

**Affected repository** (check one or more)

- [ ] `dcl-formalism` -- sympy-extending package (planned)
- [ ] `physics-research/Notes/` -- formalisation notes (external)
- [ ] one of the paper repos -- formalism flows into a paper section
- [ ] other (proposed): _______________________

**Repository status** (check one)

- [ ] existing
- [ ] planned (scoped; repo to be created)
- [ ] proposed (idea-stage only)

**Concept to formalise**

The concept, structure, or idea needing formal treatment.

**Definitions needed**

Required definitions, notation, or primitives.  If extending
sympy, name the existing sympy class(es) you plan to subclass
(e.g. `sympy.Symbol`, `sympy.Function`, `sympy.physics.quantum.Operator`).

**sympy-extension hint** (if applicable)

- [ ] new `Symbol` / `Function` / `Operator` subclass
- [ ] new `Basic` subclass with custom `_eval_*` overrides
- [ ] new module under `dcl_formalism/<area>/`
- [ ] sympy module being extended:
- Proposed public-API name (`dcl_formalism.<X>`):

**Assumptions**

Assumptions or constraints under which the formalism holds.

**Target result**

The theorem, proposition, lemma, identity, or formal result
desired.  State it crisply if you can; otherwise describe what
the result *would* look like.

**Relation to existing formalism**

How this connects to existing definitions, proofs, or structures.
Cite Paper~I / Paper~II sections, the
`external/dcl/notes/follow_on_implications.md` catalogue entries
(\#13 Operation Algebra, \#14 Balanced Equations are the obvious
parents), and any `physics-research/Notes/` material.

**Verification path**

How will the formal result be checked?

- [ ] sympy symbolic verification (test in `dcl-formalism/tests/`)
- [ ] paper-text proof
- [ ] numerical cross-check against `dcl-core` execution
- [ ] structural argument only

**Dependencies / related issues**

List dependencies and related issues.

**Success criteria**

Describe what success looks like.

**Additional context**

Any other context.
