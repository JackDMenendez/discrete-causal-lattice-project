---
handoff: 2026-07-17-paper04-merge-complete
from: dcl-paper-04 (focused)
to: PM
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: [54d1d1c, bdc7bf3, 0a8592f, b6d2e3c, e466ba3]
pr: none
status: consumed
state: complete
semver: n/a (paper merge + review revision; no software release)
flags:
  - "MERGE DONE: Paper VIII is merged into Paper IV, homed in dcl-paper-04 (slug
     unchanged). VIII folded in via git subtree (history preserved, merge commit
     bdc7bf3); scripts/fragments/notes relocated into paper-04; unified gauge section
     written; paper08/ scaffolding removed; dcl-paper-08 archived read-only with a
     tombstone (dc54624). Board: #23 closed as merged-into-#13; #13 retitled + scoped."
  - "NOT SUBMISSION-READY (reviewer verdict was working-draft; still true after
     revision). The paper builds clean (pdflatex+bibtex, 17 pp) and is claim-auditor-
     faithful, but the reviewer's DEEP physics items are addressed by honest reframing/
     caveats, NOT by new derivations: (a) the non-unitary transfer-operator eigenphase
     -> group-velocity reading is stated as requiring the A=1 normalization argument
     (not supplied); (b) the omega=0 magnitude-curvature is flagged as attenuation, not
     a proven photon dispersion; (c) the massless-spinor->photon identity is not carried
     out; (d) the gauge blocks are downgraded to geometric candidates (the dynamical
     Gamma^(2) / Tr ln T tensor stays an open item). These are genuine open physics, not
     wording -- deciding whether to derive them or ship with the caveats is a user call."
  - "RETITLED: 'Optical-Axis Anisotropy on the A=1 Discrete Causal Lattice: Kinematic
     Dispersion and the Gauge-Sector Birefringence Cancellation'. Repo slug stays
     dcl-paper-04-optical-axis-birefringence. The dcl-website refs (roadmap.json URL +
     v0.3.0 news post) point at the SLUG, which is unchanged, so no site edit is needed;
     if the PM wants the site's displayed TITLE updated, that is a dcl-website edit."
  - "AFFIRMED ANCHOR kept intact AND now FEATURED as named theorems (per the amended
     merge directive's 'Affirmed results -- FEATURE these' section, commit 2d8af44,
     added after first read): Theorem (adjugate Q_B=adj(P), general hop vectors) +
     Corollary (the {1,4,4}/{16,4,4} lattice blocks); Theorem (doubled transverse
     root / no gauge-sector birefringence, with the det(eps) Fresnel factorization);
     the temporal-plaquette origin of P and the omitted-4th-cube-diagonal geometry are
     featured as the electric-block origin and the optical-axis anchor. Paper-04
     commit c299a95; builds clean (18 pp)."
decisions:
  - "Editorial architecture resolved as MERGE (user, 2026-07-17), executed here. The
     companion-publication track (2026-07-16-paper08-paper04-companion-publication) and
     the separate-review routing (2026-07-17-paper04-paper08-external-review) are
     superseded/consumed."
consumed_by: PM (dcl-website session) — board verified (#23 closed / #13 retitled); merge status + falsifiability recorded to memory; push + archive + submission-readiness folded into 2026-07-18-paper04-falsifiability-do-both-decision
consumed_at: 2026-07-18
---

## Summary

The IV+VIII merge is complete. Paper VIII is folded into Paper IV (history-preserving
subtree), the two papers are now one, the external review's corrections are applied, the
paper builds clean and passes the claim-auditor, and dcl-paper-08 is archived with a
tombstone. The paper is a review-revised working draft, not yet submission-ready: the
reviewer's deep physics objections are handled by honest caveats rather than new
derivations, which is a user call to close out.

## Shipped (paper-04)

- `54d1d1c` WIP abstract/intro checkpoint (clean tree for the subtree).
- `bdc7bf3` subtree add of dcl-paper-08 (history preserved).
- `0a8592f` unified gauge section + all review corrections + retitle + audit three-way
  split + metadata.
- `b6d2e3c` cleanup: VIII notes -> notes/; paper08/ scaffolding removed.
- `e466ba3` claim-auditor fix: 'birefringence' reserved for the gauge sector.
- dcl-paper-08 `dc54624`: tombstone README + archived-CLAUDE.md (held-upstream gate retired).

## Corrections resolved (from the external review)

Paper VIII side: induced-action -> geometric candidate (vertex verified, not Gamma^(2);
D_3d two free coefficients, 1:4 not symmetry-forced); det(eps) prefactor (not 16);
proportional closure mu^-1 = gamma*adj(eps); exact adjugate fails O_h averaging
(adj(3I)=9I != 8I); 'constitutive closure' not 'covariant completion'; 1/g^2 relative-
vs-common normalization; bare-geometric vs loop-level action; status reconciled to the
three-way split. Paper IV side: 'birefringence' -> directional dispersion anisotropy;
Prop -> 'axial-transverse group-velocity contrast'; non-unitarity + omega=0 + photon-
identity caveats; eq-notation consistency; 'independent confirmation' -> 'independent
code-path verification'; placeholder abstract/intro written; fictitious reference removed.
Presentation: PDF metadata fixed; section headings updated.

## Verification

`python -u src/utilities/electric_induced_action.py` ALL PASS (fragments regenerated with
the det(eps) fix). Paper builds clean: pdflatex + bibtex, 17 pp, no undefined refs/
citations, no duplicate labels. Claim-auditor (merged sections vs the five-row audit
table): faithful, no overstatement.

## Remaining (user / PM)

- **User physics call:** derive the group-velocity/photon interpretation and/or the
  dynamical Gamma^(2) tensor, or ship with the honest caveats (flags). This is the gap
  between 'review-revised working draft' and 'submission-ready'.
- **Literature:** the reviewer asked for external references (anisotropic Maxwell media,
  lattice gauge actions, temporal plaquettes, constitutive closure, observational
  Lorentz-anisotropy bounds). Not yet added.
- **Presentation polish:** de-compress the audit table (landscape appendix) if desired;
  acknowledgements still a stub.

## -> Consumer actions (PM / user)

- [ ] **Note the board is reconciled:** #23 closed (merged-into-#13), #13 retitled/scoped
      for the merged paper. Confirm this matches the roadmap.
- [ ] **Archive `dcl-paper-08` on GitHub** (read-only) -- the tombstone README + CLAUDE.md
      banner are committed (`dc54624`); the GitHub 'Archive repository' toggle is the
      owner's to flip.
- [ ] **Decide the submission-readiness gap** (the deep physics items in the flags):
      derive vs ship-with-caveats. Route back to this session with the call.
- [ ] **Optional site title:** the slug is unchanged so links still work; if you want the
      displayed paper title on dcl-website updated to the new title, that is a small
      dcl-website edit.
