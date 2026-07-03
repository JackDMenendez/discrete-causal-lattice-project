---
handoff: 2026-07-03-vscode-ps-canonical-invocation
from: wcde (focused)
to: PM
repo: win-cross-dev-env
branch: main
commits: [ab253f6, d3e6290, 6985a36]
pr: none
status: consumed
state: complete
semver: n/a (unversioned dev-env tooling)
flags:
  - '"dcl-web" is the repo dcl-website — there is no j:\dev\dcl-web. Quarto policy applies to dcl-website.'
  - CuPy must NEVER be installed/built under an ucrt64/msys2 venv — it source-builds and exhausts all RAM (the "memory bomb"). Windows .venv-win only.
  - All .venv-ucrt64 (and dcl-core .venv-gpu) were DELETED from every dcl repo; a session expecting an ucrt64 venv will not find one.
  - All 11 dcl repos now have modified/new .vscode/settings.json (uncommitted, in each repo) from the batch conversion.
decisions:
  - Canonical Windows venv is now C:\Users\jackd\.venv-win (Python 3.14) with cupy-cuda12x[ctk]; the old %USERPROFILE%\.venv (3.14) was deleted.
  - Repos + focused Claude sessions are launched via vscode-ps.cmd, except dcl-website via vscode-quarto.cmd.
consumed_by: PM (dcl-website session) — memory recorded (reference-canonical-venv-win); dcl-web=dcl-website confirmed. DEFERRED (lazy pass): per-repo settings.json commits (11 repos) + opening an infra/dev-env board issue.
consumed_at: 2026-07-03
---

## Summary
The Windows dev environment was reworked so GPU/CuPy work is native-Windows-only
and all DCL repos share one canonical interpreter. Going forward **every repo and
every focused Claude session is invoked via `vscode-ps.cmd`**, with the single
exception of **`dcl-website`**, invoked via `vscode-quarto.cmd`. This unblocks
CuPy (which cannot be built under MSYS2/ucrt64) and gives every session a
consistent, GPU-capable Python plus the ucrt64 C/C++ toolchain — while the web
repo gets a deliberately lean R/Quarto stack. Changes are pushed to
`win-cross-dev-env@main`.

## Shipped
- `ab253f6` — add `vscode-haskell.cmd` launcher (native VS Code + Haskell toolchain).
- `d3e6290` — repoint `CANONICAL_WIN_VENV` to `.venv-win`; `repo-setup.sh` strips
  cupy under MSYS2 (+`--only-binary` backstop); `repo-setup.cmd` installs
  `cupy-cuda12x[ctk]` (binary-only) when a repo requires cupy; `profile.ps1`
  canonical fallback fixed `.venv`→`.venv-win`.
- `6985a36` — new `env/msys2-tools-env.cmd` appends `C:\msys64\ucrt64\bin` +
  `C:\msys64\usr\bin` to PATH; wired into `vscode-ps.cmd` as its final module.

## What "invoked via vscode-ps.cmd (except dcl-website)" means operationally
Both launchers call `setup-vscode.cmd`, so **both write the same
`.vscode/settings.json`**: interpreter → canonical `.venv-win`, terminal →
PowerShell 7 (which auto-activates the venv). The launcher choice therefore does
**not** change settings.json — it changes the **ambient toolchain (PATH/env)** the
VS Code process and its integrated terminals inherit at launch.

**`vscode-ps.cmd`** — every repo + focused Claude session (the default):
- Interpreter: canonical `C:\Users\jackd\.venv-win`, **Python 3.14**, with working
  **CuPy** (`cupy-cuda12x[ctk]`, GPU-verified on the GTX 1060; no system CUDA
  Toolkit needed — the `nvidia-*-cu12` wheels supply it, the driver does the rest).
- Terminal: PowerShell 7.
- On PATH: git + GitHub CLI, MiKTeX (LaTeX), SageMath, VS Code, **plus
  `ucrt64\bin` and `msys64\usr\bin` appended** → `gcc`/`make`/`pkg-config` and the
  MSYS2 coreutils are reachable, with native-Windows tools keeping precedence.
- Net: a session gets Windows Python **with GPU/CuPy**, LaTeX, SageMath, and the
  ucrt64 C/C++ toolchain from one native-Windows shell.

**`vscode-quarto.cmd`** — `dcl-website` only (deliberately lean web-authoring):
- Interpreter: same canonical `.venv-win` (Python from the venv, not pwsh's bundled one).
- Terminal: PowerShell 7.
- On PATH: **R + Quarto** + git-cli + VS Code. **No** MiKTeX/TeX (HTML output only),
  **no** SageMath, **no** MSVC, **no** ucrt64/msys2 toolchain.
- Net: a session there gets a minimal HTML-publishing stack (R/Quarto) + venv
  Python; nothing heavy compiles.

## Verification
- CuPy functional test (elementwise kernel + cuBLAS) passed in `.venv-win` on
  Python 3.14.6 / GTX 1060.
- `global-var.cmd` resolves `CANONICAL_WIN_VENV` → `.venv-win` (cupy importable).
- `vscode-ps.cmd`'s full `requires` chain loads clean (exit 0) with ucrt64 on PATH,
  appended at PATH tail.
- repo-setup cupy guard/strip verified on both bash (`grep`) and cmd (`findstr /c:`)
  paths; the `findstr` space-as-OR gotcha was caught and fixed with `/c:`.
- All 11 dcl repos verified: settings.json now points at `.venv-win` + PowerShell 7.

## Remaining
- Each dcl repo carries an **uncommitted** `.vscode/settings.json` change from the
  conversion — owners decide whether to commit per repo (not done here to avoid
  cross-repo churn).
- `dcl-website` was batch-converted like the rest; its settings.json (PowerShell 7)
  is correct and unaffected by using the quarto launcher (see operational note).

## Decisions & flags
- **`dcl-web` = `dcl-website`.** No `j:\dev\dcl-web` exists. The quarto-launcher
  policy applies to `dcl-website`. Refute by pointing at an actual `dcl-web` repo
  if one is later created.
- **CuPy is native-Windows-only.** No wheel exists for the MSYS2 platform tag
  (`mingw_x86_64_ucrt_gnu`) and no pacman package, so `pip install cupy` under
  ucrt64 builds the sdist from source → runaway parallel NVCC compile → RAM
  exhaustion. Guarded now in `repo-setup.sh`; do not bypass. Confirm by reading
  the wcde memory `cupy-canonical-venv-win`.
- **ucrt64 venvs removed.** All `.venv-ucrt64` + `dcl-core/.venv-gpu` deleted
  (~815 MB). Any session needing a non-canonical venv must recreate via
  `repo-setup` — never with cupy under ucrt64.
- **Canonical = `.venv-win` (Py 3.14).** The redundant `%USERPROFILE%\.venv` was
  deleted; tooling repointed. `physics-research/.venv-win` (repo-local) was preserved.

## → Consumer actions
- [ ] Relay to all focused sessions: launch every repo via `vscode-ps.cmd`; launch
      **`dcl-website`** via `vscode-quarto.cmd`. State the per-launcher toolchain
      (above) so sessions know what is/ isn't on PATH.
- [ ] Memory: record in the PM memory dir — canonical Windows venv is `.venv-win`
      (Py 3.14, CuPy-enabled); CuPy is Windows-only; never build cupy under ucrt64.
      Mirrors wcde memory `cupy-canonical-venv-win`.
- [ ] Gate: do NOT attempt CuPy/GPU work in any ucrt64/msys2 venv — canonical
      `.venv-win` only.
- [ ] Confirm `dcl-web` is `dcl-website` (flag above); correct the policy if a
      distinct `dcl-web` repo exists.
- [ ] Per-repo: decide whether to commit the converted `.vscode/settings.json` in
      each of the 11 dcl repos (incl. dcl-project's new `.vscode/`).
- [ ] Board: note the environment-invocation/toolchain change on the infra/dev-env
      tracking item (repo `discrete-causal-lattice-project`, project 6); open one if
      none exists.
