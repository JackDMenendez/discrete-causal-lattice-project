---
name: LaTeX formatting issue
about: Report a LaTeX rendering or formatting problem
labels: bug, latex
---

## LaTeX formatting issue

**Affected paper repository** (check one)

- [ ] `dcl` -- Paper I
- [ ] `dcl-sm-derivation` -- Paper II
- [ ] `dcl-generator-zoo` (catalogue paper)
- [ ] `dcl-paper-03-tidal-ionization` -- Paper III
- [ ] other: _______________________

**Affected file / section**

e.g. `paper/main.tex`, `paper/sections/audit_table.tex`,
`paper/macros/packages.tex`, line ranges if known.

**Describe the formatting problem**

Clear, concise description of the rendering or formatting issue.

**Expected rendering**

What you expected the output to look like.

**Actual rendering**

What actually appeared in the output.

**Minimal example**

Smallest example that reproduces the problem.

```latex
% paste here
```

**Output affected**

- [ ] PDF body
- [ ] figures
- [ ] tables (`longtable`, audit table, etc.)
- [ ] appendix
- [ ] title page / `\thanks{}` block
- [ ] bibliography
- [ ] other:

**Compiler / toolchain**

- LaTeX engine: pdflatex (project default; use `xelatex` / `lualatex`
  only if explicitly switched)
- Build tool: `build.cmd paper` / `./build.sh paper` (the framework
  default chain) -- or another command:
- Project version: tag or commit hash

**Logs / warnings**

```text
(paste relevant warnings or errors)
```

**Screenshots (if helpful)**

Add screenshots of the formatting issue.

**Additional context**

Any other context.
