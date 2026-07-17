---
handoff: 2026-07-16-paper08-paper04-companion-publication
from: dcl-paper-08 (focused)
to: dcl-paper-04 (focused)
repo: JackDMenendez/dcl-paper-08-electric-induced-action
branch: main
commits: [fd84dbd, a0f5f9b, 4bc0035, 21112ea, 4d59a4b]
pr: none
status: open
state: complete
semver: n/a (paper VIII v0.1-DRAFT, unreleased; companion release with Paper IV planned)
flags:
  - "COMPANION-PUBLICATION PLAN ASSUMES Paper IV is ungated and lands in days. If IV
     slips or a complication surfaces, VIII's fallback is to publish STANDALONE with the
     birefringence-verdict row at PART (the analytic verdict is complete and honest on its
     own). Do not let the coupling become a deadlock -- VIII is upstream of IV."
  - "VIII is HOLDING finalization of its introduction, conclusion, AND abstract pending
     IV's results, deliberately, in case IV bears on the framing (esp. if the speed
     anisotropy turns out physical -> the 'clean null' wording changes). Do not treat
     VIII's current abstract as final."
  - "The birefringence cancellation is DECOUPLED from the speed anisotropy (proven in VIII:
     the adjugate cancellation holds in every single trigonal domain AND under the O_h
     4-domain average). So even if IV's large-N run finds a real vacuum-speed anisotropy,
     the birefringence verdict still stands; only VIII's SEPARATE 'vacuum speed isotropy'
     row is affected. Keep the two questions distinct in IV's write-up too."
  - "VIII's electric block eps=P and the relation mu^-1 = adj(eps) are what IV must feed
     its dispersion computation. The cancellation is prefactor-independent (immune to the
     undetermined a_t / 1/g^2). If IV's numbers disagree with VIII's blocks, that is a
     RED FLAG to reconcile before either publishes -- not a thing to paper over."
decisions:
  - "Publish VIII and IV as COMPANION papers, simultaneously, cross-cited: VIII supplies
     the analytic derivation + proven cancellation; IV supplies the large-N numerical
     confirmation. This lets VIII's verdict row reach PASS by citing IV. (PM/author call,
     2026-07-16, on the basis that IV is days from done.)"
  - "SPLIT VIII's birefringence audit into two rows: (a) 'gauge-sector birefringence
     verdict (cancels)' -> PASS on IV's numerical confirmation; (b) 'vacuum speed isotropy
     / O_h restoration' -> its own row, status set by what IV's large-N dispersion shows.
     Justified because the two are proven decoupled -- this is honest decomposition, not
     status-gaming."
consumed_by:
consumed_at:
---

## Summary

Paper VIII's electric induced-action derivation is complete and the gauge-sector vacuum
birefringence verdict is analytically settled: the electric permittivity block is
`eps = P = {1,4,4}` (optical axis `(1,1,-1)` suppressed), the magnetic block is its
adjugate `mu^-1 = Q_B = adj(eps) = {4,4,16}`, and the photon dispersion is a doubled
transverse root -- so **gauge-sector vacuum birefringence cancels**, prefactor-independently
and for any hop vectors. `eps=P` is engine-verified (read off `HopOperator.step`). The
blocks and covariant completion are PASS; the birefringence verdict is PART, pending an
independent large-N numerical confirmation -- which is Paper IV's deliverable. The plan
(author decision, 2026-07-16) is to **publish VIII and IV as companion papers**, so IV's
confirmation lifts VIII's verdict to PASS and the two release together cross-cited.

## Shipped (Paper VIII, this session)

- `fd84dbd` — analytic derivation: electric block `P`, adjugate theorem `mu^-1=adj(eps)`,
  conditional birefringence verdict (doubled transverse root).
- `a0f5f9b` — engine verification `exp_01`: `eps=P` read off `HopOperator.step`
  (`delta_phi=omega+V` recovered to 1e-19); electric-block + covariant-completion rows
  STUB/PART -> PASS.
- `4bc0035` — the derivation section (`paper/sections/electric_block.tex`), abstract, bib.
- `21112ea` — claim-auditor fixes (twice-audited; verdict "publication-honest").
- `4d59a4b` — speed-anisotropy analysis: optical axis IS the 4th cube body-diagonal
  (trigonal `D_3d`); `O_h` 4-domain average restores isotropy (`<eps>=3I,<mu^-1>=8I`);
  cancellation decoupled from the anisotropy.

## Verification

- `src/utilities/electric_induced_action.py` — all checks PASS (symbolic + numeric sweep
  2e4 random k, split <1e-14).
- `src/experiments/exp_01_electric_permittivity_extraction.py` — PASS (engine read-off,
  fault-injection-proven to depend on the coupling).
- Two independent claim-auditor passes (incl. engine fault-injection) -> "substantially
  publication-honest".
- Paper builds clean: pdflatex + bibtex, 11 pages, no undefined refs/citations.

## Remaining (Paper VIII, held on purpose)

- Introduction, conclusion, and final abstract wording -- held pending IV (see flags).
- The PART -> PASS flip + cross-citation, once IV's confirmation lands.

## Decisions & flags

See frontmatter. The load-bearing items: the companion plan assumes IV is near-term (with a
standalone-PART fallback); VIII is holding intro/conclusion/abstract pending IV; and the
birefringence cancellation is decoupled from the speed anisotropy (a real proof, so the
verdict survives whatever IV finds about the vacuum speed).

## -> Consumer actions (Paper IV session)

- [ ] **Feed IV's dispersion computation with VIII's blocks**: `eps = P =
      [[3,-1,1],[-1,3,1],[1,1,3]]` and `mu^-1 = Q_B = adj(eps) =
      [[8,4,-4],[4,8,-4],[-4,-4,8]]` (bases per `electric_block.tex`). Confirm IV's own
      `(eps,mu^-1)` match these; a mismatch is a red-flag to reconcile before publishing.
- [ ] **Confirm the birefringence cancellation numerically at large N** (IV's full E+B
      photon-dispersion classification). A confirmed null polarization split is what lifts
      VIII's 'birefringence verdict (cancels)' row from PART to PASS.
- [ ] **Report whether IV's large-N run resolves the vacuum-structure question**: does the
      physical vacuum show the factor-~2 common-mode speed anisotropy about `(1,1,-1)`
      (single trigonal domain) or not (`O_h`-restored, isotropic)? This sets the status of
      VIII's separate 'vacuum speed isotropy / O_h restoration' row. Keep it distinct from
      the birefringence result.
- [ ] **Agree the companion cross-citation** (back-to-back submission; VIII cites IV for the
      numerical verdict, IV cites VIII for the derivation and blocks).
- [ ] **Board**: update issue #23 (repo `discrete-causal-lattice-project`, project 6) to
      note VIII's analytic verdict is complete and VIII/IV are on a companion track; link
      commits `fd84dbd..4d59a4b`. Reconcile with the blocks it gates (#13/#17/#18/#19).
- [ ] **PM / gate**: the 2026-07-09 "VIII held upstream of IV v1.0" ruling is superseded by
      the companion-publication decision -- record this so VIII's CLAUDE.md scope-gate and
      the board reflect a joint release, not a one-way hold.
- [ ] **On IV's confirmation landing**: ping the VIII session (or file a return handoff to
      `dcl-paper-08-electric-induced-action`) with the large-N result + the vacuum-speed
      readout, so VIII flips the verdict row PART->PASS, adds the cross-cite, and writes its
      held intro/conclusion/abstract for the joint release.
