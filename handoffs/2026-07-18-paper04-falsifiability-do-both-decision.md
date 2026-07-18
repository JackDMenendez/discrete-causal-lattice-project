---
handoff: 2026-07-18-paper04-falsifiability-do-both-decision
from: PM (dcl-website session)
to: dcl-paper-04 (focused)
repo: JackDMenendez/dcl-paper-04-optical-axis-birefringence
branch: main
commits: []                         # routes the author's falsifiability decision; no code handed off
pr: none
status: open
state: in-progress                  # the paper-04 session executes this
semver: n/a (falsifiability scoping decision + follow-on)
flags:
  - "DECISION (author, 2026-07-18): DO BOTH falsifiability channels — NOT a/b/c-exclusive. 2.b (kinematic sector) is the CONCRETE content written into this paper now; 2.a (gauge sector) is opened as a CONTINGENT follow-on. Their union is option (c) done right: a multi-channel falsifiability map with an honest per-channel status. Rationale: they are different FIELDS (photon = gauge; massive dispersion = kinematic), so they don't trade off; the ω=0 finding (photon ≠ massless spinor) forces the split."
  - "2.a MUST STAY CONTINGENT — do NOT re-assert a delivered photon falsifier. It is gated on TWO open items that are exactly the VIII 'major revision' work: (1) the effective-action derivation Γ⁽²⁾ / Tr ln T that legitimizes ε and μ⁻¹ as real vacuum response (not geometric candidates); (2) the O_h-restoration computation, which may return that the anisotropy CANCELS in the continuum limit → 2.a null. Present as open/derivation-pending, never as a bound in hand. Re-inflating this is the precise overclaim the reviewer caught."
  - "PUSH BLOCKER: paper-04 main is 33 commits AHEAD of origin — the ENTIRE merge (subtree bdc7bf3 … falsifiability 4018225 … claim-auditor 4e8da51) is LOCAL-ONLY, unpushed. None of the merge, retitle, or falsifiability work is on GitHub yet. Push before anything here is 'real', and BEFORE archiving dcl-paper-08 (its history only survives in the unpushed local paper-04 until then)."
  - "SCALE HONESTY (bake into the 2.b write-up): the kinematic anisotropy |H~|²=1−(4/3)|k⊥ a|² is a dim-6-scale effect (~(E/E_Planck)²) — the most-suppressed LV case. Even the best photon dim-6 bound (LHAASO, a≲3e-28 m ≈ 10⁷ ℓ_Planck) is weak; massive particles lose the cosmological lever arm. Expect an honest BOUND far above Planck, not a detection. The distinctive, defensible handle is the SIGNATURE not the magnitude: a fixed lattice axis → SIDEREAL modulation (SME anisotropic coefficients), which no isotropic theory fakes."
decisions:
  - "Do both channels; 2.b concrete-in-paper, 2.a contingent follow-on; reconcile the series falsifiability map to a multi-channel table (subsumes option c). Author call 2026-07-18, PM-relayed."
  - "Submission-readiness gap (from 2026-07-17-paper04-merge-complete) is thereby resolved as: SHIP the review-revised working draft with honest caveats + the multi-channel map NOW; pursue the 2.a derivations (Γ⁽²⁾, O_h restoration) as tracked follow-on rather than blocking this paper on them."
consumed_by:
consumed_at:
---

## Summary
The author's falsifiability call (relayed by PM): **do both 2.a and 2.b.** They
are complementary channels on different fields, not competing strategies, so the
thorough answer is to map both and state each honestly — which also puts the
series' falsifiability story to rest cleanly. This handoff carries that decision,
the guardrail that keeps 2.a from re-overclaiming, the still-open **push** blocker,
and the map reconciliation. It supersedes the pending decision in
`2026-07-17-paper04-falsifiability-and-a1-finding` and closes out the
submission-readiness question from `2026-07-17-paper04-merge-complete`.

## The decision, concretely

**2.b — write it into THIS paper now (it's analysis of an already-derived result).**
- Scope the falsifiable claim as the **kinematic massive-sector directional
  dispersion** (ω≠0), a **dim-6 anisotropic** effect tied to the optical axis n̂*.
- Include the **ω=0 magnitude/attenuation anisotropy** `|H~|²=1−(4/3)|k⊥|²` as a
  distinct *massless* handle (a direction-dependent filtering, NOT an energy
  dispersion — this is what `exp_01` measures).
- Observational handles to name (with honest testability caveats, not claims):
  the **sidereal-modulation** signature from the fixed lattice axis; high-energy
  astrophysical **neutrinos** as the one massive channel keeping some lever arm;
  the `exp_01`-type filtering anisotropy for the magnitude effect.
- State plainly that the expected **bound sits well above Planck** (dim-6
  suppression) — the value is a correctly-scoped honest limit + a distinctive
  signature, replacing the retired "clean kinematic dim-6 photon falsifier."

**2.a — open as a CONTINGENT follow-on (do not assert in this paper).**
- The falsifiable **photon** signal is the gauge-sector **common-mode speed
  anisotropy** (both polarizations share a direction-dependent speed even though
  birefringence cancels).
- Gate it explicitly on: (1) the **effective-action derivation** (Γ⁽²⁾ / Tr ln T)
  legitimizing ε, μ⁻¹; (2) the **O_h-restoration** computation (may null it out).
- Present it in the paper as the *named open channel we are still deriving*, with
  its status = open/PART, never as a delivered bound.

**Union = the multi-channel falsifiability map (option c, done right).** A table
with one row per channel, each with an honest status:
| channel | field | effect | status |
| kinematic massive dispersion | spinor | dim-6 directional, sidereal | PART (real, bound ≫ Planck) |
| kinematic massless anisotropy | spinor | ω=0 magnitude/filtering | PART (real observable, testability open) |
| gauge-sector photon anisotropy | U(1) gauge | common-mode speed anisotropy | OPEN (derivation + O_h pending; may be null) |
| optical-axis birefringence | gauge | polarization split | NULL — consistency check, not a falsifier |

## → Consumer actions (paper-04 session)
- [ ] **PUSH `main` to origin first** (33 commits). Nothing below is real on
      GitHub until this happens.
- [ ] **Write 2.b into the paper** per the scope above; make the dim-6 /
      above-Planck / sidereal-signature honesty explicit.
- [ ] **Add the 2.a contingent channel** to the falsifiability section + the
      map/table as OPEN (derivation + O_h pending) — contingent framing only.
- [ ] **Reconcile `notes/falsifiability_and_sme_mapping.md`** (and any program
      claim map) with the ω=0 finding: the SME dim-6 *photon* mapping assumed a
      photon dispersion the kinematic channel does not supply; re-file it under
      the gauge-sector (2.a, contingent) and add the kinematic-sector (2.b) rows.
- [ ] **Track 2.a as follow-on work** — it is the same gauge-sector
      effective-action + O_h-restoration program already behind the VIII revision
      (relates to board #17/#18/#19). Flag to PM if it needs its own board issue.
- [ ] **After push:** tell PM so PM can (a) confirm the merge is live, (b) flip
      the `dcl-paper-08` GitHub archive toggle (tombstone already committed
      `dc54624`), and (c) optionally update the dcl-website displayed paper title.
- [ ] **Literature / polish** (from merge-complete, still open): add the external
      references the reviewer asked for; de-compress the audit table; fill the
      acknowledgements stub. Submission-readiness = ship-with-caveats now, derive
      2.a later (per decision).
- [ ] When done, hand back to PM (paper state, push confirmation, whether 2.a
      needs a board issue).
