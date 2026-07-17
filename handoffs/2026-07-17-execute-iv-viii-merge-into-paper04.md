---
handoff: 2026-07-17-execute-iv-viii-merge-into-paper04
from: PM (dcl-website session)
to: dcl-paper-04 (focused)   # per user direction 2026-07-17: the paper-04 session merges VIII into its own repo
repo: [JackDMenendez/dcl-paper-04-optical-axis-birefringence, JackDMenendez/dcl-paper-08-electric-induced-action]
branch: main
commits: []                         # task assignment + full review payload; no code handed off
pr: none
status: consumed
state: in-progress                  # work to be done by the executing session
semver: n/a (paper merge + revision, no software release)
flags:
  - "SELF-MERGE: the `dcl-paper-04` session performs the merge INTO ITS OWN REPO — VIII is folded into paper-04, which stays the home. Keep the repo SLUG `dcl-paper-04-optical-axis-birefringence`; change only the PAPER (document) title. (There is no `dcl-paper-05` repo/dir anywhere — an earlier routing to a 'Paper 05' session was corrected to paper-04 per user, 2026-07-17.)"
  - "MERGE DECISION (user, 2026-07-17): merge Papers IV and VIII into ONE paper, homed in the EXISTING `dcl-paper-04` repo (reuse, do not create a new repo — nothing is published/DOI'd, and the live site already links paper-04). Title may change; the repo SLUG stays `dcl-paper-04-optical-axis-birefringence` (the optical axis remains the conceptual spine; the slug is just a handle). If the slug is ever renamed, update the two dcl-website references (assets/roadmap.json URL + news/posts/2026-07-08-dcl-core-v0-3-0.qmd)."
  - "PRESERVE HISTORY: bring Paper VIII's content into paper-04 via `git subtree add` (or read-tree), NOT a plain file copy, so the provenance of VIII's sympy-verified derivation survives (project discipline: derivation papers carry their sympy verification). Then ARCHIVE `dcl-paper-08` read-only with a tombstone README pointing to paper-04 — do NOT delete (its history lives on in paper-04 via subtree; the site never linked it, so nothing breaks)."
  - "REVIEWER VERDICTS the merge must resolve: VIII = MAJOR REVISION (the 'induced action / exact permittivity' claim exceeds the derivation); IV = WORKING DRAFT (mislabels directional dispersion anisotropy as 'birefringence'; treats a NON-UNITARY transfer-matrix eigenphase as a group velocity without proof). The core algebraic result — `Q_B = adj(P)`, `P = M Mᵀ`, doubled transverse Maxwell root — is AFFIRMED and should be FEATURED as headline theorems (see 'Affirmed results — FEATURE these'), not merely preserved; the corrections reframe the *claims* around them, not the theorems."
  - "TERMINOLOGY (correctness): reserve 'birefringence' for the GAUGE-sector result (two transverse Maxwell roots). The IV kinematic Section 2 is uniaxial DIRECTIONAL DISPERSION ANISOTROPY (compares k-directions), not a fixed-k polarization split."
  - "INDUCED-ACTION OVERCLAIM (VIII): `δφ = ω + V` from one HopOperator.step validates the VERTEX, not the quadratic effective action Γ⁽²⁾; D_3d symmetry permits two free coefficients and does NOT force the ε ratio 1:4. Downgrade to 'geometric candidate' unless the ∂²Γ/∂E∂E derivation is supplied."
  - "EXACT ADJUGATE FAILS O_h AVERAGING: adj(3I)=9I ≠ 8I → use the PROPORTIONAL closure μ⁻¹ = γ·adj(ε). General Fresnel prefactor is det(ε), NOT 16 (VIII p.8)."
decisions:
  - "Merge into Paper IV, reuse dcl-paper-04, subtree-in VIII, archive dcl-paper-08, keep the slug and retitle the document (user + PM, 2026-07-17). Reviewer's editorial 'Option 1/merge' resolved as MERGE."
  - "PM is routing the FULL external review verbatim (embedded below + asset `handoffs/assets/2026-07-17-review-paper-04-and-08-source.md`). Physics adjudication is the executing session's + user's, not PM's."
consumed_by: dcl-paper-04 (focused)
consumed_at: 2026-07-17
---

## Summary
Per the user (2026-07-17), Papers IV and VIII are being **merged into a single
paper homed in the existing `dcl-paper-04` repo**, with the `dcl-paper-04`
session performing the merge into its own repo. This handoff carries (1) the **full external
review** of both papers verbatim, and (2) the **merge mandate + safe mechanics**
so the merge preserves history and resolves the review. The core algebraic
result is sound and stays; the merge's job is to fix the framing/terminology
objections and fold VIII's electric block into the unified Paper IV.

## The merge mandate (do this)
1. **Home = existing `dcl-paper-04-optical-axis-birefringence`.** Reuse it; do
   NOT create a new repo (nothing is released/DOI'd; the live site already links
   paper-04). The paper-04 session merges VIII into its own repo; keep the slug,
   change only the document title.
2. **Fold VIII in with history:** `git subtree add --prefix=<path> \
   https://github.com/JackDMenendez/dcl-paper-08-electric-induced-action main`
   (or read-tree), so VIII's sympy-verified derivation keeps its provenance.
   Reconcile shared/duplicated gauge-sector material (IV currently repeats VIII).
3. **Archive `dcl-paper-08`** read-only afterward with a tombstone README →
   points to paper-04. Do not delete.
4. **Title:** may change to reflect the unified scope (reviewer's steer: the
   optical axis is the conceptual unity). Keep the repo **slug** as-is; if you do
   rename it, update the two dcl-website refs (roadmap.json URL + the v0.3.0 news
   post). Fix VIII's `CLAUDE.md` scope-gate text ("held upstream" → merged).
5. **Series bookkeeping:** VIII's number is retired/absorbed into IV. Board:
   close #23 (repo `discrete-causal-lattice-project`, project 6) as "merged into
   Paper IV (#13)"; #13 becomes the merged paper's tracking issue.

## Affirmed results — FEATURE these prominently (the critic's highlighted contributions)
The reviewer did not only correct; they flagged genuine results the merged paper
should **foreground as headline contributions**, not bury. Give each a clear
theorem/proposition environment and state its generality:
1. **The adjugate theorem `Q_B = adj(P)`** with `P = M Mᵀ` (Gram matrix of the
   three hop vectors) and `Q_B` the Gram matrix of their pairwise cross products.
   The reviewer calls this "the best contribution" — compact, **general**, and
   NOT peculiar to the numerical lattice values. State it as a named theorem with
   its general (hop-vector) form, with the `{1,4,4}`/`{16,4,4}` lattice case as a
   corollary.
2. **The doubled transverse Maxwell root / non-birefringent closure** — "a
   genuine theorem, not merely a numerical observation": both transverse
   polarizations share dispersion even though the common speed is direction-
   dependent. Present as a theorem with the Fresnel-determinant factorization
   `det(...) = det(ε) ω² (ω² − kᵀεk)²`.
3. **The omitted-fourth-cube-diagonal geometry** — the reviewer calls the
   geometric explanation of the special (optical) direction "clear and
   memorable." Keep it as the intuitive anchor for the optical axis.
4. **The temporal-plaquette construction** `Θ_a = A_0(x) − A_0(x+V_a) = V_a·E`,
   hence `P = Σ_a V_a V_aᵀ` — "geometrically well motivated." Feature it as the
   structural origin of the electric block (with the induced-action *claim* about
   it downgraded per the corrections below).

## Corrections the merged paper must resolve

### From Paper VIII (was major-revision)
- **Downgrade the induced-action claim** → "geometric candidate for the electric
  response block" / "plaquette-induced electric quadratic form", UNLESS you
  supply `ε_ij ∝ ∂²Γ[A]/∂E_i∂E_j |_{A=0}`, `Γ[A] = −log det T[A]` (or a measured
  2nd-order response). State that a general D_3d-invariant quadratic form has two
  free coefficients; the 1:4 ratio is not symmetry-forced.
- **p.8 prefactor** is `det(ε)`, not `16`.
- **Proportional closure** `μ⁻¹ = γ·adj(ε)`; fix the O_h-average text — the
  EXACT adjugate identity does NOT survive averaging (`adj(3I)=9I≠8I`); the
  averaged medium is non-birefringent only because it is isotropic.
- **Retitle "covariant completion"** → "the constitutive closure" /
  "non-birefringent electric–magnetic completion" unless you build the full 4D
  `χ^{μνρσ}` and state the effective metric + time normalization.
- **Coupling normalization:** a common `1/g²` cancels from the source-free EOM
  and does NOT set the photon speed; the RELATIVE electric/magnetic normalization
  (incl. temporal-vs-spatial lattice scales) does.
- **Status language:** reconcile the PASS-vs-"held partial" contradiction to the
  three-way split — null polarization split (conditional on the blocks) = PASS;
  blocks as the actual dynamical effective action = PART; common-mode isotropy =
  PART.
- **"Tree-level induced action"** wording: a matter-integrated action is
  loop-level; a prescribed plaquette action is a bare geometric action.

### From Paper IV (was working draft)
- **Terminology:** Section 2 is uniaxial directional dispersion anisotropy, not
  birefringence. Rename accordingly (reviewer suggestion for the standalone IV
  was "Optical-Axis Dispersion Anisotropy on the A=1 Discrete Causal Lattice" —
  adapt for the merged scope) and Proposition 2.1 → "Axial–transverse
  group-velocity contrast". Reserve "birefringence" for the gauge-sector roots.
- **Prove the transfer-matrix interpretation:** `T(k)` is non-unitary off-axis
  (`|λ_±|² = sin²(ω/2)+cos²(ω/2)|H~|² < 1`); justify `grad_k arg λ_+` as a
  physical group velocity (derive wave-packet motion incl. the momentum
  dependence of `|λ|`) or show how the A=1 normalization yields a unitary
  propagator. Handle ω=0 (eigenphase group velocity zero everywhere; `|H~|`
  curvature is filtering, not proven photon dispersion).
- **Photon identity:** add a standalone argument for how the two-component
  spinor mode acquires the representation, helicity, and gauge character of a
  photon.
- **Eq (15) notation:** pick ONE — `K=[k]_×` with `ω²=kᵀεk`, OR `K=[k̂]_×` with
  the squared phase speed `v²=k̂ᵀεk̂`.
- **Soften "independent confirmation"** → "independent code-path verification".
- **Presentation:** fill placeholder abstract/intro/scope/examples/conclusion/
  appendices; remove the fictitious sample reference.

### Presentation (VIII side)
- Fix PDF metadata placeholders ("Author Name", "Your Paper Title", placeholder
  keywords); remove the acknowledgement TODO; fix overfull monospace paths;
  de-compress the audit table (landscape appendix); add external literature
  (anisotropic Maxwell media, lattice gauge actions, temporal plaquettes,
  constitutive closure, observational Lorentz-anisotropy constraints).

## → Consumer actions (executing session)
- [ ] Merge per the mandate above (reuse paper-04, subtree-in VIII, archive
      paper-08, retitle document, keep slug).
- [ ] **Feature the four affirmed results** (section "Affirmed results — FEATURE
      these") as named theorems/propositions with their general forms — the
      adjugate theorem `Q_B = adj(P)`, the doubled-root non-birefringent closure,
      the fourth-cube-diagonal geometry, and the temporal-plaquette origin of P.
- [ ] Resolve every correction in the two lists above WITHOUT weakening those
      affirmed results (the corrections retitle/reframe the *claims* around them,
      not the theorems themselves).
- [ ] Board: close #23 as merged-into-#13; update #13 title/scope for the merged
      paper.
- [ ] When done, write a handoff back to PM (merge complete, board state, any
      correction you could not resolve).
- [ ] Cross-refs: `2026-07-17-paper04-paper08-external-review` (the same review
      routed to the two paper sessions), `2026-07-16-paper08-paper04-companion-
      publication` (now superseded by MERGE), `2026-07-16-paper08-verdict-
      delivered-paper04-unblocked`.

---

## FULL EXTERNAL REVIEW (verbatim; source: dcl-website `notes/Review_paper_04_and_08.md`)
> Math is as-authored; every equation is restated in prose-forward form in the
> corrections above. Also preserved at
> `handoffs/assets/2026-07-17-review-paper-04-and-08-source.md`.

### Overall assessment
The papers contain a **strong and elegant algebraic result**, especially the adjugate relationship between the electric and magnetic quadratic forms. I independently recomputed the matrices, their spectra, and the Fresnel determinant: ε = [[3,−1,1],[−1,3,1],[1,1,3]], adj(ε) = [[8,4,−4],[4,8,−4],[−4,−4,8]], with eigenvalues {1,4,4} and {16,4,4}, respectively, and det( K adj(ε) K + ω² ε ) = det(ε) ω² ( ω² − kᵀ ε k )². That part is correct and worthwhile. It gives a clean non-birefringent constitutive closure: two transverse polarizations have the same dispersion even though their common speed is direction-dependent.

My publication verdict would be:
* **Paper VIII:** promising and mathematically interesting, but requires **major revision**, primarily because the physical interpretation as an *induced action* is stronger than the current derivation supports.
* **Paper IV:** presently a **working technical draft**, not yet a submission-ready paper. Its central kinematic calculation appears algebraically sound, but it is described as "birefringence" when it is actually directional dispersion anisotropy, and the physical meaning of the transfer-matrix eigenphase needs much more justification.

### Paper VIII: what is strongest
The best contribution is the theorem Q_B = adj(P), derived from the hop-vector matrix M, with P = M Mᵀ. This is compact, general, and not peculiar to the numerical lattice values. The associated doubled-root dispersion is also a genuine theorem, not merely a numerical observation. The geometrical explanation of the special direction as the omitted fourth cube diagonal is clear and memorable.

The temporal-link observation is also useful. Treating the on-site scalar-potential phase as a temporal gauge link is standard in spirit and provides a natural temporal plaquette: Θ_a = A_0(x) − A_0(x + V_a) = V_a · E. This makes the proposed electric tensor P = Σ_a V_a V_aᵀ plausible and geometrically well motivated.

The paper is also unusually candid about the remaining common-mode speed anisotropy. Distinguishing anisotropy shared by both polarizations from polarization birefringence is exactly right.

### Paper VIII: the principal scientific gap
The engine experiment verifies that the tick rule contains the phase A_0 = ω + V(x). It does **not yet establish that integrating out the matter dynamics produces** Γ⁽²⁾[E] ∝ Σ_a (V_a · E)² with no cross-plaquette terms and with the claimed weighting.

Recovering δφ from one application of `HopOperator.step` validates the **vertex or coupling**, not the **quadratic effective action**. To call P the induced permittivity, one needs something equivalent to ε_ij ∝ ∂²Γ[A]/∂E_i∂E_j at A=0, with Γ[A] = −log det T[A], or a directly measured second-order energy/current response. Gauge invariance and D_3d symmetry constrain the answer, but they do not by themselves force the eigenvalue ratio 1:4. A general D_3d-invariant quadratic form has two independent coefficients. Cross terms between temporal plaquettes can change that ratio.

Consequently, the present evidence supports language such as "geometric candidate for the electric response block" or "plaquette-induced electric quadratic form" more securely than "the exact induced-action permittivity."

This concern also applies, at least conceptually, to the magnetic block unless Paper I genuinely derives it from an effective-action Hessian rather than assuming an equal-weight Wilson plaquette action. The paper's statement that the geometric block is a "tree-level induced action" should be reconsidered: an action obtained by integrating out matter is normally a loop-level effective action, whereas a prescribed plaquette action is a bare geometric action.

### Important mathematical and logical corrections in Paper VIII
**1. The general determinant coefficient is not 16.** Page 8 says that for a "general symmetric ε" the determinant is 16 ω² (ω² − kᵀεk)². For general ε, the prefactor is det(ε), not 16. Sixteen is the determinant of the particular lattice matrix. Paper IV gives the correct general form.

**2. Use the proportional closure as the physically relevant theorem.** The no-birefringence result survives μ⁻¹ = γ adj(ε) for any positive scalar γ. This is the correct formulation if the electric and magnetic sectors carry different overall normalizations. That change also resolves a problem in the O_h average. The paper gives ⟨ε⟩ = 3I, ⟨μ⁻¹⟩ = 8I. But adj(3I) = 9I ≠ 8I. Thus the **exact equality** μ⁻¹ = adj(ε) does not survive averaging. The proportional condition does: 8I = (8/9) adj(3I). The averaged medium remains non-birefringent because it is isotropic, but the manuscript should not say that the exact adjugate relation survives averaging.

**3. "Covariant completion" overstates what has been shown.** The algebra demonstrates an impedance-matched, non-birefringent anisotropic constitutive medium. It does not by itself establish Lorentz covariance or boost symmetry in the original lattice coordinates. A safer section title would be "The constitutive closure" or "The non-birefringent electric–magnetic completion". To retain "covariant," construct the complete four-dimensional constitutive tensor χ^{μνρσ}, show that it is metric-induced or satisfies the electromagnetic closure relation, and state precisely which effective metric and time normalization result.

**4. The coupling-normalization discussion needs correction.** A single common factor 1/g² multiplying both the electric and magnetic parts of the action cancels from the source-free equations of motion and therefore does **not** set the photon speed. The speed is determined by the **relative** electric/magnetic normalization, including temporal-versus-spatial lattice scales.

**5. The status language contradicts itself.** The audit table labels gauge-sector birefringence as PASS, and the body repeatedly says it is settled. Page 10 then says the "unconditional birefringence verdict is held partial." The vacuum-domain issue cannot revive polarization splitting according to the preceding theorem, so these statements must be reconciled. My recommendation is: null polarization split conditional on the proposed blocks: PASS; derivation of the blocks as the actual dynamical effective action: PART; common-mode isotropy: PART. That status assignment would accurately identify where the uncertainty really lies.

### Paper IV: the central terminology problem
Section 2 does not derive birefringence in the usual physical sense. Birefringence means two polarization eigenmodes with different phase or group velocities **for the same propagation vector**. The paper instead compares propagation in different directions: k ⊥ n_* (maximal group speed); k ∥ n_* (zero group speed). That is **uniaxial directional dispersion anisotropy**, not an ordinary/extraordinary polarization split. The two λ_± branches are the two eigenvalue branches of the spinor transfer matrix — apparently positive/negative-frequency or paired spinor branches — not two optical polarizations at fixed k.

I would rename the paper along the lines of "Optical-Axis Dispersion Anisotropy on the A=1 Discrete Causal Lattice" and rename Proposition 2.1 "Axial–transverse group-velocity contrast". The gauge-sector result may properly discuss birefringence because it explicitly compares the two transverse Maxwell polarization roots.

### Paper IV: the transfer-matrix interpretation needs proof
The eigenvalues are λ_± = i sin(ω/2) ± cos(ω/2) |H~(k)|. Away from the optical axis, |λ_±|² = sin²(ω/2) + cos²(ω/2) |H~|² < 1. Thus T(k) is not unitary on those modes. Its eigenvalues contain both phase evolution and attenuation or amplitude renormalization. Taking θ(k) = arg λ_+(k) and identifying ∇_k θ as a physical group velocity is not automatically valid for a nonunitary transfer operator. The paper needs to derive wave-packet motion for this evolution, including the momentum dependence of |λ|, or explain precisely how the A=1 normalization converts it into a unitary physical propagator.

The photon-limit discussion makes the issue especially visible. At ω=0, λ_± = ± |H~|, so the phase is momentum-independent and the eigenphase group velocity is zero everywhere. The manuscript then calls the curvature of |H~| a "photon dispersion-curvature split." But curvature of an eigenvalue's **magnitude** is attenuation or filtering curvature unless a further physical argument turns it into energy dispersion. Until that mapping is supplied, the safe claim is: the transfer operator has an exact axial–transverse anisotropy in its structure-factor magnitude. It is not yet demonstrated that this is a photon energy dispersion.

Relatedly, a massless limit of a spinor propagator is ordinarily a massless spinor mode, not automatically a photon. The paper needs a concise standalone explanation of how the two-component mode acquires the physical representation, helicity content, and gauge character of a photon.

### A concrete notation error in Paper IV
Equation (15) defines K = [k̂]_× but then gives ω² = kᵀ ε k. These are two different formulations: with K = [k]_× (unscaled), the dispersion is ω² = kᵀ ε k; with K = [k̂]_× (unit), the generalized eigenvalue is the squared phase speed v² = k̂ᵀ ε k̂. Use one formulation consistently.

### How the two papers work together
At present, the gauge-sector material in Paper IV substantially repeats Paper VIII. The claim of "independent confirmation" should also be softened: it is a separate implementation and useful cross-check, but it uses the same framework, same engine, same geometric objects, and same author. "Independent code-path verification" would be more accurate.

I see two good editorial choices: (1) Make Paper VIII the complete gauge-response paper. Paper IV then becomes a shorter paper solely about the spinor/transfer-operator anisotropy, with the gauge result summarized in one section. (2) Merge the papers. The shared optical axis is the conceptual unity, and one stronger paper may be preferable to two overlapping drafts. The first option is probably cleaner if the series architecture matters. [PM/user decision 2026-07-17: MERGE.]

### Presentation and publication readiness
Paper VIII is structurally mature, but it still needs: external literature on anisotropic Maxwell media, lattice gauge actions, temporal plaquettes, constitutive closure, and observational Lorentz-anisotropy constraints; corrected PDF metadata, which currently contains "Author Name," "Your Paper Title," and placeholder keywords; removal of the acknowledgement TODO; correction of overfull monospace paths; a less compressed audit table, perhaps moved to a landscape appendix.

Paper IV visibly retains placeholder abstract, introduction, scope, worked examples, conclusion, acknowledgements, appendices, and a fictitious sample reference. It is therefore not yet ready for scientific circulation beyond trusted collaborators.

### Bottom line
There is a **real mathematical result here**: the Gram matrix of three hop vectors and the Gram matrix of their pairwise cross products are adjugates, and that closure produces a doubled transverse Maxwell root. That is elegant and defensible.

The major vulnerability is the step from "these are the natural temporal and spatial plaquette quadratic forms" to "these are the exact permittivity and inverse permeability induced by the dynamical lattice." That step remains to be demonstrated through the effective action or a genuinely dynamical response calculation. Until then, the null-birefringence theorem is rigorous **conditional on the proposed constitutive tensors**, but the derivation of those tensors as the physical vacuum response remains partial.
