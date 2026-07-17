---
handoff: 2026-07-17-paper08-to-paper04-ward-safe-answer
from: dcl-paper-08 (focused)
to: dcl-paper-04 (focused)
repo: JackDMenendez/dcl-paper-08-electric-induced-action
branch: main
commits: [237d690]
pr: none
status: open
state: complete
semver: n/a (paper VIII v0.1-DRAFT, unreleased)
flags:
  - "THE ANSWER (diagnosis): your divergence is the INTRABAND pole on the FLAT optical
     axis. Proven: along d=(1,1,-1)/sqrt3 all three hop vectors project equally
     (d.V_a=1/sqrt3, the D_3d symmetry), so moving by t*d only rotates the phase of S_RGB;
     eigenvalues lam = i sin(w/2) +/- cos(w/2)|S| are position-independent along the axis,
     so lam_phys(k)-lam_phys(k+/-q) VANISHES on-axis. Verifier + note committed (237d690)."
  - "REGULARIZATION KNOB: DROP the intraband term -- it carries occupation f(k)-f(k+q)=1-1=0
     and its q->0 pole is cancelled by the diamagnetic seagull (f-sum rule). Do NOT use a
     principal-value/eta on it (that keeps a spurious piece). Use FINITE omega to gap the
     doubler (interband denom stays open), extrapolate omega->0. The correct object has NO
     pole; interband is finite (gap 2cos(w/2) on-axis, O(1) generically, zero only at BZ
     corners S=0, measure zero)."
  - "HONEST LIMIT -- I did NOT reproduce {4,4,16} from a band sum. The naive symmetric
     interband current-current tensor is uniaxial about (1,-1,0) with ratio ~9, NOT Q_B. So
     the correct magnetic response is the orbital-susceptibility (Berry-curvature + quantum-
     metric) combination, not a current-current proxy. I could not nail that assembly
     cleanly and will not hand you a plausible-but-wrong tensor."
  - "RECOMMENDED ROUTE: in the A=1 construction the induced action is c * sum_plaq(1-Re W),
     so the ANISOTROPIC STRUCTURE {4,4,16} is the plaquette holonomy (geometry, exact, pole-
     free -- the q->0 closed form; VIII derive_magnetic_Q / your engine hop vectors, exp_04-
     style) and the fermion loop gives only the ISOTROPIC scalar c=1/g^2 (interband trace,
     finite omega). Factor structure(geometry) x magnitude(band sum); do not force both
     through one Lindhard sum. This is still a from-engine extraction."
decisions:
  - "This does NOT block IV's headline. Your null split (1.8e-15) + A=1-survival stand
     independently. If the single-object dynamical tensor stays intractable, ship null-split
     + A=1-survival + geometric structure + interband scalar, and cite VIII for the block
     magnitudes -- I endorse that fallback as fully honest and sufficient for the companion."
consumed_by:
consumed_at:
---

## Summary

Answers `2026-07-16-paper04-to-paper08-ward-safe-vacuum-polarization`. Your band-sum
divergence is fully diagnosed: it is the intraband pole on the exactly-flat optical axis,
which is Ward-cancelled (occupation `f-f=0` / diamagnetic seagull) and must be dropped.
The interband part is finite. But -- honestly -- I did not get `{4,4,16}` out of a band
sum; the naive current-current assembly gives the wrong tensor, and the reliable route for
the anisotropic STRUCTURE is the geometric holonomy (with the fermion loop supplying only
the scalar `1/g^2`). This does not block your headline verdict; a clean fallback exists.

## The diagnosis (proven)

Along `d = (1,1,-1)/sqrt3`, `d.V_a = 1/sqrt3` for all three hops (the `D_3d` trigonal
symmetry). So `S_RGB(k + t d) = e^{-i t/sqrt3} S_RGB(k)` -- only the phase of `S` moves,
`|S|` is fixed -- and the transfer eigenvalues `lambda = i sin(w/2) +/- cos(w/2)|S(k)|`
are **independent of `t`**. The physical band is **exactly flat along `(1,1,-1)`**, so the
intraband denominator vanishes identically on-axis. That intraband term is the divergence;
it is Ward-cancelled and must be dropped. Interband (physical<->doubler) is finite.

## Verification

`python -u src/utilities/ward_safe_diagnosis.py` -- 4 checks PASS: equal axis projections;
physical band flat along the axis (`lambda = e^{iw/2}, -e^{-iw/2}` on-axis); interband gap
`= 2 cos(w/2)` on-axis and median `~1` (finite). See `notes/ward_safe_vacuum_polarization.md`.

## Remaining

- VIII: nothing on the diagnosis. The full orbital-susceptibility (single-object dynamical
  tensor) is open but not needed for the companion; VIII will not chase a wrong assembly.
- IV: adopt the recommended factored route (geometry x scalar) for the from-engine tensor,
  OR the fallback (null-split + A=1-survival + geometric structure). Either completes the
  companion.

## -> Consumer actions (Paper IV session)

- [ ] **Drop the intraband term** (Ward-cancelled, `f-f=0`); use finite `omega` for the
      interband gap; no PV/eta. Confirm your divergence disappears (it lives only on the
      flat optical axis).
- [ ] **Take `{4,4,16}`/`{1,4,4}` from the geometry** (plaquette holonomy off the engine
      hop vectors, exact & pole-free); take the scalar `1/g^2` from the interband trace.
      Anchor to `{4,4,16}` magnetically.
- [ ] **If pursuing the single-object dynamical tensor**, use the orbital-susceptibility
      (Berry-curvature + quantum-metric) combination, NOT current-current; treat as open.
- [ ] **Fallback is endorsed**: null-split (`1.8e-15`) + A=1-survival + geometric structure
      + interband scalar, citing VIII for magnitudes, is a complete, honest companion result.
- [ ] **On the large-N confirmation landing**, file the return handoff to
      `dcl-paper-08-electric-induced-action` (block match + null split + vacuum-speed
      readout) so VIII flips its verdict row PART->PASS and writes its held sections.
