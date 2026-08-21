---
handoff: 2026-08-21-wcde-drawio-settings-pin-and-profile-gaps
from: dcl-mathematics (focused)
to: wcde (focused)
repo: JackDMenendez/win-cross-dev-env
branch: main
commits: []                         # no code handed off — this reports an environment gap for wcde to fix at source
pr: none
status: open
state: ready
semver: 0.3.1 -> 0.4.0 (MINOR, unreleased)   # PROPOSED — the wcde session owns the verdict; see Decisions
flags:
  - "DO NOT 'fix' the version skew by setting hediet.vscode-drawio.offline to false. That routes diagram content through https://embed.diagrams.net/ — a network egress and privacy change, not a rendering fix. The skew is acceptable; the mitigation is explicit colours in the files."
  - "NO lean.txt EXISTS in shells/windows/lib/vsprofiles/, yet WCDE_VSCODE_PROFILE=lean is live (verified in a running session on 2026-08-21) and the vscode-lean launcher is documented in the user's global CLAUDE.md. Either a manifest is missing or lean's extension set is defined somewhere else. UNVERIFIED which — do NOT create lean.txt until that is confirmed, or you may shadow a working mechanism."
  - "EXTENSION-ISOLATION CLAIM MAY BE STALE. The user's global CLAUDE.md states each launcher starts VS Code with its own --user-data-dir AND --extensions-dir. The only draw.io extension on this machine is in the SHARED %USERPROFILE%\\.vscode\\extensions (hediet.vscode-drawio-1.9.260701018); no per-profile extensions dir was found beyond .vscode-shared. Either isolation is not in force for `lean`, or the documentation overstates it. Unverified — reconcile the doc with reality before relying on per-profile extension sets."
  - "PINNING drawio-inline-editor.theme IS A PREFERENCE, NOT A CORRECTION. The value below (light) is chosen for determinism, not because dark is wrong. If the author wants dark inline previews, pin dark — the requirement is that it be PINNED, not that it be light."
  - "extensions.autoUpdate is already false in user-settings.json (deliberate). That FREEZES the version skew described below until someone updates on purpose. This is a consequence of an existing correct policy, not a new bug, but it should be documented as known state so the skew is not rediscovered as a mystery every few months."
decisions:
  - "dcl-mathematics has already mitigated its own exposure independently (all colours made explicit in figures/Cubic-Space.drawio, verified pixel-identical). wcde is NOT blocking dcl-mathematics. This handoff is about making the environment deterministic for every repo, not about unblocking one."
  - "semver MINOR is proposed on the grounds that pinned settings add coverage without breaking existing provisioning. If the wcde session reads pinned editor settings as a fix to drift, PATCH is defensible. Routed, not adjudicated."
consumed_by:
consumed_at:
---

## Summary

Colour rendering of the same `.drawio` file differs between the VS Code
draw.io extension and the Windows draw.io desktop app. Investigated from
`dcl-mathematics` on 2026-08-21. The root cause is not a bug in either tool:
**most colours were never stored in the file**, so each build supplied its own
defaults — and the two builds are a major version apart. Along the way, three
wcde-level gaps surfaced: draw.io editor settings are not pinned in
`user-settings.json`, `hediet.vscode-drawio` is absent from `common.txt` and
`ps.txt`, and no `lean.txt` manifest exists despite `lean` being a live
profile. dcl-mathematics has fixed its own files; wcde should close the
environment gaps so the next repo does not rediscover this.

## Findings (all verified on 2026-08-21)

**Version skew, frozen by policy.**
- Desktop draw.io: **31.3.1** (`C:\Program Files\draw.io\draw.io.exe`).
- VS Code extension `hediet.vscode-drawio-1.9.260701018` bundles its **own**
  draw.io at **30.2.7** (`<ext>/drawio/VERSION`).
- `hediet.vscode-drawio.offline` defaults to `true`, so the extension **never**
  uses the desktop build. Two draw.io releases, one file.
- `extensions.autoUpdate: false` is already pinned in wcde's
  `user-settings.json`, so the skew is stable rather than drifting.

**A hypothesis that was tested and REJECTED — record it so it is not re-chased.**
`figures/Cubic-Space.drawio` carried `background="light-dark(#FFFFFF,#FFFFFF)"`,
and the obvious theory was that the older bundled build cannot parse the
`light-dark()` CSS function. **Both builds understand it** (verified by string
search in each build's `app.min.js` / `app.asar`). `light-dark()` is not the
cause. It was removed anyway, since both branches were white and it added a
syntax dependency for zero information.

**The actual cause.** In that one figure, 18 of 27 shapes had no `fillColor`,
72 elements had no `strokeColor`, and 257 had no `fontColor`. Those are not
"colours that failed to survive" — they were never written down, so each
build rendered them from its own palette.

**Settings not pinned.** `shells/windows/lib/vsprofiles/user-settings.json`
contains **no** `hediet.vscode-drawio.*` or `drawio-inline-editor.*` keys.
Extension defaults observed in this version:

| setting | default | matches desktop? |
| --- | --- | --- |
| `hediet.vscode-drawio.theme` | `kennedy` | yes |
| `hediet.vscode-drawio.appearance` | `light` | yes |
| `drawio-inline-editor.theme` | **`auto`** | **no — follows the VS Code colour theme** |

The first two happen to agree with the desktop today; they are unpinned and
can drift on any extension update. The third is the one that actively differs,
and it governs **inline diagram previews** rather than the full editor.

**Profile manifest gaps.**
- `hediet.vscode-drawio` appears **only** in `vsprofiles/drawio.txt`.
- It is **not** in `common.txt` (which carries vim, gitlens, claude-code,
  editorconfig) and **not** in `ps.txt` (which currently carries only
  `ms-vscode.cpptools` and is documented as awaiting a `seed-profile.cmd ps`).
- There is **no `lean.txt`** at all — see flag 2.
- So diagram editing from `ps` or `lean` works only because the extension
  already happens to be installed in the shared extensions directory. Nothing
  in the manifests guarantees it.

## Verification

- Version numbers read directly from each installation, not inferred.
- `light-dark()` support confirmed present in **both** builds before the
  hypothesis was discarded.
- The dcl-mathematics mitigation was verified by rendering the figure through
  `draw.io.exe --export --format png --scale 2 --crop` **before and after**
  making colours explicit, then diffing the two PNGs pixel by pixel: **byte
  identical** (1498 x 1444, `ImageChops.difference` bbox `None`). The change is
  provably implicit-to-explicit only.
- Resulting XML re-validated (259 cells, `math="1"` preserved).
- No remaining `light-dark(` or `=default` tokens in that file.

## Remaining

Nothing gates this. It is environment hygiene, and it is not blocking any
repo. The one genuinely open question is flag 2 (`lean.txt`), which needs a
look at how the `vscode-lean` launcher resolves its extension set before
anything is added.

## Decisions & flags

**Flag 1 — the `offline: false` trap.** The tempting one-line "fix" for the
version skew is to point the extension at the online draw.io. That does not
merely change a renderer: it sends diagram content to an external host. For a
research repo with unpublished figures that is a material change, and it is
declined in advance. **What would confirm it is the wrong move:** nothing —
it is a policy call, not an empirical one. The skew itself is harmless once
files carry explicit colours, which is the real fix.

**Flag 2 — missing `lean.txt`.** `WCDE_VSCODE_PROFILE=lean` was read from a
live session, and `dcl-mathematics/CLAUDE.md` documents a `vscode-lean`
launcher for the Lean 4 + Mathlib project under `src/dcl_formalism/`. But
`vsprofiles/` has no `lean.txt`. **What would confirm or refute:** read the
`vscode-lean` launcher's `requires` line and see which manifest it names. If it
names `lean.txt`, the file is genuinely missing. If it names something else, the
documentation of the profile-to-manifest mapping in `vsprofiles/README.md` is
incomplete. Do not guess.

**Flag 3 — extension isolation.** The user's global CLAUDE.md is emphatic that
each launcher gets its own `--extensions-dir`, and treats that as the reason
tools resolve by bare name. Observation does not match: the draw.io extension
lives in the shared `%USERPROFILE%\.vscode\extensions`, and the only sibling
directories are `.vscode-kanban`, `.vscode-print-resource-cache`, and
`.vscode-shared`. **What would confirm or refute:** inspect the `vscode-*.cmd`
launchers for the actual `--extensions-dir` arguments passed. If isolation is
partial (say, `user-data-dir` isolated but `extensions-dir` shared), the doc
should say so, because per-profile extension manifests mean something quite
different under a shared extensions directory.

**Flag 4 — the pinned value is a preference.** Determinism is the requirement;
`light` is the suggestion.

**Flag 5 — frozen skew is a feature with a documentation debt.** `autoUpdate:
false` is correct and should stay. It just means this skew persists silently,
so it belongs in wcde's known-state documentation rather than being
rediscovered.

## → Consumer actions

- [ ] **Settings:** add to `shells/windows/lib/vsprofiles/user-settings.json`:
      `"hediet.vscode-drawio.theme": "kennedy"`,
      `"hediet.vscode-drawio.appearance": "light"`,
      `"drawio-inline-editor.theme": "light"`.
      The third is the one that actually differs today; the first two are
      pinned to stop future drift. See flag 4 before choosing the values.
- [ ] **Manifests:** decide whether `hediet.vscode-drawio` belongs in
      `common.txt` (diagram editing is used from `ps` and `lean`, not only from
      the `drawio` profile) or whether `drawio.txt` should be composed into
      those profiles. Currently neither is true and it works only by accident.
- [ ] **Gate — flag 2:** do NOT create `lean.txt` until the `vscode-lean`
      launcher's `requires` line has been read and the profile-to-manifest
      mapping confirmed. Then either add the manifest or fix
      `vsprofiles/README.md`.
- [ ] **Gate — flag 3:** do NOT rely on per-profile extension isolation until
      the `--extensions-dir` arguments in the `vscode-*.cmd` launchers have been
      checked against the claim in the user's global CLAUDE.md. If the claim is
      overstated, correct the doc — it is loaded into every session and is
      currently steering behaviour.
- [ ] **Gate:** do NOT set `hediet.vscode-drawio.offline` to `false` (flag 1).
- [ ] **Docs:** record the bundled-vs-desktop draw.io version skew
      (30.2.7 vs 31.3.1, frozen by `extensions.autoUpdate: false`) as known
      state, together with the note that the durable mitigation is explicit
      colours in the `.drawio` files rather than any editor setting.
- [ ] **Docs:** record that `draw.io.exe --export --format png --scale 2 --crop`
      renders correctly and headless in a few seconds (MathJax included), and is
      the source of truth for committed figures — not whichever editor is open.
- [ ] **Promotion:** make the change in DEV (`j:\dev\wcde`) and promote to PROD
      (`c:\prod\wcde`) after verification. Workspace `settings.json` files in the
      DCL repos reference `c:\prod\wcde`, so an unpromoted fix has no effect.
- [ ] **Board:** no issue exists for this yet. Open one in
      `JackDMenendez/discrete-causal-lattice-project` (project 6) if wcde work
      is tracked there, and record the number back into this handoff before
      flipping it to consumed.
- [ ] **Semver:** confirm or overrule the proposed `0.3.1 -> 0.4.0 (MINOR)`.
