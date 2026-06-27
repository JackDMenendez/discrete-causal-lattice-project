---
handoff: 2026-06-27-bell-separability-conclusions-paper06
from: PM (dcl-website session)
to: dcl-paper-06-Bell-test (focused)
repo: dcl-paper-06-Bell-test
branch: main
commits: []                         # advisory; the artifact is dcl-mathematics 3ed082a (referenced)
pr: none
status: consumed
state: in-progress
semver: n/a (physics conclusions + a referenced math note; no paper-06 code shipped)
flags:
  - "The current prepare_pair() (enforce_joint_unity / direct-sum) is FORMALLY separable → it will read S<=2 regardless of prob_floor. A null there is a PREPARATION artifact, not a physics verdict. (Formal backing for the still-open 2026-06-27-entangled-pair-preparation-physics-gap handoff.)"
  - "Randomness is NOT the loophole. Bell admits stochastic local models, and Fine's theorem folds any local RNG into lambda → a random-walk-on-shared-resonance is LHV, S<=2. Do not frame the random walk as the source of the violation."
  - "The scalar S alone is misleading. The PRIMARY diagnostic is the shape of E(theta) (correlation vs relative analyzer angle): LINEAR ⇒ separable, S<=2; cos(2theta) ⇒ non-separable, S→2√2. Report the curve, not just the number."
  - "Adjacency-without-metric REINTRODUCES the locality loophole: graph-adjacent A,B are causally connected, so a critic attributes any correlation to the edge. The floor_ledger no-signalling audit is therefore load-bearing — A's marginal MUST be independent of B's setting through the edge."
  - "The discreteness thesis (prob_floor CREATES the violation, vanishes in continuum) runs against the usual grain: the CONTINUUM entangled state already gives 2√2 and coarse-graining degrades correlations. High burden; the prob_floor=0 vs >0 comparison + the positive control decide whether the floor is load-bearing or incidental."
decisions:
  - "The single decidable question is REPRESENTATIONAL: does the lattice store a joint amplitude over PAIRS of nodes (entangled) or two fields over SINGLE nodes (mean-field/Hartree → separable → S<=2)? The two-body Bohr solver is the probe."
  - "Math backbone committed: dcl-mathematics/notes/bell_chsh_separability_on_lattice.md (3ed082a). Paper VI cites it via the audit-table evidence column."
consumed_by: dcl-paper-06-Bell-test (focused)
consumed_at: 2026-06-27
---

## Summary
A long foundations discussion converged on exactly what it takes for the A=1
lattice to violate Bell/CHSH, and the conclusions directly shape the paper-06
experiment. They are written up formally in
`dcl-mathematics/notes/bell_chsh_separability_on_lattice.md` (commit `3ed082a`,
the nonlocality backbone for Paper VI). This handoff relays the actionable
results to the focused session building the CHSH harness.

## Shipped
- (paper-06: none) — advisory handoff.
- Referenced artifact: `dcl-mathematics` `3ed082a` —
  `notes/bell_chsh_separability_on_lattice.md` (the formal treatment; §1–9 +
  conclusions + open questions).

## The conclusions (what they mean for the experiment)
1. **Separable ⇒ S≤2, unconditionally.** Per-session A=1, any shared classical
   variable (locked phase / shared coherence / shared "trembling" / *linear*
   harmonic-resonance lock), and a local random walk are all LHV. No dynamics,
   randomness, or constant nonlinearity lifts a separable model above 2.
2. **The violation is one thing only:** a non-separable joint amplitude
   (coherent |RL⟩+|LR⟩, *not* a classical mixture) sampled by a JOINT,
   non-factorizable collapse (`mode="joint"`, B drawn from the A-updated state).
   Both conditions necessary.
3. **Configuration space, not physical space.** Entanglement lives in
   Ψ(x_A,x_B); two fields ψ_A(x),ψ_B(x) on the same lattice are a mean-field
   product → separable. This is the representational crux (see decisions).
4. **Adjacency-without-metric is the candidate home** for the joint object
   (ER=EPR-flavored; explains the empirically distance-independent Bell
   violation, e.g. Micius 1200 km). It supplies the *channel*, not the *state* —
   and it brings the locality loophole, hence the no-signalling audit.
5. **E(θ) is the verdict; prob_floor=0 vs >0 is the thesis test.**

## Verification
N/A (conclusions + referenced note). The operational checks are the paper's own:
the `measure_pair` positive control (textbook maximally-entangled state, optimal
angles → S→2√2 in joint mode at prob_floor=0) and the E(θ) curve.

## Remaining
Pairs with — does not supersede — the open `2026-06-27-entangled-pair-preparation-physics-gap`
handoff (the birth-event physics is still the author's call). This handoff adds
the formal backing and the experiment-design consequences.

## Decisions & flags
See frontmatter. Load-bearing: the direct-sum prep will read S≤2 (artifact);
randomness is not a loophole; report E(θ) not just S; the no-signalling audit is
the locality-loophole guard under adjacency; the discreteness thesis carries a
high burden decided by prob_floor=0 vs >0.

## → Consumer actions (paper-06 focused session)
- [ ] Read `dcl-mathematics/notes/bell_chsh_separability_on_lattice.md`
      (`3ed082a`) and cite it as the nonlocality backbone via the audit-table
      evidence column when the paper's nonlocality section is written.
- [ ] Make **E(θ)** (correlation vs relative angle) the PRIMARY reported
      diagnostic, alongside scalar S: linear ⇒ separable (≤2), cos 2θ ⇒
      entangled (→2√2).
- [ ] Run the **positive control** (textbook maximally-entangled state, optimal
      angles → S→2√2, `mode="joint"`, `prob_floor=0`) and gate all
      interpretation on the harness passing it first.
- [ ] Treat the current **direct-sum `prepare_pair()` as confirmed-insufficient**
      (it will read ≤2); the gate hinges on a genuinely non-separable
      preparation — track via the entangled-pair-preparation handoff.
- [ ] Resolve the **representational question** in code: joint amplitude over
      pairs of nodes vs two fields over nodes (mean-field). Probe with the
      two-body Bohr solver (is its bound state a config-space joint object or a
      Hartree product?).
- [ ] Keep the **floor_ledger no-signalling audit** as the locality-loophole
      guard (A's marginal ⟂ B's setting through the adjacency edge).
- [ ] Interpret **prob_floor=0 vs >0**: violation only with the floor ⇒
      discreteness is the entangling nonlinearity (paper thesis); violation at
      floor=0 ⇒ entanglement was already in the prep and the floor is incidental
      (headline flips). State whichever the data shows.
- [ ] Do NOT bank on the random walk as the violation's source (Fine's theorem);
      keep nothing public until a result is derived (falsifiability-framing rule).
