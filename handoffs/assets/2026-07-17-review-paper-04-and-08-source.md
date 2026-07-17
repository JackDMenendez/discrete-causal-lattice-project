<!--
VERBATIM SOURCE of the external-style review of Papers IV and VIII.
Authored in dcl-website: notes/Review_paper_04_and_08.md.
Preserved here (dcl-project) so the dcl-paper-04 and dcl-paper-08 sessions can
read the exact wording. The structured, per-paper actionable split is in the
routing handoff 2026-07-17-paper04-paper08-external-review.md.
Display-math below is as-authored (some LaTeX delimiters rendered as [...] / ====
in the source); the handoff restates every equation in clean prose-forward form.
-->

## Overall assessment

The papers contain a **strong and elegant algebraic result**, especially the adjugate relationship between the electric and magnetic quadratic forms. I independently recomputed the matrices, their spectra, and the Fresnel determinant:

epsilon = [[3,-1,1],[-1,3,1],[1,1,3]],  adj(epsilon) = [[8,4,-4],[4,8,-4],[-4,-4,8]],

with eigenvalues {1,4,4} and {16,4,4}, respectively, and

det( K adj(epsilon) K + omega^2 epsilon ) = det(epsilon) omega^2 ( omega^2 - k^T epsilon k )^2.

That part is correct and worthwhile. It gives a clean non-birefringent constitutive closure: two transverse polarizations have the same dispersion even though their common speed is direction-dependent.

My publication verdict would be:

* **Paper VIII:** promising and mathematically interesting, but requires **major revision**, primarily because the physical interpretation as an *induced action* is stronger than the current derivation supports.
* **Paper IV:** presently a **working technical draft**, not yet a submission-ready paper. Its central kinematic calculation appears algebraically sound, but it is described as "birefringence" when it is actually directional dispersion anisotropy, and the physical meaning of the transfer-matrix eigenphase needs much more justification.

## Paper VIII: what is strongest

The best contribution is the theorem Q_B = adj(P), derived from the hop-vector matrix M, with P = M M^T. This is compact, general, and not peculiar to the numerical lattice values. The associated doubled-root dispersion is also a genuine theorem, not merely a numerical observation. The geometrical explanation of the special direction as the omitted fourth cube diagonal is clear and memorable.

The temporal-link observation is also useful. Treating the on-site scalar-potential phase as a temporal gauge link is standard in spirit and provides a natural temporal plaquette: Theta_a = A_0(x) - A_0(x + V_a) = V_a . E. This makes the proposed electric tensor P = sum_a V_a V_a^T plausible and geometrically well motivated.

The paper is also unusually candid about the remaining common-mode speed anisotropy. Distinguishing anisotropy shared by both polarizations from polarization birefringence is exactly right.

## Paper VIII: the principal scientific gap

The engine experiment verifies that the tick rule contains the phase A_0 = omega + V(x). It does **not yet establish that integrating out the matter dynamics produces** Gamma^(2)[E] proportional to sum_a (V_a . E)^2 with no cross-plaquette terms and with the claimed weighting.

Recovering delta_phi from one application of `HopOperator.step` validates the **vertex or coupling**, not the **quadratic effective action**. To call P the induced permittivity, one needs something equivalent to epsilon_ij proportional to d^2 Gamma[A] / (dE_i dE_j) at A=0, with Gamma[A] = -log det T[A], or a directly measured second-order energy/current response. Gauge invariance and D_3d symmetry constrain the answer, but they do not by themselves force the eigenvalue ratio 1:4. A general D_3d-invariant quadratic form has two independent coefficients. Cross terms between temporal plaquettes can change that ratio.

Consequently, the present evidence supports language such as "geometric candidate for the electric response block" or "plaquette-induced electric quadratic form" more securely than "the exact induced-action permittivity."

This concern also applies, at least conceptually, to the magnetic block unless Paper I genuinely derives it from an effective-action Hessian rather than assuming an equal-weight Wilson plaquette action. The paper's statement that the geometric block is a "tree-level induced action" should be reconsidered: an action obtained by integrating out matter is normally a loop-level effective action, whereas a prescribed plaquette action is a bare geometric action.

## Important mathematical and logical corrections in Paper VIII

### 1. The general determinant coefficient is not 16
Page 8 says that for a "general symmetric epsilon" the determinant is 16 omega^2 (omega^2 - k^T epsilon k)^2. For general epsilon, the prefactor is det(epsilon), not 16. Sixteen is the determinant of the particular lattice matrix. Paper IV gives the correct general form.

### 2. Use the proportional closure as the physically relevant theorem
The no-birefringence result survives mu^-1 = gamma adj(epsilon) for any positive scalar gamma. This is the correct formulation if the electric and magnetic sectors carry different overall normalizations. That change also resolves a problem in the O_h average. The paper gives <epsilon> = 3I, <mu^-1> = 8I. But adj(3I) = 9I != 8I. Thus the **exact equality** mu^-1 = adj(epsilon) does not survive averaging. The proportional condition does: 8I = (8/9) adj(3I). The averaged medium remains non-birefringent because it is isotropic, but the manuscript should not say that the exact adjugate relation survives averaging.

### 3. "Covariant completion" overstates what has been shown
The algebra demonstrates an impedance-matched, non-birefringent anisotropic constitutive medium. It does not by itself establish Lorentz covariance or boost symmetry in the original lattice coordinates. A safer section title would be "The constitutive closure" or "The non-birefringent electric-magnetic completion". To retain "covariant," construct the complete four-dimensional constitutive tensor chi^{mu nu rho sigma}, show that it is metric-induced or satisfies the electromagnetic closure relation, and state precisely which effective metric and time normalization result.

### 4. The coupling-normalization discussion needs correction
A single common factor 1/g^2 multiplying both the electric and magnetic parts of the action cancels from the source-free equations of motion and therefore does **not** set the photon speed. The speed is determined by the **relative** electric/magnetic normalization, including temporal-versus-spatial lattice scales.

### 5. The status language contradicts itself
The audit table labels gauge-sector birefringence as PASS, and the body repeatedly says it is settled. Page 10 then says the "unconditional birefringence verdict is held partial." The vacuum-domain issue cannot revive polarization splitting according to the preceding theorem, so these statements must be reconciled. My recommendation is:
* Null polarization split conditional on the proposed blocks: PASS.
* Derivation of the blocks as the actual dynamical effective action: PART.
* Common-mode isotropy: PART.
That status assignment would accurately identify where the uncertainty really lies.

## Paper IV: the central terminology problem

Section 2 does not derive birefringence in the usual physical sense. Birefringence means two polarization eigenmodes with different phase or group velocities **for the same propagation vector**. The paper instead compares propagation in different directions: k perpendicular to n_* (maximal group speed); k parallel to n_* (zero group speed). That is **uniaxial directional dispersion anisotropy**, not an ordinary/extraordinary polarization split. The two lambda_± branches are the two eigenvalue branches of the spinor transfer matrix -- apparently positive/negative-frequency or paired spinor branches -- not two optical polarizations at fixed k.

I would rename the paper along the lines of "Optical-Axis Dispersion Anisotropy on the A=1 Discrete Causal Lattice" and rename Proposition 2.1 "Axial-transverse group-velocity contrast". The gauge-sector result may properly discuss birefringence because it explicitly compares the two transverse Maxwell polarization roots.

## Paper IV: the transfer-matrix interpretation needs proof

The eigenvalues are lambda_± = i sin(omega/2) ± cos(omega/2) |H~(k)|. Away from the optical axis, |lambda_±|^2 = sin^2(omega/2) + cos^2(omega/2) |H~|^2 < 1. Thus T(k) is not unitary on those modes. Its eigenvalues contain both phase evolution and attenuation or amplitude renormalization. Taking theta(k) = arg lambda_+(k) and identifying grad_k theta as a physical group velocity is not automatically valid for a nonunitary transfer operator. The paper needs to derive wave-packet motion for this evolution, including the momentum dependence of |lambda|, or explain precisely how the A=1 normalization converts it into a unitary physical propagator.

The photon-limit discussion makes the issue especially visible. At omega=0, lambda_± = ± |H~|, so the phase is momentum-independent and the eigenphase group velocity is zero everywhere. The manuscript then calls the curvature of |H~| a "photon dispersion-curvature split." But curvature of an eigenvalue's **magnitude** is attenuation or filtering curvature unless a further physical argument turns it into energy dispersion. Until that mapping is supplied, the safe claim is: the transfer operator has an exact axial-transverse anisotropy in its structure-factor magnitude. It is not yet demonstrated that this is a photon energy dispersion.

Relatedly, a massless limit of a spinor propagator is ordinarily a massless spinor mode, not automatically a photon. The paper needs a concise standalone explanation of how the two-component mode acquires the physical representation, helicity content, and gauge character of a photon.

## A concrete notation error in Paper IV

Equation (15) defines K = [k_hat]_× but then gives omega^2 = k^T epsilon k. These are two different formulations:
* With K = [k]_× (unscaled), the dispersion is omega^2 = k^T epsilon k.
* With K = [k_hat]_× (unit), the generalized eigenvalue is the squared phase speed v^2 = k_hat^T epsilon k_hat.
Use one formulation consistently.

## How the two papers work together

At present, the gauge-sector material in Paper IV substantially repeats Paper VIII. The claim of "independent confirmation" should also be softened: it is a separate implementation and useful cross-check, but it uses the same framework, same engine, same geometric objects, and same author. "Independent code-path verification" would be more accurate.

I see two good editorial choices:
1. **Make Paper VIII the complete gauge-response paper.** Paper IV then becomes a shorter paper solely about the spinor/transfer-operator anisotropy, with the gauge result summarized in one section.
2. **Merge the papers.** The shared optical axis is the conceptual unity, and one stronger paper may be preferable to two overlapping drafts.
The first option is probably cleaner if the series architecture matters.

## Presentation and publication readiness

Paper VIII is structurally mature, but it still needs:
* external literature on anisotropic Maxwell media, lattice gauge actions, temporal plaquettes, constitutive closure, and observational Lorentz-anisotropy constraints;
* corrected PDF metadata, which currently contains "Author Name," "Your Paper Title," and placeholder keywords;
* removal of the acknowledgement TODO;
* correction of overfull monospace paths;
* a less compressed audit table, perhaps moved to a landscape appendix.

Paper IV visibly retains placeholder abstract, introduction, scope, worked examples, conclusion, acknowledgements, appendices, and a fictitious sample reference. It is therefore not yet ready for scientific circulation beyond trusted collaborators.

## Bottom line

There is a **real mathematical result here**: the Gram matrix of three hop vectors and the Gram matrix of their pairwise cross products are adjugates, and that closure produces a doubled transverse Maxwell root. That is elegant and defensible.

The major vulnerability is the step from "these are the natural temporal and spatial plaquette quadratic forms" to "these are the exact permittivity and inverse permeability induced by the dynamical lattice." That step remains to be demonstrated through the effective action or a genuinely dynamical response calculation. Until then, the null-birefringence theorem is rigorous **conditional on the proposed constitutive tensors**, but the derivation of those tensors as the physical vacuum response remains partial.
