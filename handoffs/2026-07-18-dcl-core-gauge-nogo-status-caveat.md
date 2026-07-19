---
handoff: 2026-07-18-dcl-core-gauge-nogo-status-caveat
from: PM (dcl-website session)
to: dcl-core (focused)
repo: JackDMenendez/dcl-core
branch: main
commits: []                         # status/caveat request; no code handed off
pr: none
status: open
state: in-progress
semver: n/a (PM relay; the core version-bump decision is the dcl-core session's)
flags:
  - "PAPER IV v1.0 NO-GO TOUCHES THE CORE. v0.3.0's Peierls gauge channel + the induced electric/magnetic blocks (eps={1,4,4}, Q_B=adj(eps)) IMPLEMENT the single fixed three-diagonal (trigonal) A=1 construction that Paper IV v1.0 (concept DOI 10.5281/zenodo.21435951) shows is EXCLUDED AS CONSTRUCTED: the induced-photon common-mode speed anisotropy v^2=k^T eps k is O(1) / DIMENSION-4 (factor-~2 anisotropic speed of light) -> excluded by cavity / Michelson-Morley isotropy bounds. The matter sector is ALSO excluded as constructed (referee M1/M2). Root: omission of the 4th cube diagonal V_4=(1,1,-1) (the 4-diagonal set = 4*I is isotropic)."
  - "THE CODE IS NOT WRONG; THE OBJECT IS NOT THE PHYSICAL VACUUM. The engine correctly computes the three-diagonal construction — but that construction is now known NOT to be a phenomenologically viable physical vacuum EM. The ask is an HONEST STATUS CAVEAT so downstream work does not mistake the current gauge sector for validated physical electromagnetism. Do NOT read this as 'core is broken': A=1 conservation, the calibration-boundary architecture, and the engine are unaffected."
  - "ESCAPE IS OPEN FOUNDATIONAL RESEARCH (do not build now). The candidate fix is an O_h-restoring FOUR-ORIENTATION vacuum / four-axis (V_4-inclusive or polygonal) hop topology that would isotropize the induced gauge loop while matter keeps its axis (decoupling). Whether it preserves A=1 + Dirac is a Paper-I-level open question — possibly its own foundational paper. A future core feature (multi-orientation vacuum), not this update."
decisions:
  - "PM relays the need (author: 'need to update the core library as well'). The exact scope — doc/CLAUDE.md/release-note caveat vs a runtime note/guard vs a version bump — is the dcl-core session's + author's call."
consumed_by:
consumed_at:
---

## Summary
Paper IV v1.0's single-domain no-go (concept DOI 10.5281/zenodo.21435951) applies
to dcl-core: the v0.3.0 gauge sector is the very three-diagonal construction shown
to give an excluded O(1)/dim-4 photon-speed anisotropy. The engine is correct; the
construction is not the physical vacuum. dcl-core should carry an honest status
caveat so nobody mistakes the current gauge implementation for validated physical
EM, cite Paper IV, and note the open O_h-restoring escape. Scope, wording, and any
version bump are the dcl-core session's call.

## → Consumer actions (dcl-core session)
- [ ] Add an **honest status caveat** to the gauge-sector surface (module docstring
      / docs / CLAUDE.md / release notes, your call): the single fixed three-diagonal
      construction's induced photon is **excluded as constructed** (O(1)/dim-4
      common-mode anisotropy) per Paper IV v1.0; the matter sector likewise; cite the
      **concept DOI 10.5281/zenodo.21435951**. State the escape (O_h-restoring
      four-orientation vacuum) as open future work.
- [ ] Decide whether this warrants a **runtime note/guard** (e.g., a docstring/
      comment where the induced blocks are built) and/or a **version bump** — or is
      documentation-only. PM defers to you.
- [ ] Keep scope honest: A=1 conservation is NOT falsified; the calibration boundary
      + engine are unaffected; only the single-domain gauge construction's
      phenomenological viability is qualified.
- [ ] If/when the four-orientation-vacuum escape becomes a core feature, that is a
      new MINOR (and ties to the foundational-paper thread) — flag to PM for the
      roadmap; do not build it under this caveat update.
- [ ] Hand back to PM with what changed (and any new version) so the dcl-website
      news/calibration pages stay consistent.
