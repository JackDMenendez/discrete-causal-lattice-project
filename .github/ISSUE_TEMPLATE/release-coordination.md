---
name: Release coordination
about: Track a release (single-repo or co-released across repos) end-to-end
labels: release
---

## Release coordination

**Repository being released** (check one)

- [ ] `dcl` (rarely; immutable since v1.0)
- [ ] `dcl-sm-derivation`
- [ ] `dcl-generator-zoo`
- [ ] `dcl-paper-03-tidal-ionization` -- Paper III
- [ ] `dcl-core`
- [ ] `dcl-formalism` (planned)
- [ ] other: _______________________

**Version**

- Target version: `vX.Y.Z`
- Prior version: `vX.Y-1`
- Planned release date: `YYYY-MM-DD`

**Co-released with** (check any that apply -- order matters)

A *co-released* release means another repo is released in the
same window with a binding dependency.  Per the cross-repo
coordination rule, **dcl-core releases FIRST** when a paper
depends on it, so the paper can pin to the new tag before its
own Zenodo deposit.

- [ ] `dcl-core` (engine; release this BEFORE any consumer paper)
- [ ] `dcl-paper-03-tidal-ionization` (pins `dcl_core`; release
      AFTER `dcl-core`)
- [ ] `dcl-formalism` (planned; if it co-releases with a paper,
      release BEFORE)
- [ ] other consumer paper:

**Pre-release checklist** (the universal steps)

- [ ] Working tree clean on `main`
- [ ] CI green at HEAD
- [ ] `release_notes/vX.Y.md` drafted
- [ ] `release_notes/vX.Y-release-message.md` drafted
- [ ] `CITATION.cff` -- `version`, `date-released` updated
- [ ] For paper repos: `paper/main.tex` `\thanks{}` block updated
- [ ] For `dcl-core`: `src/dcl_core/_version.py` bumped
- [ ] For `dcl-formalism`: `src/dcl_formalism/_version.py` bumped

**For paper repos that depend on `dcl-core` (Paper III, future
papers): pre-release pin bump**

- [ ] `dcl-core` has a tagged release (NOT `@main`).
- [ ] `virtual-env-requirements.txt`: `dcl_core @ git+...@vX.Y.Z`
- [ ] `CITATION.cff`: add a `references:` entry with the
      `dcl-core` Zenodo DOI for that tag
- [ ] Venv reinstalled with the pinned version
- [ ] Experiment re-run as a sanity check (results unchanged
      within tolerance under the pin change)
- [ ] "Pre-release: pin dcl_core to vX.Y.Z" commit on `main`

**Release steps** (the reserved-DOI workflow)

- [ ] Final build + audit (`build.cmd paper` for paper repos,
      `pytest` for software repos)
- [ ] [User] Reserve a Zenodo DOI (deposit stays in Draft)
- [ ] Insert DOI in `CITATION.cff`, `paper/main.tex` `\thanks{}`,
      release notes; rebuild
- [ ] For paper repos: snapshot `build/main.pdf` to
      `.stage/<name>_vX.Y.pdf`
- [ ] Commit "vX.Y release: fill DOI placeholders, snapshot PDF"
- [ ] [User] Upload artifact(s) to Zenodo and Publish (locks DOI)
- [ ] Tag `vX.Y` and push the tag
- [ ] Create the GitHub Release using the release-message body
- [ ] For software repos: (optional) publish to PyPI
- [ ] For `dcl-core` releases: walk downstream consumers (open
      bump-and-rebuild issues in each pinning paper repo)

**Post-release**

- [ ] Confirm the Zenodo deposit is in the
      `a1-discrete-causal-lattice` community
- [ ] Verify `gh release view vX.Y` renders correctly
- [ ] Update each paper repo's `CITATION.cff` `references:`
      entry if this release became the new pinned engine
- [ ] Bump `CLAUDE.md`'s CURRENT STATUS block in the released
      repo to the next planned increment

**Notes / blockers / observations**

(Use this section for the release-day narrative -- anything that
went sideways, post-mortem material, etc.)
