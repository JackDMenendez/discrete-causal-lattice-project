---
handoff: 2026-08-04-wcde-vscode-isolation-canonical-invocation
from: wcde (focused)
to: PM
repo: win-cross-dev-env
branch: main
commits: [3bf5bd7, b678bd7, 7b4c15a, d8e6b3d]
pr: none
status: open
state: complete
semver: n/a (reference/source-of-truth doc; describes win-cross-dev-env @ v0.3.1)
flags:
  - "SUPERSEDES 2026-07-03-vscode-ps-canonical-invocation — that doc is the 'Source of truth' the user-global CLAUDE.md still cites (\"last reconciled 2026-07-03\"). The invocation model has moved on: per-flavor VS Code ISOLATION is now live in PROD, there are many launcher flavors beyond vscode-ps, and $env:WCDE_VSCODE_PROFILE identifies the active flavor. The global CLAUDE.md pointer should be repointed here (consumer action below)."
  - "CuPy is native-Windows-only — NEVER pip install / build under ucrt64/msys2 (source-build → runaway NVCC → RAM exhaustion, the 'memory bomb'). .venv-win + the cupy-cuda12x wheel ONLY. Unchanged from the superseded doc; still load-bearing. See wcde memory cupy-canonical-venv-win."
  - "Launcher-isolated VS Code puts the flavor's toolset on PATH — call tools by BARE NAME, not absolute paths (paths are brittle across the DEV j:\\dev\\wcde / PROD c:\\prod\\wcde split). If a needed tool is missing from PATH inside a launcher session, that is a wcde gap: fix it at source (the flavor's requires/*-env.cmd PATH, or its profile manifest under shells/windows/lib/vsprofiles/), not with a hardcoded path. See wcde memory no-hardcoded-full-paths."
  - "python activation now flows SOLELY through `requires.cmd python` -> env\\python-env.cmd -> lib\\python-activate.cmd (v0.3.1). A launcher gets a venv only if `python` is in its requires list; setup-vscode.cmd writes python.defaultInterpreterPath from DEV_SHELL_ACTIVE_VENV_PATH. Do NOT re-add ad-hoc python-activate.cmd calls."
decisions:
  - "Canonical Windows venv remains C:\\Users\\jackd\\.venv-win (Python 3.14, cupy-cuda12x[ctk]); one venv for every repo (no per-repo/.venv-ucrt64/.venv-gpu)."
  - "Repos + focused sessions launch via vscode-ps.cmd by default; dcl-website via vscode-quarto.cmd (web profile). Other flavors (lean/exp-tex/python/agda/sagemath/ghcup/haskell/miktex/mingw64/ucrt64/cmd) exist for specialized work."
consumed_by:
consumed_at:
---

## Summary
This is the current source-of-truth for **how DCL repos and focused Claude
sessions are launched on Windows**, replacing `2026-07-03-vscode-ps-canonical-invocation`.
Since that doc: VS Code launches are now **per-flavor isolated** (each launcher
gets its own `--user-data-dir` + `--extensions-dir`), the flavor set has grown
well past `vscode-ps`/`vscode-quarto`, `$env:WCDE_VSCODE_PROFILE` names the active
flavor, and per-flavor extension manifests live under
`shells/windows/lib/vsprofiles/`. This is all **live in PROD** (`c:\prod\wcde`) as
of **win-cross-dev-env v0.3.1** (2026-08-04). The canonical-venv / CuPy / bare-tool-name
rules from the superseded doc still hold and are carried forward here.

## What is canonical now (the model to relay to sessions)

**Interpreter (unchanged):** canonical `C:\Users\jackd\.venv-win` (Python 3.14,
CuPy via `cupy-cuda12x[ctk]`, GPU-verified). One venv for every repo. Terminal is
PowerShell 7, which auto-activates the venv.

**Launch = a per-flavor `vscode-*.cmd` launcher.** Each launcher:
1. runs its `requires.cmd` chain (the flavor's toolset onto PATH),
2. sets `$env:WCDE_VSCODE_PROFILE` (e.g. `ps`, `web`, `lean`, `python`,
   `exp-tex`, `ucrt64`, `mingw64`, `agda`, `haskell`, `sage`, `tex`),
3. starts an **isolated** VS Code instance (own `--user-data-dir` +
   `--extensions-dir`, `--sync off`), provisioned from that flavor's extension
   manifest (`shells/windows/lib/vsprofiles/<profile>.txt` + `common.txt`),
4. writes `.vscode/settings.json` via `setup-vscode.cmd` (interpreter → the venv
   python **iff** `python` is in the flavor's requires; terminal → PowerShell 7).

**Which flavor am I in?** Check `$env:WCDE_VSCODE_PROFILE`; map it via the
profile→toolset table in `shells/windows/lib/vsprofiles/README.md`. Unset ⇒ a bare
session not started by a launcher. Rough default when guessing: `ps` = full stack
(CuPy, LaTeX, SageMath, gcc/make); `web` = Quarto only, no TeX/compilers.

**Consequence of isolation:** the flavor's ambient PATH reaches the VS Code
process and the shells Claude Code spawns, so tools resolve by **bare name**
(`quarto` in `web`, `lean`/`lake` in `lean`, `gcc` in `ucrt64`). Prefer bare tool
names + relative/workspace paths. A tool missing from PATH inside a launcher
session is a **wcde gap** — fix at source (see flags), do not hardcode a path.

**Flavors of note added since 2026-07-03:** `lean` (Lean 4 / Mathlib + graphviz,
v0.3.1), `python` and `exp-tex` (v0.2.0), plus vim/nvim editor integration wired
into `setup-vscode.cmd` (gated on `WCDE_VSVIM_ACTIVE` / `WCDE_NVIM_ACTIVE`).

## Verification
- PROD `c:\prod\wcde` confirmed at v0.3.1 (new lean/mathlib/graphviz env files
  present; modified win-choco/setup-vscode/python-activate carry v0.3.1 content;
  `git archive v0.3.1` tree-vs-PROD diff showed only fs-metadata noise).
- `requires.cmd global python` publishes the canonical `.venv-win`; a python
  launcher writes the correct `python.defaultInterpreterPath`; a non-python
  launcher omits it (both exercised in real cmd subshells).

## Remaining
- The user-global CLAUDE.md still cites the superseded 2026-07-03 doc as source of
  truth — repoint it here (consumer action).
- Open design calls inherited from 2026-07-29 (unchanged by this release): whether
  the `python` profile should guarantee its dev-deps (scipy/pytest/editable
  dcl_core) via a seed step; `laytex` vs `latex` spelling; retiring the unreferenced
  `env/texlive-env.cmd`; `extensions.autoUpdate` value-type alignment
  (`false` boolean vs `"off"` string). Tracked in [[2026-08-04-wcde-v0.3.1-released]].

## Decisions & flags
See frontmatter. Load-bearing: this doc supersedes the 2026-07-03 source-of-truth;
CuPy stays Windows-`.venv-win`-only; call tools by bare name inside a launcher and
treat a missing tool as a wcde gap; python activation has exactly one path
(`requires.cmd python`).

## → Consumer actions
- [ ] Repoint the user-global `~/.claude/CLAUDE.md` "Source of truth" line from
      `2026-07-03-vscode-ps-canonical-invocation` to THIS handoff, and update the
      "last reconciled" date to 2026-08-04. (User's private global file — PM/user
      to apply; wcde did not edit it unprompted.)
- [ ] Relay the launch model above to focused sessions: per-flavor isolated
      `vscode-*.cmd`; identify flavor via `$env:WCDE_VSCODE_PROFILE`; call tools by
      bare name; report a missing-on-PATH tool as a wcde gap.
- [ ] Memory (PM dir): note isolation-in-PROD + `$env:WCDE_VSCODE_PROFILE` is the
      flavor selector; mirrors wcde memory. Keep the CuPy-Windows-only + canonical
      `.venv-win` facts.
- [ ] Board: note the invocation-model update on the infra/dev-env tracking item
      (repo `discrete-causal-lattice-project`, project 6).
