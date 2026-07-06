---
handoff: 2026-07-05-wcde-vscode-isolation
from: wcde (focused)
to: PM
repo: win-cross-dev-env
branch: main
commits: []                         # NONE — all work is uncommitted working-tree
pr: none
status: open
state: in-progress
semver: unreleased (uncommitted working-tree; no bump until DEV soak → commit)
flags:
  - "PROD wcde (c:\\prod\\wcde) does NOT have these changes — launching a vscode-*.cmd from the PROD shell runs the OLD un-isolated behavior. This already caused a false 'isolation broken' report. Test ONLY from the DEV copy j:\\dev\\wcde."
  - "First-run provisioning + real GUI launch are UNVERIFIED. Only the isolation helper's path/gitignore logic was tested headlessly (dry-run). `code --install-extension` loops and true parallel-instance isolation have not been run."
  - "Extension ids in the manifests are UNVERIFIED — especially anthropic.claude-code. A wrong id fails that one install silently. Confirm against `code --list-extensions`."
  - "ps.txt is a placeholder starter list, NOT your real ~151-extension set. Run seed-profile.cmd ps before relying on the ps profile or it opens lean."
  - "vscode-haskell.cmd is a clone of vscode-ps.cmd and still carries the vscode-ps.cmd header comment (cosmetic mislabel), profile=haskell."
decisions:
  - "user-data-dir is repo-local (<repo>\\.vsisolation\\<profile>\\data, gitignored) when a target is given, else %USERPROFILE%; extensions-dir is ALWAYS %USERPROFILE%\\.vsisolation\\<profile>\\ext (shared per profile, ~47MB total, user-approved as acceptable)."
  - "Profile key = explicit WCDE_VSCODE_PROFILE per launcher; MSYSTEM-derived default for subsystem flavors, overridden for haskell/agda; vscode-cmd shares the ps profile."
  - "common.txt (installed into every profile) = vscodevim.vim, eamodio.gitlens, anthropic.claude-code, editorconfig.editorconfig."
consumed_by:
consumed_at:
---

## Summary
Fixes the VS Code single-instance PATH-collapse in win-cross-dev-env: opening a
second flavor (e.g. vscode-quarto) while a first (vscode-ps) was running just
handed the folder to the running instance, so the new window inherited the wrong
ambient PATH and the full extension set. Each `vscode-*.cmd` now launches an
**isolated** instance with its own `--user-data-dir` + `--extensions-dir`, keyed
by a per-flavor `WCDE_VSCODE_PROFILE` label. This also puts each flavor's toolset
on PATH for the dedicated Claude Code in that window, which retired the old
"call quarto/gh by full path" workaround.

## Shipped
All UNCOMMITTED in j:\dev\wcde working tree (nothing staged/committed):
- NEW `shells/windows/tools/vscode-isolation.cmd` — resolves per-profile dirs,
  appends `.vsisolation/` to the repo `.gitignore`, provisions extensions once
  (marker-guarded), sets `WCDE_VSCODE_DEV_SHELL_ARGS`. Has a `WCDE_VSISO_DRYRUN=1`
  test mode.
- NEW `shells/windows/tools/seed-profile.cmd` — snapshots the current default
  VS Code extension set into a profile manifest (bootstrap `ps`).
- NEW `shells/windows/lib/vsprofiles/` — common.txt + per-profile manifests
  (ps, web, ucrt64, mingw64, haskell, agda, sage, tex) + README.md.
- MODIFIED all 11 vscode-*.cmd launchers (agda, cmd, ghcup, haskell, miktex,
  mingw64, ps, quarto, sagemath, ucrt64) to set a profile + call the helper.
  (vscode-quarto.cmd also had win-dev + R dropped from its requires — user edit.)
- Docs: global `C:\Users\jackd\.claude\CLAUDE.md` reconciled (check
  $env:WCDE_VSCODE_PROFILE, call tools by name, notify user on a PATH gap so it's
  fixed in wcde); memory `no-hardcoded-full-paths.md` added (project j--dev-wcde).

## Verification
- Helper logic: PASS headlessly (dry-run) — repo-local vs user-profile data
  resolution, correct arg quoting, idempotent `.gitignore` append.
- First-run extension install + GUI launch + real parallel isolation: NOT RUN.
- semver: no bump; changes uncommitted. Decide bump at commit time.

## Remaining
- User is actively soaking (DEV only). Blocked on user's "soak went well" before
  any commit or PROD rollout (ties to memory `wcde-dev-soak-before-release`).
- Seed ps.txt from the real extension set.
- Verify manifest extension ids.
- Optional: fix vscode-haskell.cmd header comment; decide whether ghcup should
  keep sharing the haskell profile.

## Decisions & flags
See frontmatter. Load-bearing: the PROD-vs-DEV flag is the one most likely to
cause a false failure report — the isolation code lives only in j:\dev\wcde and
PROD (c:\prod\wcde) is unchanged, so a PROD-shell launch behaves the old way.
The ps.txt and extension-id flags are what would make a first real launch look
"wrong" (lean when expected full, or a silent skipped install).

## → Consumer actions
- [ ] Gate: do NOT commit the wcde working tree or roll to PROD until the user
      confirms the DEV soak went well (memory `wcde-dev-soak-before-release`).
- [ ] Relay to any session testing this: launch flavors ONLY from
      j:\dev\wcde\shells\windows\cmd\vscode-*.cmd, never the PROD shell.
- [ ] Before trusting the `ps` profile: run
      `j:\dev\wcde\shells\windows\tools\seed-profile.cmd ps` from a VS Code shell.
- [ ] Verify manifest ids (esp. `anthropic.claude-code`) against
      `code --list-extensions`; fix any that fail to install.
- [ ] Memory: note in the consuming session that the "call tools by full path"
      guidance is retired for launcher-isolated sessions (already in
      `no-hardcoded-full-paths.md`, j--dev-wcde memory).
- [ ] When soak passes and commit happens: decide the wcde semver bump and
      whether to write a follow-up handoff superseding the 2026-07-03
      vscode-ps-canonical-invocation source-of-truth.
