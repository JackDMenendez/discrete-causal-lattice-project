---
handoff: 2026-09-04-wcde-lean-profile-missing-manifest
from: dcl-mathematics (focused)
to: PM
repo: win-cross-dev-env (wcde)
branch: main
commits: []                         # none -- diagnosis only, no code written
pr: none
status: consumed
state: in-progress
semver: 0.3.1 -> 0.3.2 (PATCH, unreleased)   # proposed; restores intended behaviour
flags:
  - reprovision-destroys-current-set: do NOT clear `.wcde-provisioned` for the
    lean profile before `lean.txt` exists -- doing so would reinstall from
    `common.txt` only and wipe Lean 4, LaTeX Workshop and the rest.
  - lean-txt-contents-unverified: the proposed manifest is reverse-engineered
    from the live ext dir and may include ad-hoc installs never intended as
    profile policy. Needs an owner's eye before commit.
  - not-the-reported-symptom: this does NOT explain the LaTeX preview failure
    that led to the investigation. That symptom is unresolved and separate.
decisions:
  - vscode-lean.cmd itself needs NO change; the launcher is correct as written.
    The missing artefact is the manifest, not the launcher.
  - PATCH rather than MINOR: this restores intended behaviour rather than
    adding a flavour.
consumed_by: wcde (focused)
consumed_at: 2026-09-04
---

## Summary

`vscode-lean.cmd` sets `WCDE_VSCODE_PROFILE=lean`, but **no `lean.txt` exists**
in `shells/windows/lib/vsprofiles/`, and `lean` is **absent from the
profile -> launcher table** in that directory's `README.md`. Per the README, first
launch of a profile installs `common.txt` + `<profile>.txt`; with no `lean.txt`,
the lean profile is entitled to `common.txt` only -- four extensions.

The live ext dir at `%USERPROFILE%\.vsisolation\lean\ext` is nevertheless richly
populated (18 extensions, including `leanprover.lean4` and
`james-yu.latex-workshop`) and carries a `.wcde-provisioned` marker, so it was
filled by hand or from a manifest that has since gone. **The breakage is latent,
not active:** today's sessions work. It bites on a fresh machine, a new
`%USERPROFILE%`, or any deliberate re-provision -- at which point the lean
profile silently loses the Lean 4 extension, i.e. the entire reason the launcher
exists.

`lean` is the **only** launcher in the tree without a manifest (verified: every
other launcher maps to an existing `<profile>.txt` -- cmd->ps, ghcup->haskell,
miktex->tex, quarto->web, sagemath->sage).

## Shipped

Nothing. No commits, no edits to wcde -- this is a defect report raised from a
neighbouring repo. `j:\dev\wcde` was read only.

## Verification

Evidence gathered 2026-09-04 from a live `lean`-profile session
(`$env:WCDE_VSCODE_PROFILE` = `lean`), repo `dcl-mathematics`:

- `ls shells/windows/lib/vsprofiles/` -> agda, common, drawio, exp-tex, haskell,
  mingw64, ps, python, sage, tex, ucrt64, web, write, README.md,
  user-settings.json. **No `lean.txt`.**
- `README.md` profile table lists ps, web, ucrt64, mingw64, haskell, agda, sage,
  tex, python, exp-tex, drawio, write. **No `lean` row.**
- `shells/windows/cmd/vscode-lean.cmd` line 9: `set "WCDE_VSCODE_PROFILE=lean"`.
- `%USERPROFILE%\.vsisolation\lean\ext` contains 18 extensions and
  `.wcde-provisioned`.
- Cross-check on toolchain intent: the launcher's `requires.cmd` line already
  pulls **miktex** and **graphviz**, which matches the LaTeX and graphviz
  extensions present in the ext dir. The PATH side and the (missing) extension
  side were meant to agree.

Root cause, from wcde history: `d8e6b3d` ("Lean 4 / Mathlib VS Code
integration") added the launcher; `3066352` ("vscode-isolation: per-flavor
isolated VS Code + profile manifests") introduced the manifest system without
creating `lean.txt`; `af3695d` added `write`/`drawio` **with** manifests and left
a comment in `drawio.txt` reading "inherits the lean toolset" -- so a lean
toolset was conceptually assumed while the file was never written.

Semver verdict: PATCH. Additive file plus a docs row, restoring documented
behaviour. No interface change.

## Remaining

The fix, which is two files and no logic:

**1. Create `shells/windows/lib/vsprofiles/lean.txt`.** Proposed contents, being
the live ext dir minus the four in `common.txt`:

```
# lean.txt - vscode-lean profile (Lean 4 / Mathlib theorem proving).
# common.txt is installed too; list only profile-specific extras here.
# The launcher's requires.cmd line also puts MiKTeX and Graphviz on PATH,
# so the LaTeX and Graphviz extensions below are deliberate, not strays.

leanprover.lean4
james-yu.latex-workshop
tecosaur.latex-utilities
hediet.vscode-drawio
purocean.drawio-preview
geeklearningio.graphviz-markdown-preview
tintinweb.graphviz-interactive-preview
stephanvs.dot
shd101wyy.markdown-preview-enhanced
yzhang.markdown-all-in-one
davidanson.vscode-markdownlint
yzane.markdown-pdf
tamasfe.even-better-toml
brunnerh.insert-unicode
```

**2. Add the row to `shells/windows/lib/vsprofiles/README.md`**, in the
profile -> launcher table:

```
| `lean`    | vscode-lean                     | `lean.txt` |
```

Gate: nothing blocks this. It is safe to land at any time **provided** the
reprovision flag below is honoured.

## Decisions & flags

**`vscode-lean.cmd` needs no change** -- recorded because the fix was requested
"in vscode-lean.cmd". The launcher is correct: it sets the profile label, loads
the right `requires` chain (including miktex and graphviz), and calls
`vscode-isolation.cmd` and `setup-vscode.cmd` exactly as its siblings do. The
defect is the absence of the manifest the label points at. The alternative --
repointing the launcher at an existing label such as `tex` -- is **rejected**: it
would drop `leanprover.lean4` and collapse two ext dirs into one, which is what
the isolation design exists to prevent.

**FLAG `reprovision-destroys-current-set`.** The current ext dir is the only
surviving record of what this profile should contain. Clearing
`.wcde-provisioned`, deleting the ext dir, or provisioning on a fresh machine
*before* `lean.txt` lands would reinstall `common.txt` only and destroy the
evidence along with the toolset. **Write `lean.txt` first; test re-provisioning
second.** What would confirm the fix: clear the marker on a throwaway profile
dir, relaunch, and verify all 18 extensions return.

**FLAG `lean-txt-contents-unverified`.** The list above is inferred from what is
installed, not from a statement of intent. Some entries may be ad-hoc installs
from a single session rather than profile policy -- `brunnerh.insert-unicode`,
`yzane.markdown-pdf` and `tamasfe.even-better-toml` are the likeliest strays.
The Lean, LaTeX, drawio and graphviz entries are corroborated by the launcher's
own `requires` line and are safe. What would refute an entry: the owner saying
they installed it for one task.

**FLAG `not-the-reported-symptom`.** This investigation started from a report
that LaTeX **preview and IntelliSense are not working** in a `lean`-profile
window. That symptom is **not explained by this defect** -- `latex-workshop`
10.18.0 is installed, its engine requirement (^1.114.0) is satisfied by VS Code
1.134.0, `pdflatex`/`latexmk`/`perl` all resolve, no `latex-workshop.*` setting
or `.tex` editor association exists in either the workspace or the per-repo
isolation settings, and `notes/notebook.pdf` built successfully the same day.
Current best hypothesis is an extension host that has not reloaded since
provisioning, which is a session-level issue and **not** a wcde change. Do not
close the preview complaint on the strength of this handoff.

## -> Consumer actions

- [ ] wcde: create `shells/windows/lib/vsprofiles/lean.txt` with the contents in
      *Remaining*, after an owner's pass over the three suspected strays named in
      the `lean-txt-contents-unverified` flag.
- [ ] wcde: add the `lean` row to the profile -> launcher table in
      `shells/windows/lib/vsprofiles/README.md`.
- [ ] Gate: do **NOT** clear `.wcde-provisioned`, delete
      `%USERPROFILE%\.vsisolation\lean\ext`, or provision the lean profile on a
      fresh machine until `lean.txt` is committed. See the
      `reprovision-destroys-current-set` flag.
- [ ] wcde: after `lean.txt` lands, verify by re-provisioning a throwaway copy of
      the profile ext dir and confirming all 18 extensions install.
- [ ] wcde: tag `v0.3.2` when landing, or fold into the next release -- PATCH,
      currently unreleased.
- [ ] Audit: confirm no other launcher lacks a manifest. Checked 2026-09-04 and
      `lean` was the only one; worth a re-check whenever a `vscode-*.cmd` is
      added, since nothing enforces the pairing.
- [ ] Separately: the LaTeX preview symptom in `dcl-mathematics` remains
      unresolved and is **not** covered by this handoff. Route it back to the
      dcl-mathematics session rather than closing it here.

## Consumed note (2026-09-04, wcde)

The wcde-tagged consumer actions are done in 98c111b, released as v0.4.0 (folded in rather than tagged v0.3.2). lean.txt written with all 14 profile entries verbatim per the owner's call -- the three suspected strays were RETAINED deliberately. Verified by dry-run provision: 18 extensions (4 common + 14 lean), no 'no manifest' warning, and the .wcde-provisioned marker restored untouched per the reprovision-destroys-current-set gate. NOT done and routed onward: the LaTeX preview/IntelliSense symptom is NOT covered here and goes back to dcl-mathematics; the launcher/manifest pairing audit is recorded in vsprofiles/README.md but nothing enforces it.
