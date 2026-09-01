---
handoff: 2026-09-01-wcde-write-drawio-flavors
from: wcde (focused)
to: PM
repo: win-cross-dev-env
branch: main
commits: [af3695d, af1a76e]
pr: none
status: open
state: complete
semver: 0.3.1 -> 0.4.0 (MINOR, UNRELEASED - pushed to main, NOT tagged, PROD still v0.3.1)
flags:
  - "UNRELEASED AND UNTAGGED - the release decision is the user's and is still open. Both commits are pushed to origin/main, but there is NO v0.4.0 tag and c:\\prod\\wcde is still v0.3.1. This is MINOR by strict semver (it adds two user-facing flavors, `write` and `drawio`). Note the precedent in [[2026-08-04-wcde-v0.3.1-released]]: v0.3.1 was tagged PATCH though it also added a feature, so the next bump must not be mis-sequenced off that tag. If released, the extract-over deploy is still SAFE: `git diff --diff-filter=D v0.3.1..HEAD` is empty, so no tracked file is deleted and no stale-file clearing of PROD is needed."
  - "EXTENSION IDS ARE NOW VERIFIED - this CLOSES the long-standing 'ids UNVERIFIED' flag carried by 2026-07-05-wcde-vscode-isolation and 2026-07-07-wcde-web-profile-code-spell-checker. Evidence is empirical, not a `code --list-extensions` run: every id resolved and installed with a real version into its isolated ext dir - streetsidesoftware.code-spell-checker-4.5.6, ltex-plus.vscode-ltex-plus-15.7.1, chrischinchilla.vale-vscode-0.34.0, yzhang.markdown-all-in-one-3.6.3, quarto.quarto-1.135.0, hediet.vscode-drawio-1.9.0. A wrong id fails its install silently, so a present versioned directory is proof the id is correct."
  - "THE 2026-07-07 'INERT SPELL-CHECK' PREMISE NO LONGER HOLDS AS OF TODAY - do not consume that handoff expecting to fix a live breakage. streetsidesoftware.code-spell-checker-4.5.6 is ALREADY installed in the web profile ext dir, added through the VS Code UI at some point after that handoff was written. Its provisioned marker still dates to Jul 8, i.e. the manifest never installed it. So af1a76e buys REPRODUCIBILITY (a fresh web profile now gets it) rather than repairing a currently-broken state, and NO marker deletion is needed today."
  - "MANIFEST DRIFT - five extensions are installed through the UI but are in no manifest, so a from-scratch re-provision would silently drop them. write profile: davidanson.vscode-markdownlint, shd101wyy.markdown-preview-enhanced, github.vscode-pull-request-github, ms-vscode.notepadplusplus-keybindings. drawio profile: purocean.drawio-preview. The first two are squarely writing tools and are strong candidates for write.txt; the latter two are general and would belong in common.txt if kept. Needs a keep-or-drop decision per extension - this handoff does NOT decide it."
  - "TWO PATHS DELIBERATELY LEFT UNCOMMITTED. `.vscode/settings.json` is excluded for the same reason as v0.3.1 - setup-vscode.cmd regenerates it on every launcher run and its paths flip DEV/PROD by %WCDELEVEL%, so it is machine state. `.claude/` is untracked because it holds settings.local.json (machine-local). Neither is a candidate for this release; .gitignore entries for both are still not written."
decisions:
  - "LTeX config lives in lib/vsprofiles/user-settings.json (the per-profile seed), NOT in a repo's .vscode/settings.json, because setup-vscode.cmd rewrites that file wholesale on every launch and would destroy it. configurationTarget points dictionary/disabledRules/hiddenFalsePositives at workspaceFolderExternalFile so per-repo vocabulary lands in the repo and survives. VERIFIED landed: the essay repo's write-profile seed carries the ltex keys."
  - "The `write` flavor deliberately omits `python`. setup-vscode.cmd writes python.defaultInterpreterPath only when `python` is in a flavor's requires, so omitting it keeps the canonical venv out of a prose workspace entirely."
  - "pandoc-env / vale-env / calibre-env each probe the REAL install directory rather than relying on a Chocolatey shim in %CHOCOLATEY_PATH%\\bin, which would drag the whole win-choco chain (and ghcup with it) into an otherwise lean flavor."
  - "redhat.vscode-yaml, offered as recommended-optional by 2026-07-07, is NOT taken: no schema config is shipped for _quarto.yml, so it would add an extension for no configured benefit."
consumed_by:
consumed_at:
---

## Summary
win-cross-dev-env gains two VS Code flavors: **`write`** (creative writing /
long-form prose) and **`drawio`** (diagram editing). Both are pushed to
origin/main but **not tagged and not in PROD** — the release call is open. The
same push also lands the `code-spell-checker` addition that handoff
`2026-07-07-wcde-web-profile-code-spell-checker` requested, so that handoff can
be closed, though its premise has drifted (see flags). The `write` flavor was
built to serve a real consumer: `j:\dev\Question-Number-Three-and-the-Unfinished-Sentence`,
an essay bound for Medium, which is now authoring against it.

## Shipped
- `af3695d` — **`write` and `drawio` flavors.** New launchers `vscode-write.cmd`,
  `vscode-drawio.cmd`, `win-drawio.cmd`; new env modules `pandoc-env.cmd`,
  `vale-env.cmd`, `calibre-env.cmd`, `drawio-env.cmd`; new manifests `write.txt`,
  `drawio.txt`; LTeX defaults added to `user-settings.json`; `setup-vscode.cmd`
  writes the `*.svg` → draw.io editor association guarded on
  `WCDE_DRAWIO_ACTIVE`; both flavors added to the vsprofiles README table.
- `af1a76e` — **`web` profile: `streetsidesoftware.code-spell-checker`**, closing
  the request from `2026-07-07-wcde-web-profile-code-spell-checker`.

13 files, +243 lines, no deletions.

## Verification
- **Requires chain, real cmd subshell:** `requires.cmd global win git-cli pandoc
  miktex quarto calibre vale vsvim nvim vscode` exits **0**; `WCDE_PANDOC_EXE`,
  `WCDE_VALE_EXE` and `WCDE_CALIBRE_EXE` all resolve to real binaries, and
  `pandoc.exe`, `vale.exe`, `ebook-convert.exe` and `quarto.cmd` all resolve on
  PATH by bare name.
- **Extension ids:** verified empirically by installed-version directories — see
  flag 2. This closes an item open since 2026-07-05.
- **LTeX seed:** confirmed present in the write profile's repo-local
  `settings.json`, so the `user-settings.json` change demonstrably takes effect.
- **Downstream consumer:** the essay repo builds end-to-end through the flavor —
  Pandoc renders 5,953 words to 32KB of HTML with drafting comments stripped and
  no duplicate title; Vale reports 0 errors.
- **PROD deploy safety:** no deletions in `v0.3.1..HEAD`, so extract-over remains
  safe if released.
- **Semver verdict:** MINOR (0.4.0). Not applied — see flag 1.

## Remaining
- The **release decision** (tag v0.4.0 + roll to PROD, or hold) — user's call,
  nothing technical blocks it.
- The **manifest drift** keep-or-drop decision on five UI-installed extensions.
- Carried over, untouched by this work: the `laytex` vs `latex` spelling of
  `laytex-env.cmd`, retiring the unreferenced `env/texlive-env.cmd`, aligning
  `extensions.autoUpdate` value type, and the `python`-profile dev-deps question
  — all from `2026-08-04-wcde-v0.3.1-released`.
- Still owed from `2026-08-04-wcde-vscode-isolation-canonical-invocation`: the
  user-global CLAUDE.md still cites the superseded 2026-07-03 doc as source of
  truth. That pointer is now further out of date — the flavor table it describes
  has gained `write` and `drawio`.

## Decisions & flags
See frontmatter; all five flags are load-bearing. The two a careless reader would
drop: **this is pushed but NOT released**, so anyone assuming `main` equals PROD
will be wrong about `c:\prod\wcde`; and **the 2026-07-07 handoff's "spell-check is
inert" premise is stale** — the extension is already installed by hand, so closing
that handoff is bookkeeping, not a repair. The extension-id flag is the good news:
it closes an unknown that has been open across three handoffs.

## → Consumer actions
- [ ] Decide the release: either tag **v0.4.0** on `af1a76e` and roll to
      `c:\prod\wcde` via `git archive v0.4.0 | tar -x`, or record that it is
      deliberately held on `main`. Extract-over is safe (no deletions verified).
      Do NOT tag it PATCH — see flag 1 on the v0.3.1 precedent.
- [ ] Consume and close `2026-07-07-wcde-web-profile-code-spell-checker`: flip
      `status: open -> consumed`, cite `af1a76e`, and record that the extension
      was already present manually so the fix is reproducibility, not repair.
- [ ] Propagate the closed extension-id unknown into
      `2026-07-05-wcde-vscode-isolation` if it still carries the UNVERIFIED flag,
      citing the six verified ids in flag 2.
- [ ] Decide per extension whether the five drifted UI-installed extensions join
      `write.txt` / `drawio.txt` / `common.txt` or are dropped; anything kept must
      be added to a manifest or the next re-provision loses it.
- [ ] Repoint the user-global CLAUDE.md "Source of truth" line from
      `2026-07-03-vscode-ps-canonical-invocation` to
      `2026-08-04-wcde-vscode-isolation-canonical-invocation`, and add `write` and
      `drawio` to the flavor list it summarizes.
- [ ] Memory: record in the wcde session memory that `write` and `drawio` flavors
      exist and that `vscode-write.cmd` is how the essay repo is opened; link
      [[no-hardcoded-full-paths]].
- [ ] Gate: do NOT add per-repo editor config to `.vscode/settings.json` in any
      repo opened by a wcde launcher — `setup-vscode.cmd` rewrites it wholesale.
      Use the tool's own config file, or the profile seed `user-settings.json`.
