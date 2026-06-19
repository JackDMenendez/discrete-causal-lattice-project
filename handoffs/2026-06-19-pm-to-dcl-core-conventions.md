---
handoff: 2026-06-19-pm-to-dcl-core-conventions
from: PM
to: dcl-core (focused)
repo: dcl-core
branch: feat/v0.3.0-peierls-phase1
commits: [755ef75]
pr: none
status: consumed
state: complete
semver: n/a (docs only)
flags: [d4-leaning-text-still-says-forward-midpoint]
decisions: []
consumed_by: PM (executed on focused's behalf)
consumed_at: 2026-06-19
---

## Summary
A **reverse** handoff (PM → focused): the two follow-ups that came out of
consuming `2026-06-19-v0.3.0-phase1`. Both were edits the PM could make
directly, so this is filed already-**consumed** — a provenance record of
changes made in the dcl-core tree on the focused session's behalf, not a
to-do. One residual item is flagged below for the focused session.

## Shipped
- `755ef75` (branch `feat/v0.3.0-peierls-phase1`) — 2 files:
  - `CLAUDE.md` (Conventions): added the **/handoff** cross-session pointer.
  - `notes/gauge_field_v030_plan.md` §3.5: recorded the manifest `A_mid`
    **direction** — `"backward / gather-side: ½(A(x)+A(x−v))"` — plus a bullet
    tying a Q-tensor (#4) sign-flip back to the convention.

## Verification
Docs only; no code/test change. Staged selectively — the focused session's
`docs/design/05_interaction_engine.md` (modified) and untracked WIP
(`TOOLCHAIN.md`, `session-field.drawio`, …) were left untouched.

## Remaining
Nothing blocking. One design-doc cleanup flagged below is the focused
session's call (design authority), deliberately not done by the PM.

## Decisions & flags
- **`d4-leaning-text-still-says-forward-midpoint` (FLAG).** Plan note §1 **D4**
  still reads *"Leaning: A_mid = ½(A(x)+A(x+v))"*, but Phase 1 shipped the
  **backward** `½(A(x)+A(x−v))`. The manifest §3.5 now records the backward
  direction, so the two sections disagree. Resolve D4 (and the `05`
  decisions ledger) to "backward / gather-side, resolved by Phase 1" —
  PM left this to the focused session as a design-record edit, not a
  mechanical one.

## → Consumer actions
- [x] Add the `/handoff` pointer to dcl-core `CLAUDE.md` — done (`755ef75`).
- [x] Record `A_mid` backward direction in manifest §3.5 — done (`755ef75`).
- [x] Heads-up (no action): both rode commit `755ef75` on
      `feat/v0.3.0-peierls-phase1`, so they appear in the Phase 1 PR. If you'd
      rather keep the workflow pointer off that PR, cherry-pick to `main` and
      drop from the branch.
- [ ] (focused session) Resolve **D4** text to backward-midpoint — see flag.
