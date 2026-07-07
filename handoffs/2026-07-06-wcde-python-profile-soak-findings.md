---
handoff: 2026-07-06-wcde-python-profile-soak-findings
from: dcl-core (focused) — ran as a live DEV-soak session
to: PM
repo: win-cross-dev-env
branch: main
commits: []                         # findings only; wcde tree still uncommitted (gated)
pr: none
status: open
state: blocked                      # gated on user DEV-soak sign-off (memory wcde-dev-soak-before-release)
semver: n/a (wcde findings; the wcde bump is decided at its commit, per 2026-07-05 handoff)
flags:
  - "DRIFT past the 2026-07-05 handoff: the wcde working tree has a NEW, uncommitted `python` flavor — `shells/windows/cmd/vscode-python.cmd` + `shells/windows/cmd/env/python-env.cmd` — NOT listed in 2026-07-05-wcde-vscode-isolation (which enumerated ps/web/ucrt64/mingw64/haskell/agda/sage/tex). Whatever commit/handoff closes the soak MUST cover the `python` profile too."
  - "PROVISIONING GAP surfaced by this soak: the `python` profile ACTIVATES `.venv-win` (python-env.cmd -> lib/python-activate.cmd) but INSTALLS NOTHING. The canonical `.venv-win` was missing scipy (a declared dcl_core dependency), pytest, and any editable dcl_core install — so a launcher-opened Python session cannot run the dcl_core suite out of the box. Root-cause decision for wcde: should the `python` profile guarantee its dev deps (a seed/repo-setup step) rather than assume a fully-provisioned venv?"
  - "SHARED VENV MUTATED: to verify dcl-core work this session ran `pip install -e . pytest` into C:\\Users\\jackd\\.venv-win, adding scipy 1.18.0, pytest 9.1.1, and an editable dcl_core 0.2.2. The canonical venv now differs from its prior state — intended, but recorded here because .venv-win is shared across all DCL repos."
  - "CuPy present but CUDA path not detected in this session (`UserWarning: CUDA path could not be detected`) — non-fatal for CPU work; flagged only so it is not mistaken for a regression."
decisions:
  - "None taken by this session on the wcde side — the wcde release stays gated on the user's DEV-soak sign-off. These are findings to fold into that decision."
consumed_by:
consumed_at:
---

## Summary
A dcl-core focused session ran inside the wcde VS Code isolation DEV soak
(`WCDE_VSCODE_PROFILE=python`, isolated `--user-data-dir` +
`--extensions-dir`). It provides positive soak evidence AND surfaces two gaps
not captured by the 2026-07-05 isolation handoff: a new uncommitted `python`
flavor, and that the `python` profile assumes a fully-provisioned `.venv-win`
which was in fact missing scipy/pytest/editable-dcl_core.

## Soak evidence (positive — retires a 2026-07-05 "UNVERIFIED" flag)
The 2026-07-05 handoff flagged "first-run provisioning + real GUI launch are
UNVERIFIED." This session is a live counter-example:
- Launched as an **isolated** instance: `--user-data-dir
  J:\dev\dcl-core\.vsisolation\python\data`, `--extensions-dir
  C:\Users\jackd\.vsisolation\python\ext` (per `WCDE_VSCODE_DEV_SHELL_ARGS`).
- The helper **provisioned** `J:\dev\dcl-core\.vsisolation\{ps,python}\` and
  **appended** `.vsisolation/` to dcl-core's `.gitignore` (idempotent append
  worked). dcl-core committed that ignore line (`b1a7d35`).
So: isolated launch + per-profile data-dir + gitignore append all work in a
real GUI session. Extension-id correctness and the real ps.txt seed remain
unverified (still open per 2026-07-05).

## The two gaps (see flags 1–2)
1. New `python` flavor exists in the tree but is undocumented in the soak
   handoff — drift to reconcile at commit time.
2. `python` profile activates but does not provision `.venv-win`; the venv was
   under-provisioned (no scipy/pytest/editable dcl_core). This is the wcde
   equivalent of "a tool missing from PATH in a launcher session is a wcde gap."

## Remaining / gating
- wcde release stays BLOCKED on the user's "DEV soak went well" sign-off
  (memory `wcde-dev-soak-before-release`); do NOT commit the wcde tree or roll
  to PROD (`c:\prod\wcde`) before that.
- Decide the `python`-profile venv-provisioning policy (flag 2).

## → Consumer actions
- [ ] Fold the `python` flavor into the wcde commit + the follow-up handoff that
      supersedes `2026-07-03-vscode-ps-canonical-invocation` (it is currently
      undocumented — flag 1).
- [ ] Decide whether the `python` profile should guarantee its venv dev deps
      (scipy/pytest/editable dcl_core) via a seed/repo-setup step instead of
      assuming a provisioned `.venv-win` (flag 2). Update the profile manifest /
      `python-env.cmd` accordingly.
- [ ] Memory (j--dev-wcde): note that `.venv-win` now carries scipy 1.18.0 +
      pytest 9.1.1 + editable dcl_core (flag 3), and that the `python` profile
      exists and was DEV-soaked in a real GUI session on 2026-07-06.
- [ ] When soak passes: proceed with the 2026-07-05 handoff's own consumer
      actions (seed ps.txt, verify extension ids, commit, semver, PROD rollout).
