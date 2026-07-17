---
handoff: 2026-07-17-paper04-paper08-external-review
from: PM (dcl-website session)
to: dcl-paper-04 + dcl-paper-08 (focused)
repo: [JackDMenendez/dcl-paper-04-optical-axis-birefringence, JackDMenendez/dcl-paper-08-electric-induced-action]
branch: main
commits: []                         # routes a review note; no code handed off
pr: none
status: consumed                    # SUPERSEDED — see superseded_by; the merge handoff below is the live directive
superseded_by: 2026-07-17-execute-iv-viii-merge-into-paper04   # user chose MERGE (2026-07-17): IV+VIII → one paper in dcl-paper-04
state: complete                     # review delivered; the revisions are the consuming sessions' work
semver: n/a (external review, not a software change)
flags:
  - "REVIEWER VERDICTS: Paper VIII = MAJOR REVISION (the 'induced action / exact permittivity' claim exceeds the derivation); Paper IV = WORKING DRAFT, not submission-ready. This TEMPERS the 2026-07-16 'VIII done except the PASS flip' picture — VIII's central framing is challenged, not just its verdict row."
  - "PAPER IV TERMINOLOGY (correctness-of-claim): Section 2 is NOT birefringence. It compares different k-DIRECTIONS (k⊥n_* fast, k∥n_* zero group speed) = uniaxial DIRECTIONAL DISPERSION ANISOTROPY, not a polarization split at fixed k. The two λ_± are spinor transfer-matrix branches, not two optical polarizations. Only the GAUGE-sector result (two transverse Maxwell roots) earns the word 'birefringence'."
  - "PAPER IV TRANSFER-MATRIX NON-UNITARITY (interpretation gap): off-axis |λ_±|² = sin²(ω/2) + cos²(ω/2)|H~|² < 1, so T(k) is NOT unitary; identifying grad_k arg λ_+ as a physical group velocity is not automatically valid. At ω=0 the eigenphase group velocity is zero everywhere and curvature of |H~| is FILTERING/attenuation curvature, NOT proven photon energy dispersion. Central claim needs a derivation."
  - "PAPER VIII INDUCED-ACTION OVERCLAIM: recovering δφ = ω + V from one HopOperator.step validates the VERTEX/COUPLING, not the quadratic effective action Γ^(2). D_3d symmetry allows TWO independent coefficients — it does NOT force the ε eigenvalue ratio 1:4. Downgrade to 'geometric candidate for the electric response block' unless the ∂²Γ/∂E∂E derivation (or a measured 2nd-order response) is supplied."
  - "PAPER VIII ADJUGATE DOES NOT SURVIVE O_h AVERAGING: adj(3I)=9I ≠ 8I, so the EXACT μ⁻¹=adj(ε) fails under averaging; only the PROPORTIONAL closure μ⁻¹=γ·adj(ε) survives (8I = (8/9)·adj(3I)). The averaged medium is non-birefringent by isotropy, not by the exact adjugate identity."
  - "PAPER VIII p.8 PREFACTOR ERROR: the general Fresnel determinant prefactor is det(ε), NOT 16 (16 is the specific lattice value). Paper IV already has the correct general form."
  - "PAPER VIII STATUS SELF-CONTRADICTION: audit table says gauge birefringence PASS while p.10 says 'held partial'. Reconcile to the three-way split (matches board #23 audit-row split): null polarization split conditional on the blocks = PASS; blocks as the actual dynamical effective action = PART; common-mode isotropy = PART."
  - "POSITIVE ANCHOR (do NOT weaken): the theorem Q_B = adj(P) with P = M Mᵀ (Gram matrix of the three hop vectors; Q_B the Gram matrix of their pairwise cross products) and the doubled transverse Maxwell root are CORRECT, general, and defensible — independently recomputed by the reviewer (ε eigenvalues {1,4,4}, adj(ε) {16,4,4})."
  - "EDITORIAL ARCHITECTURE (author/PM call, not a paper-session call): reviewer prefers Option 1 — VIII becomes the complete gauge-response paper, IV shrinks to the spinor/transfer-operator anisotropy with the gauge result summarized in one section; Option 2 = merge. This intersects the companion-publication decision and should go to the user before either session restructures."
decisions:
  - "PM is ROUTING this review verbatim (asset below); PM is not adjudicating the physics. Verdicts and corrections are the reviewer's, for the two paper sessions to act on and the user to arbitrate on the editorial-architecture question."
consumed_by:
consumed_at:
---

## Summary
An external-style review of Papers IV and VIII (authored in dcl-website,
`notes/Review_paper_04_and_08.md`) is routed here to both paper sessions. It
**affirms the core algebraic result** — the adjugate closure `Q_B = adj(P)` and
the doubled transverse Maxwell root are correct and elegant — but returns
**Paper VIII = major revision** and **Paper IV = working draft**, on two
load-bearing scientific objections (VIII overclaims an *induced action* where
only a *vertex* is verified; IV calls *directional dispersion anisotropy*
"birefringence" and treats a *non-unitary* transfer-operator eigenphase as a
group velocity without proof), plus a set of exact mathematical corrections. The
verbatim review is preserved as the asset beside this file; the per-paper action
lists below split it so neither session has to infer what is theirs.

## Verbatim source
`handoffs/assets/2026-07-17-review-paper-04-and-08-source.md` (exact wording,
math as-authored). Every equation is restated in prose-forward form there and in
the flags above. Origin file: dcl-website `notes/Review_paper_04_and_08.md`.

## What the reviewer confirms (anchor — keep)
- `Q_B = adj(P)`, `P = M Mᵀ` (Gram matrix of the three hop vectors; `Q_B` the
  Gram matrix of their pairwise cross products): compact, general, lattice-value-
  independent. Doubled-root dispersion is a genuine theorem.
- The temporal-link / temporal-plaquette picture `Θ_a = A_0(x) − A_0(x+V_a) =
  V_a·E`, hence `P = Σ_a V_a V_aᵀ`, is geometrically well motivated.
- The candor about the residual common-mode speed anisotropy (shared by both
  polarizations, distinct from a polarization split) is exactly right.

## → Consumer actions — Paper VIII session (`dcl-paper-08-electric-induced-action`)
- [ ] **Downgrade the induced-action claim.** Replace "the exact induced-action
      permittivity" with "geometric candidate for the electric response block" /
      "plaquette-induced electric quadratic form" — UNLESS you supply the
      effective-action derivation `ε_ij ∝ ∂²Γ[A]/∂E_i∂E_j |_{A=0}`,
      `Γ[A] = −log det T[A]` (or a directly measured 2nd-order energy/current
      response). State explicitly that a general D_3d-invariant quadratic form has
      two free coefficients and the 1:4 ratio is not symmetry-forced.
- [ ] **Fix p.8 prefactor:** general Fresnel determinant prefactor is `det(ε)`,
      not `16`.
- [ ] **Adopt the proportional closure** `μ⁻¹ = γ·adj(ε)` (any positive scalar
      γ) as the physically relevant theorem; correct the O_h-average text — the
      EXACT adjugate identity does NOT survive averaging (`adj(3I)=9I≠8I`); the
      averaged medium stays non-birefringent only because it is isotropic.
- [ ] **Retitle "covariant completion"** → "the constitutive closure" /
      "non-birefringent electric–magnetic completion", unless you build the full
      4D constitutive tensor `χ^{μνρσ}` and state the effective metric + time
      normalization it implies.
- [ ] **Fix the coupling-normalization discussion:** a common `1/g²` cancels
      from the source-free EOM and does NOT set the photon speed; the speed is
      set by the RELATIVE electric/magnetic normalization (incl. temporal-vs-
      spatial lattice scales).
- [ ] **Reconcile the status language** to the three-way split (this is the
      board #23 audit-row split): null polarization split (conditional on the
      blocks) = PASS; blocks as the actual dynamical effective action = PART;
      common-mode isotropy = PART. Remove the PASS-vs-"held partial" contradiction.
- [ ] **Reconsider "tree-level induced action"** wording — a matter-integrated
      action is a loop-level effective action; a prescribed plaquette action is a
      bare geometric action. (Same caveat conceptually touches the magnetic block
      unless Paper I derives it from an effective-action Hessian.)
- [ ] **Presentation:** fix PDF metadata placeholders ("Author Name", "Your
      Paper Title", placeholder keywords); remove the acknowledgement TODO; fix
      overfull monospace paths; de-compress the audit table (consider a landscape
      appendix); add external literature (anisotropic Maxwell media, lattice
      gauge actions, temporal plaquettes, constitutive closure, observational
      Lorentz-anisotropy constraints).

## → Consumer actions — Paper IV session (`dcl-paper-04-optical-axis-birefringence`)
- [ ] **Fix the central terminology.** Section 2 is uniaxial directional
      dispersion anisotropy, NOT birefringence (no polarization split at fixed
      k). Rename the paper (reviewer suggestion: "Optical-Axis Dispersion
      Anisotropy on the A=1 Discrete Causal Lattice") and Proposition 2.1
      ("Axial–transverse group-velocity contrast"). Reserve "birefringence" for
      the gauge-sector result (two transverse Maxwell roots), which earns it.
- [ ] **Prove the transfer-matrix interpretation.** T(k) is non-unitary off-axis
      (`|λ_±|²<1`); justify identifying `grad_k arg λ_+` as a physical group
      velocity — derive wave-packet motion including the momentum dependence of
      `|λ|`, or show how the A=1 normalization yields a unitary physical
      propagator. Address the ω=0 case where the eigenphase group velocity is
      zero everywhere and `|H~|`-curvature is filtering/attenuation curvature,
      not yet a photon energy dispersion.
- [ ] **Justify photon identity.** A massless spinor-propagator limit is a
      massless spinor mode; add a standalone argument for how the two-component
      mode acquires the representation, helicity content, and gauge character of
      a photon.
- [ ] **Fix eq (15) notation:** pick ONE — `K=[k]_×` with `ω²=kᵀεk`, OR
      `K=[k̂]_×` with the squared phase speed `v²=k̂ᵀεk̂`. Do not mix.
- [ ] **Soften "independent confirmation"** → "independent code-path
      verification" (same framework, engine, geometric objects, author as VIII).
- [ ] **Presentation:** fill the placeholder abstract, introduction, scope,
      worked examples, conclusion, acknowledgements, appendices; remove the
      fictitious sample reference.

## → Consumer actions — PM / user (editorial + coordination)
- [ ] **Editorial-architecture decision (needs the user):** Option 1 (VIII = the
      complete gauge-response paper; IV shrinks to spinor/transfer-operator
      anisotropy) vs Option 2 (merge). Reviewer prefers Option 1. This intersects
      the companion-publication plan — decide before either session restructures.
- [ ] **Board reconciliation (PM):** this review tempers the 2026-07-16
      "audit-PASS / VIII done except PASS flip" status. Consider annotating
      board #23 (VIII) and #13 (IV) that an external review returned major-
      revision / working-draft, and that the gauge-sector "PASS" is really
      "conditional-on-blocks PASS" pending the effective-action derivation.
- [ ] **Cross-links:** relates to `2026-07-16-paper08-verdict-delivered-paper04-
      unblocked` (the status this review tempers) and
      `2026-07-16-paper08-paper04-companion-publication` (the joint-release track).
