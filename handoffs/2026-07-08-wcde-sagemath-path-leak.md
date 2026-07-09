---
handoff: 2026-07-08-wcde-sagemath-path-leak
from: wcde (focused) — bug fix
to: PM
repo: win-cross-dev-env
branch: main
commits: ["eaef5cd"]
pr: none
status: open
state: ready
semver: patch (v0.2.1)
flags:
  - "SageMath was unintentionally leaking into the ps profile toolchain via an explicit `requires sagemath` line in vscode-ps.cmd. This was not intended for the default PowerShell profile — SageMath should only appear in the dedicated `vscode-sagemath.cmd` launcher."
  - "vscode-cmd.cmd (line 4) contains the same `sagemath` requirement and may need audit/removal depending on design intent for the generic cmd profile."
decisions:
  - "Removed `sagemath` from the `requires` call in vscode-ps.cmd, line 10. The ps profile now loads: global, win, git-cli, miktex, vscode, msys2-tools."
  - "Single-line edit; committed and pushed."
consumed_by:
consumed_at:
---

## Summary
Fixed an unintended SageMath PATH leak in the ps (PowerShell) profile.
vscode-ps.cmd was explicitly requiring SageMath as part of its baseline
environment, polluting the toolchain when it should only be available via
the dedicated `vscode-sagemath.cmd` launcher. Removed the requirement;
available in the next release.

## Shipped
- Commit `eaef5cd`: Remove SageMath from ps profile PATH
  - [vscode-ps.cmd](shells/windows/cmd/vscode-ps.cmd): Removed `sagemath` from line 10's `requires` call.
  - Now: `global win git-cli miktex vscode msys2-tools`
  - Before: `global win git-cli miktex sagemath vscode msys2-tools`

## Consumer actions
- [ ] Review the single-line diff in commit eaef5cd.
- [ ] Audit `vscode-cmd.cmd` (line 4) for the same issue if design intent is unclear.
- [ ] Include this commit in the next release (v0.2.1 or later).
