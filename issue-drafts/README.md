# Issue drafts

Filled-out issue-template bodies, drafted locally before being filed
on GitHub.  Workflow:

1. **Draft locally.**  Pick the relevant template under
   [`.github/ISSUE_TEMPLATE/`](../.github/ISSUE_TEMPLATE/), copy the
   body (everything below the `---` frontmatter), fill in the fields
   here.  Save as `NNN-<template>-<short-slug>.md` (sequential
   3-digit number; see naming below).
2. **File on GitHub.**  Open the picker at
   <https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/new/choose>,
   select the template (so the `labels:` frontmatter auto-applies),
   select-all in the body field, paste the filled-out draft over the
   empty template.  Submit.
3. **Cross-reference.**  Once the issue has a number (e.g. `#42`),
   rename the draft's title or add a comment in this README's table
   so the local draft and the live issue stay paired.

## Naming convention

`NNN-<template>-<short-slug>.md`

- `NNN` -- sequential 3-digit zero-padded local number, starting at
  `001`.  Local to this folder; not tied to GitHub issue numbers
  (those are assigned by GitHub at file-time).
- `<template>` -- the template type used: `new-subproject`,
  `paper-enhancement`, `research-investigation`,
  `research-artifact`, `experiment-feature`, `formalism-feature`,
  `figure-or-animation`, `release-coordination`,
  `core-software-change`, `latex-formatting`, `bug`,
  `utility-feature`.
- `<short-slug>` -- kebab-case topic.  Match the eventual memory
  entry slug where applicable.

Examples:

- `001-new-subproject-hilbert-sixth-capstone.md`
- `002-paper-enhancement-paper-ii-induced-action-prefactor.md`
- `003-release-coordination-dcl-core-v0-1-0-paper-iii.md`

## Index

| # | Draft | Template | GitHub issue | Status |
|---|---|---|---|---|
| 001 | [Hilbert's Sixth Problem capstone paper](./001-new-subproject-hilbert-sixth-capstone.md) | `new-subproject` | [#2](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/2) | filed |
| 002 | [Paper III -- tidal ionization (retroactive)](./002-new-subproject-paper-03-tidal-ionization.md) | `new-subproject` | [#3](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/3) | filed |
| 003 | [DCL public website](./003-new-subproject-dcl-website.md) | `new-subproject` | [#4](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/4) | filed |
| 004 | [dcl-mathematics foundations repo](./004-new-subproject-dcl-mathematics.md) | `new-subproject` | [#6](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/6) | filed |
| 005 | [δp_min investigation (Paper III prerequisite)](./005-research-investigation-dp-min.md) | `research-investigation` | [#7](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/7) | filed |
| 006 | [dcl-delta-p-min investigation hub (retroactive)](./006-new-subproject-dcl-delta-p-min.md) | `new-subproject` | [#8](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/8) | filed |
| 007 | [dcl-core 3D upgrade (core3d to v1.0 maturity)](./007-new-subproject-dcl-core-3d-upgrade.md) | `new-subproject` | [#9](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/9) | filed |
| 008 | [Lattice dimensional family (spatial vs. internal; colour/space duality)](./008-research-investigation-lattice-dimensional-family.md) | `research-investigation` | [#11](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/11) | filed |
| 009 | [DIY-lattice cookbook (build-your-own 3D lattice how-to)](./009-research-artifact-diy-lattice-cookbook.md) | `research-artifact` | [#12](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/12) | filed |
| 010 | [Paper I substrate premises (coordination-six: prove or soften)](./010-paper-enhancement-paper-i-substrate-premises.md) | `paper-enhancement` | [#10](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/10) | filed |
| 011 | Paper IV optical-axis birefringence (subproject) | `new-subproject` | [#13](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/13) | filed (no local draft) |
| 012 | [Kinematic closed-form ordinary/extraordinary speed split along (1,1,-1)](./012-formalism-feature-kinematic-oe-split.md) | `formalism-feature` | [#14](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/14) | filed (sub-issue of #13) |
| 013 | [exp_02 optical-axis o/e eigenphase cross-check](./013-experiment-feature-exp02-oe-eigenphase-crosscheck.md) | `experiment-feature` | [#15](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/15) | filed (sub-issue of #13) |
| 014 | [Paper IV abstract + introduction](./014-paper-enhancement-paper-iv-abstract-introduction.md) | `paper-enhancement` | [#16](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/16) | filed (sub-issue of #13) |
| 015 | [Gauge-sector birefringence (Q eigenvalues {4,4,16})](./015-formalism-feature-gauge-sector-birefringence.md) | `formalism-feature` | [#17](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/17) | filed (sub-issue of #13) |
| 016 | [exp_03 gauge-sector birefringence companion](./016-experiment-feature-exp03-gauge-sector-companion.md) | `experiment-feature` | [#18](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/18) | filed (sub-issue of #13) |
| 017 | [Multi-channel concordance (P9)](./017-formalism-feature-multichannel-concordance-p9.md) | `formalism-feature` | [#19](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/19) | filed (sub-issue of #13) |
| 018 | [core3d v0.3.0 Peierls gauge field + vacuum response](./018-core-software-change-core3d-peierls-gauge-field.md) | `core-software-change` | [#20](https://github.com/JackDMenendez/discrete-causal-lattice-project/issues/20) | filed (sub-issue of #9; blocks #18) |

## Notes

- The draft files contain *only the body* of the template (the
  `## ...` heading downward).  The frontmatter (`name:`, `about:`,
  `labels:`) is consumed by GitHub's picker and shouldn't be
  pasted into the issue body.
- Filing via the picker matters for `labels:` -- pasting into a
  blank issue (skipping the picker) loses the auto-applied labels
  and forces manual label entry.
- Once an issue is filed, the local draft is mostly historical
  (the live issue on GitHub is the canonical source of truth).
  Keep the draft for provenance / future editing convenience; the
  GitHub issue may diverge as the work progresses.
