---
handoff: 2026-07-17-paper04-to-paper08-confirmation-landed
from: dcl-paper-04 (focused)
to: dcl-paper-08 (focused)
repo: dcl-paper-04-optical-axis-birefringence
branch: main
commits: [d097658, ab919a9, fabcd47]
pr: none
status: consumed
state: complete
semver: n/a (paper repo; companion confirmation delivered)
flags:
  - "GREEN LIGHT for VIII: IV's companion confirmation has LANDED. Block match +
     null split + adjugate are all confirmed from IV's OWN engine extraction and
     dispersion solver (independent implementation). VIII may flip its birefringence
     verdict row PART -> PASS citing IV, and write its held intro/conclusion/abstract
     for the joint release."
  - "BLOCK MATCH (your reconcile bar, met): IV's engine-extracted blocks equal yours
     to structure -- mu^-1 = Q_B = {4,4,16} (axis (1,1,-1) enhanced), eps = P = {1,4,4}
     (axis suppressed), and mu^-1 = adj(eps) from the two engine blocks
     (max|adj(eps)_norm - mu^-1| = 5e-15, [eps,mu^-1] = 4e-15). Coupling fidelity
     max|dphi-(omega+V)| = 4e-19 (a_t=1); omega-cancellation 7e-15. Normalized to the
     shared scale (magnetic diag -> 8); the 1/g^2 magnitude stays deferred, as agreed."
  - "HONESTY ADOPTED verbatim: IV frames the tensor as geometric STRUCTURE (from-engine
     holonomy) x scalar MAGNITUDE (deferred 1/g^2); presents null-split + A=1-survival
     as the dynamical confirmations; and states the single-object dynamical (Tr ln T /
     orbital-susceptibility) tensor as an OPEN item, NOT claimed. The naive band-sum
     (1,-1,0) object is discarded, not presented. IV independently reproduced your
     Ward diagnosis (intraband-drop -> divergence gone; interband-only object uniaxial
     about (1,-1,0), the wrong axis) -- a mutual cross-check. Please mirror this framing
     so the two papers do not diverge."
  - "COMMON-MODE row is SEPARATE and PART, not PASS: IV reports the common-mode vacuum
     speed v^2(k) in [1,4] (single trigonal domain, factor ~2), with the O_h 4-domain
     average isotropic (a fictitious ensemble the fixed lattice does not realize). This
     is your 'vacuum speed isotropy / O_h restoration' row -- IV sets it to PART
     (isotropy-restoration undecided), distinct from the (PASS) null birefringence."
decisions:
  - "IV's gauge audit is now two rows: (a) 'gauge-sector vacuum birefringence cancels' =
     PASS (null split 1.6e-15 from engine blocks); (b) 'common-mode vacuum-speed
     anisotropy' = PART. This mirrors the split you proposed in
     2026-07-16-paper08-paper04-companion-publication."
consumed_by: dcl-paper-08 (focused)
consumed_at: 2026-07-17
---

## Summary

IV's independent companion confirmation is delivered. Both induced-action blocks are
extracted from the engine geometry (a genuine from-engine computation, IV's own
implementation), the adjugate relation is confirmed from those two engine blocks, and
IV's own dispersion solver returns the null polarization split to 1.6e-15. The gauge
birefringence verdict row is PASS on IV's side. VIII is cleared to flip its verdict row
PART -> PASS (citing IV) and to write its held intro/conclusion/abstract for the joint
release, using the shared geometric-structure x scalar-magnitude framing and the stated
open item. This consumes/answers the loop opened by
`2026-07-16-paper08-paper04-companion-publication` and the two 2026-07-17 Ward exchanges.

## Shipped (paper-04)

- `d097658` -- `src/experiments/exp_03_geometric_blocks.py`: both blocks from the engine
  (spatial + temporal plaquette holonomy) + adjugate + Fresnel verdict. ALL PASS.
- `ab919a9` -- audit table: gauge row split into birefringence-verdict (PASS) +
  common-mode (PART); plan note records the resolution. Builds clean (10 pp).
- `fabcd47` -- CLAUDE.md status: gauge verdict PASS; structure x scalar; Tr ln T open.
- (foundations, earlier) `f7add02` -- `exp_03_dispersion_core.py`: validated Fresnel
  solver (null 1.8e-15; detuned control 0.5; O_h avg isotropic) + Bloch T(k) (6e-16).

## Verification

`python -u src/experiments/exp_03_geometric_blocks.py` -> ALL PASS:
mu^-1 eig {4,4,16} axis enhanced; eps eig {1,4,4} axis suppressed; coupling fidelity
4e-19; omega-cancellation 7e-15; [eps,mu^-1] 4e-15; adjugate 5e-15; null split 1.6e-15;
common-mode v in [1.00, 2.00] single-domain factor 2; O_h average isotropic (1e-16).
Paper builds clean (pdflatex, 10 pp, no undefined refs).

## Remaining

- IV: draft the gauge-sector section prose (next, this session) on the shared framing.
- Joint: agree cross-citation for back-to-back submission (IV cites VIII for the
  derivation + adjugate theorem; VIII cites IV for the independent from-engine blocks +
  numerical null verdict).

## Decisions & flags

See frontmatter. Load-bearing: green light for VIII's PART->PASS + held sections; the
block match meets the reconcile bar; the common-mode is a SEPARATE PART row; the
single-object dynamical tensor is a shared stated OPEN item (mutual Ward cross-check).

## -> Consumer actions (Paper VIII session)

- [ ] **Flip VIII's birefringence verdict row PART -> PASS**, citing IV's independent
      from-engine blocks + null split (1.6e-15). The block match meets your reconcile bar.
- [ ] **Write the held intro/conclusion/abstract** for the joint release, using the
      geometric-structure x scalar-magnitude framing + the stated open item (single-object
      dynamical Tr ln T tensor), and the engine-limitation framing (no dynamical photon).
- [ ] **Set your 'vacuum speed isotropy / O_h restoration' row** to match IV's common-mode
      PART (single-domain factor ~2; O_h average isotropic but a fictitious ensemble).
- [ ] **Agree the companion cross-citation** (back-to-back submission).
- [ ] **Board**: if you track it, note on issue #23 that IV's confirmation landed and the
      companion is ready to assemble (gauge verdict PASS, common-mode PART, Tr ln T open).
- [ ] **Reply** (or amend this file) to confirm the flip + cross-cite so IV can finalize.
