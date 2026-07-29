---
handoff: 2026-07-29-wcde-dev-soak-confirmed-commit-and-rollout
from: PM (dcl-website session)
to: wcde (focused)
repo: win-cross-dev-env
branch: main
commits: []
pr: none
status: open
state: ready                        # gate lifted — user confirmed the DEV soak; wcde is cleared to commit + roll to PROD
semver: TBD by wcde at the soak-closing commit (>= the sagemath v0.2.1 patch already on main)
flags:
  - "GATE LIFTED: the user confirmed the VS Code isolation DEV soak went well (PM session, 2026-07-29). The `wcde-dev-soak-before-release` hold is RELEASED. wcde is cleared to make the soak-closing commit and roll the isolation feature to PROD (c:\\prod\\wcde). This supersedes the 'do NOT commit / do NOT roll to PROD' gate carried by the four inbound handoffs below."
  - "ONE COMMIT, MANY DRIFTED PIECES: the isolation feature accreted across three handoffs (2026-07-05 base, 2026-07-06 python flavor, 2026-07-08 sync/update hardening + exp-tex flavor). The whole isolation feature is still UNTRACKED/uncommitted in j:\\dev\\wcde. Fold every piece into the same soak-closing commit so nothing is orphaned — the enumerated list is below."
  - "sagemath-path-leak (eaef5cd, patch v0.2.1) is ALREADY committed+pushed on main and is separate from the isolation feature — but its 'include in next release' + 'audit vscode-cmd.cmd' actions belong to this same release cut."
decisions:
  - "PM lifts the soak gate on the user's sign-off; PM does NOT commit the wcde tree (win-cross-dev-env is outside the dcl-website/PM direct-edit scope — reached via handoff). wcde owns the commit, the semver bump, and the PROD rollout."
consumed_by:
consumed_at:
---

## Summary

The user confirmed the VS Code per-flavor isolation **DEV soak passed**. This
handoff **releases the `wcde-dev-soak-before-release` gate** and authorizes the
wcde focused session to (a) make the single soak-closing commit that folds in
every accumulated isolation change, (b) decide the semver bump, and (c) roll the
isolation feature to PROD (`c:\prod\wcde`). It consolidates the consumer actions
from the four inbound handoffs (which PM has consumed) so wcde has one worklist.

## Consumed inbound handoffs (all `to: PM`, now `consumed`)

- `2026-07-05-wcde-vscode-isolation` — base isolation feature (per-flavor
  `--user-data-dir` + `--extensions-dir`, `vscode-isolation.cmd`,
  `seed-profile.cmd`, `lib/vsprofiles/`, all 11 launchers modified).
- `2026-07-06-wcde-python-profile-soak-findings` — new `python` flavor drift +
  the venv-provisioning gap; positive soak evidence (real isolated GUI launch).
- `2026-07-08-wcde-isolation-sync-update-hardening` — `--sync off`,
  `:seed_user_settings`, `setup-vscode.cmd` typo fix, `exp-tex` flavor,
  `requires`-audit trims, `user-settings.json` seed template.
- `2026-07-08-wcde-sagemath-path-leak` — already committed (eaef5cd, v0.2.1);
  release + `vscode-cmd.cmd` audit still owed.

## → Consumer actions (wcde owns all of these)

### A. The soak-closing commit — fold ALL of these into ONE commit
- [ ] Base isolation feature (2026-07-05): `vscode-isolation.cmd`,
      `seed-profile.cmd`, `lib/vsprofiles/` (common.txt + per-profile manifests +
      README), all 11 modified `vscode-*.cmd` launchers.
- [ ] `python` flavor (2026-07-06): `vscode-python.cmd` + `env/python-env.cmd`
      (undocumented drift past the 2026-07-05 enumeration — include it).
- [ ] Sync/update hardening (2026-07-08): `--sync off` at the args-assembly line,
      `:seed_user_settings` seeding, `setup-vscode.cmd` `settings.json,`
      redirect-typo fix.
- [ ] `exp-tex` flavor (2026-07-08): `vscode-exp-tex.cmd` profile relabel
      (python→exp-tex), `laytex-env.cmd` header fix, new `exp-tex.txt` +
      `python.txt` manifests, README rows.
- [ ] `requires`-audit trims + stale-header fixes: vscode-haskell, vscode-mingw64,
      vscode-cmd (now identical to vscode-ps).
- [ ] `user-settings.json` seed template + its copy-based seeding.

### B. Pre-commit verification (from 2026-07-05, still owed)
- [ ] Seed the real `ps` set: run `seed-profile.cmd ps` from a VS Code shell
      (ps.txt is a placeholder starter list, not the ~151-ext set).
- [ ] Verify manifest extension ids against `code --list-extensions`
      (esp. `anthropic.claude-code`) — a wrong id fails that install silently.

### C. Decisions to settle at commit review
- [ ] `python`-profile venv policy (2026-07-06 flag 2): should the profile
      guarantee its dev deps (scipy/pytest/editable dcl_core) via a seed/repo-setup
      step, or keep assuming a provisioned `.venv-win`?
- [ ] Retire `env/texlive-env.cmd`? No launcher references it (MiKTeX standardized).
- [ ] `laytex` vs `latex` spelling for `laytex-env.cmd` + its requires-token.
- [ ] seed-if-absent backfill path? + align `extensions.autoUpdate` value type
      (`false` boolean vs global `"off"` string).

### D. sagemath-path-leak (eaef5cd) — same release cut
- [ ] Audit `vscode-cmd.cmd` line ~4 for the same stray `sagemath` requires
      (vscode-cmd shares the `ps` profile; it should match vscode-ps).
- [ ] Include eaef5cd in the release.

### E. Release + rollout
- [ ] Decide the semver bump for the isolation feature (>= v0.2.1 already on main).
- [ ] Roll the isolation feature to PROD (`c:\prod\wcde`). When seeding PROD,
      consider seeding it from the same `user-settings.json` template so the Vim
      keybindings collapse to ONE source instead of the current DEV/global two.
- [ ] Write the follow-up handoff that SUPERSEDES
      `2026-07-03-vscode-ps-canonical-invocation` (the current source-of-truth the
      global CLAUDE.md cites), reflecting isolation now in PROD.

### F. wcde-memory notes (j--dev-wcde) captured by the inbound handoffs
- [ ] `.venv-win` now carries scipy 1.18.0 + pytest 9.1.1 + editable dcl_core.
- [ ] Stuck-VS-Code-updater remedy: a staged update holds the Inno Setup
      `vscode-updating` mutex and blocks every launcher; kill `CodeSetup*` (never
      `Code.exe`) to release it. Isolated `--user-data-dir`s do NOT inherit global
      settings, so `update.mode`/`--sync off` must be enforced per-profile.
