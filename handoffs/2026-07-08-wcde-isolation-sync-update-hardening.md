---
handoff: 2026-07-08-wcde-isolation-sync-update-hardening
from: wcde (focused) — live DEV-soak session (triggered from a dcl-delta-p-min window)
to: PM
repo: win-cross-dev-env
branch: main
commits: []                         # uncommitted; wcde tree still gated (see 2026-07-06 handoff)
pr: none
status: open
state: blocked                      # gated on user DEV-soak sign-off (memory wcde-dev-soak-before-release)
semver: n/a (wcde; bump decided at the soak-closing commit, per 2026-07-05 handoff)
flags:
  - "UNCOMMITTED WIP on top of untracked feature: all three source changes live in the working tree only. `shells/windows/tools/vscode-isolation.cmd` is still `??` (untracked — the whole isolation feature is uncommitted), and `shells/windows/tools/setup-vscode.cmd` is `M`. Nothing here is committed or released; it must ride the same soak-closing commit that folds in the `python` flavor (2026-07-06 handoff)."
  - "DEV-ONLY until isolation promotes: `--sync off` and the update-suppression seeding ONLY affect isolated (DEV) launches. PROD (`c:\\prod\\wcde`) launchers have no `--extensions-dir`/isolation, so PROD sessions still use the global `%USERPROFILE%\\.vscode\\extensions` (153 exts) and the global user settings (which already carry `update.mode: manual`). The user's observed 'DEV ~14 exts vs PROD 100+' is this gap BY DESIGN, not a bug; it closes when isolation rolls to PROD."
  - "SEED-IF-ABSENT is not a backfill: `:seed_user_settings` writes the update keys ONLY when an isolated data dir has no `User\\settings.json`. Existing isolated data dirs self-heal on next launch (none currently have a settings.json). But a data dir that later grows a settings.json WITHOUT the update keys will NOT be backfilled. Chosen to avoid clobbering UI-accumulated settings; confirm acceptable at commit review."
  - "VALUE-TYPE drift vs global settings: the seed writes `\"extensions.autoUpdate\": false` (boolean) whereas the user's global `%APPDATA%\\Code\\User\\settings.json` uses `\"off\"` (string). Both disable extension auto-update, but a careful diff will show the mismatch — reconcile to one form at commit if desired."
  - "NEW `exp-tex` FLAVOR (further drift past 2026-07-06): the tree gained a `vscode-exp-tex.cmd` launcher + `laytex-env.cmd` env (MiKTeX-on-PATH) for an experimental python+LaTeX flavor. As found, `vscode-exp-tex.cmd` set `WCDE_VSCODE_PROFILE=python` — COLLIDING with vscode-python's isolation dir and provisioning ZERO tex extensions. Fixed this session: relabelled to `exp-tex`, added `exp-tex.txt` (ms-python.python, ms-toolsai.jupyter, james-yu.latex-workshop) + `python.txt` (the pure-python flavor had NO manifest, rode only common.txt), fixed `laytex-env.cmd`'s copy-paste header/echo (said `miktex`), and added both rows to the vsprofiles README. NOTE: the file/token is spelled `laytex` (not `latex`) — left as-is pending the user's call; renaming would touch the requires line + filename."
decisions:
  - "Placed `--sync off` at the single args-assembly line in vscode-isolation.cmd (one edit covers every launcher: ps/web/ucrt64/mingw64/haskell/agda/sage/tex/python) rather than editing each vscode-*.cmd."
  - "Root-caused the stuck-updater ambush to isolated `--user-data-dir`s NOT inheriting global settings (so they defaulted to `update.mode: default` and auto-downloaded). Fixed at source by seeding the data dir, not just by killing the process."
  - "Seed-if-absent (never merge/clobber) over a JSON-merge into the data-dir settings."
consumed_by:
consumed_at:
---

## Summary
A wcde DEV-soak session hardened the VS Code isolation feature against two
real failures observed live: (1) VS Code **Settings Sync** had been enabled in
an isolated instance and pulled 152 extensions into the shared `ps` profile ext
dir; (2) a staged VS Code update held the Inno Setup `vscode-updating` mutex and
**blocked every launcher** ("Code is currently being updated"). Both are now
fixed at the wcde source. All changes are uncommitted and remain gated on the
DEV-soak sign-off, exactly like the 2026-07-06 soak-findings handoff this
follows.

## Shipped (working tree only — no commits)
- `shells/windows/tools/vscode-isolation.cmd` (untracked): added `--sync off`
  to `WCDE_VSCODE_DEV_SHELL_ARGS` so Settings Sync is forced OFF on every
  isolated launch (a stray sign-in can no longer refill a profile's ext dir);
  added `:seed_user_settings` which seeds a fresh isolated `--user-data-dir`'s
  `User\settings.json` with `update.mode: manual`,
  `update.enableWindowsBackgroundUpdates: false`, `extensions.autoUpdate: false`
  (seed-if-absent), closing the auto-update-in-isolation gap.
- `shells/windows/tools/setup-vscode.cmd` (`M`): fixed a redirect typo where the
  autosave block wrote to a file literally named `settings.json,` (trailing
  comma) instead of `settings.json`, producing malformed JSON + a junk file.
- `shells/windows/cmd/vscode-exp-tex.cmd` (untracked): relabelled
  `WCDE_VSCODE_PROFILE` from `python` → `exp-tex` (was colliding with the
  vscode-python flavor's isolation dir and provisioning no TeX extensions).
- `shells/windows/lib/vsprofiles/exp-tex.txt` (new) + `python.txt` (new): manifests
  for the two python-family flavors (exp-tex = python + jupyter + latex-workshop;
  python = python + jupyter). vscode-python previously had no manifest.
- `shells/windows/cmd/env/laytex-env.cmd` (untracked): fixed copy-paste header +
  echo that still said `miktex-env` / `------------ miktex`.
- `shells/windows/lib/vsprofiles/README.md`: added `python` and `exp-tex` rows to
  the profile→launcher table.
- Launcher `requires`-audit trims (on top of the user's own launcher audit):
  `vscode-haskell.cmd` → `global win git-cli haskell vscode` (dropped
  miktex+sagemath; also fixed a stale `vscode-ps` copy-paste header);
  `vscode-mingw64.cmd` → `global win-dev mingw64 vscode` (dropped texlive+sagemath;
  header updated); `vscode-cmd.cmd` → realigned to `global win git-cli miktex
  sagemath vscode msys2-tools`, now IDENTICAL to vscode-ps (they share the `ps`
  profile) and matching CLAUDE.md. Net: no launcher loads `texlive` anymore
  (standardized on MiKTeX); `texlive-env.cmd` is now unreferenced.

## Verification
- `--sync off` confirmed present in the live launch command line.
- Seeding dry-run tested both paths: fresh data dir → valid JSON with the three
  keys; pre-existing settings.json → skipped (not clobbered).
- `setup-vscode.cmd` re-run against a scratch target → well-formed JSON, no junk
  `settings.json,` file.
- Runtime cleanups performed this session (one-off, no code follow-up): reset the
  bloated `ps` ext dir (`%USERPROFILE%\.vsisolation\ps\ext`, 152 exts + stale
  marker → re-provisions to the 5-ext default on next launch); killed the two
  stuck `CodeSetup*` processes to release the `vscode-updating` mutex; removed
  junk `settings.json,` files from `dcl-core` and `wcde`.

## Root causes (the load-bearing part)
- **Sync bloat:** extensions live per-profile at `%USERPROFILE%\.vsisolation\
  <profile>\ext` (shared across repos), NOT in a repo's `.vsisolation`. Deleting
  a repo's `.vsisolation` never touches them, and Settings Sync refills them on
  sign-in. `--sync off` is the deterministic guard; settings.json has no full
  kill switch (`update.mode`/`settingsSync.*` are only partial).
- **Update ambush:** the global user settings already had `update.mode: manual`,
  but isolated `--user-data-dir`s start empty and do NOT inherit it, so those
  instances defaulted to auto-download → staged an update → held the Inno Setup
  mutex → refused all launches. Seeding the data dir fixes it at the source.

## Remaining / gating
- wcde release stays BLOCKED on the user's "DEV soak went well" sign-off
  (memory `wcde-dev-soak-before-release`); do NOT commit the wcde tree or roll to
  PROD (`c:\prod\wcde`) before that — same gate as 2026-07-06.

## → Consumer actions
- [ ] Fold ALL of these into the SAME soak-closing wcde commit that folds in the
      `python` flavor (per 2026-07-06 handoff): (a) `--sync off` in
      vscode-isolation.cmd, (b) `:seed_user_settings` seeding in
      vscode-isolation.cmd, (c) the `settings.json,` redirect-typo fix in
      setup-vscode.cmd, (d) the `exp-tex` flavor: `vscode-exp-tex.cmd` profile
      relabel + `laytex-env.cmd` header fix + new `exp-tex.txt`/`python.txt`
      manifests + README rows, (e) the launcher `requires`-audit trims
      (vscode-haskell, vscode-mingw64, vscode-cmd) + stale-header fixes.
- [ ] Decide whether to RETIRE `shells/windows/cmd/env/texlive-env.cmd` now that
      no launcher references it (MiKTeX is the standardized TeX distro), or keep it
      as an available-but-unused loader.
- [ ] Decide the `laytex` vs `latex` spelling for `laytex-env.cmd` / the `laytex`
      requires-token; if renaming, update `vscode-exp-tex.cmd`'s requires line and
      the filename together.
- [ ] Memory (j--dev-wcde): record the stuck-VS-Code-updater remedy — a staged
      update holds the Inno Setup `vscode-updating` mutex and blocks every wcde
      launcher; kill the `CodeSetup*` processes to release it, NEVER `Code.exe`
      (it hosts the live session). Also record that isolated `--user-data-dir`s
      do NOT inherit global VS Code settings, so `update.mode` (and `--sync off`)
      must be enforced per-profile — which is why these guards live in
      vscode-isolation.cmd.
- [ ] At commit review, decide on the two minor items in flags 3–4: whether
      seed-if-absent needs a backfill path, and whether to align
      `extensions.autoUpdate` value type (`false` vs `"off"`) with the global
      settings.
- [ ] When soak passes: proceed with the 2026-07-05 handoff's own consumer
      actions (seed ps.txt, verify extension ids, commit, semver, PROD rollout) —
      these sync/update guards are part of that same cut.
