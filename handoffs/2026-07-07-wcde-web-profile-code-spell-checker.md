---
handoff: 2026-07-07-wcde-web-profile-code-spell-checker
from: PM (dcl-website session)
to: wcde (focused)
repo: win-cross-dev-env
branch: main
commits: []                         # request; no wcde commits — the wcde session makes them (still soak-gated)
pr: none
status: open
state: blocked                      # folds into the wcde isolation DEV-soak gate (2026-07-05 / 2026-07-06)
semver: n/a (wcde manifest addition; bump decided at the wcde commit per 2026-07-05)
flags:
  - "GROUNDED, not a wish: dcl-website ships `cspell.json` at repo root — a real Code Spell Checker config with a custom project dictionary (arXiv, core3d, dcl_core, Poincaré, Zenodo, viXra, ORCID, ...) and ignorePaths (_site, .quarto, site_libs, .venv-*). The extension that READS it — `streetsidesoftware.code-spell-checker` — is NOT in the `web` profile manifest (web.txt lists only quarto.quarto; common.txt adds vim/gitlens/claude-code/editorconfig). So in a launcher-isolated vscode-quarto session the project's spell-check config is INERT. This is the wcde 'tool missing from PATH is a wcde gap' rule, applied to extensions."
  - "GATE — fold into the existing soak, do NOT make it a separate PROD change: the whole vscode-isolation / per-profile-manifest tree is UNCOMMITTED in j:\\dev\\wcde and DEV-soak-gated (handoffs 2026-07-05-wcde-vscode-isolation + 2026-07-06-wcde-python-profile-soak-findings; memory wcde-dev-soak-before-release / wcde-vscode-isolation-gate). Adding a line to web.txt re-touches that gated tree — bundle it into the same soak/commit, never roll to PROD (c:\\prod\\wcde) before the user's soak sign-off."
  - "EXTENSION-ID UNVERIFIED (ties to the 2026-07-05 open item): `code` CLI is NOT on PATH in this web-profile session, so I could not run `code --list-extensions` to confirm the id. Verify `streetsidesoftware.code-spell-checker` is exact before relying on it (a wrong id fails that one install silently, per the 2026-07-05 handoff)."
decisions:
  - "Requested via handoff, not a direct edit: this session (dcl-website/PM) owns only dcl-project + dcl-website; wcde is another session's province."
  - "code-spell-checker is REQUIRED (config already present); redhat.vscode-yaml is RECOMMENDED-OPTIONAL only (there are 3 .yml incl _quarto.yml + qmd front matter, but no schema config shipped) — the wcde session's call whether to include it."
consumed_by:
consumed_at:
---

## Summary
Requests one extension be added to the wcde `web` VS Code isolation profile:
**`streetsidesoftware.code-spell-checker`**. The dcl-website repo already carries
a `cspell.json` (custom dictionary + ignore paths), but the `web` profile
manifest provisions only `quarto.quarto`, so a launcher-isolated authoring
session has the spell-check config but not the extension that acts on it —
prose-heavy essay work (46 `.qmd` files) with no working spell-check. Optionally
also add `redhat.vscode-yaml` for `_quarto.yml` + front-matter. This folds into
the still-gated wcde isolation soak; it is not a standalone PROD change.

## Shipped
Nothing — this is a request to the wcde session. The observed state:
- `web.txt` = `quarto.quarto` (only extra beyond common.txt).
- `common.txt` = vscodevim.vim, eamodio.gitlens, anthropic.claude-code, editorconfig.editorconfig.
- dcl-website `cspell.json` present (repo root), configured, unused in-editor.

## Verification
- Confirmed `$env:WCDE_VSCODE_PROFILE = web`; `quarto` resolves on PATH;
  `code` does NOT (flag 3).
- Confirmed `cspell.json` is a real Code Spell Checker config (dictionary +
  ignorePaths) by reading it.
- Extension-id correctness: NOT verified in-session (no `code` CLI) — flag 3.

## Remaining
- wcde session: add the extension id(s) to `web.txt`, re-provision, verify id.
- Stays blocked on the wcde DEV-soak sign-off (do not commit/PROD before then).

## Decisions & flags
See frontmatter. Load-bearing: the need is grounded in an already-shipped
`cspell.json` (not a preference); it must fold into the gated soak commit, not a
separate PROD roll; and the id is unverified because `code` is absent from PATH.

## → Consumer actions
- [ ] Add `streetsidesoftware.code-spell-checker` to
      `shells/windows/lib/vsprofiles/web.txt`.
- [ ] Optional: add `redhat.vscode-yaml` to `web.txt` (schema help for
      `_quarto.yml` + qmd front matter) — wcde's call; not required.
- [ ] Verify the exact id against `code --list-extensions` before trusting it
      (flag 3; closes part of the 2026-07-05 "extension ids UNVERIFIED" item).
- [ ] Re-provision the `web` profile: delete
      `%USERPROFILE%\.vsisolation\web\ext\.wcde-provisioned` (or the whole `ext`
      dir) so the next `vscode-quarto` launch installs from the manifests.
- [ ] Gate: bundle this into the DEV-soak isolation commit (2026-07-05 /
      2026-07-06); do NOT commit the wcde tree or roll to PROD before the user's
      soak sign-off. Fold it into the follow-up handoff that supersedes
      `2026-07-03-vscode-ps-canonical-invocation`.
