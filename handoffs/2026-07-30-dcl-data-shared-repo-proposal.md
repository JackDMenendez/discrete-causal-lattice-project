---
handoff: 2026-07-30-dcl-data-shared-repo-proposal
from: dcl-mathematics (focused)
to: PM
repo: JackDMenendez/dcl-mathematics
branch: main
commits: [883f0ea, c4beff8]
pr: none
status: consumed
state: pm-decided                   # APPROVED as a board item (#29 / internal 028); repo CREATION still gated on the bit-reproducibility verify below
semver: n/a (proposal + research notes, no software change)
flags:
  - "UNVERIFIED PREMISE: the whole 'store recipes + hashes, not bulk' design assumes dcl-core is BIT-REPRODUCIBLE from (version, config, seed). Nobody has checked. Any nondeterminism (RNG state, thread scheduling, dict/set iteration order, parallel reduction order) breaks the hash contract and forces bulk storage + LFS instead. VERIFY BEFORE ADOPTING."
  - "CONVENTION CONFLICT: proposing dcl-data as machine-readable source of truth for audit verdicts CONTRADICTS the documented convention that `paper/sections/audit_table.tex` IS the authority (dcl-mathematics CLAUDE.md; the claim-auditor agent relies on it). Either the convention changes or dcl-data is advisory only. Do not let this be settled silently by whoever writes code first."
  - "CROSS-CUTTING SCHEMA CHANGE: the proposed per-artifact God-eye flag (observer-accessible: true/false) changes claim-auditor behaviour in EVERY paper repo, not just dcl-mathematics. It is the mechanism that stops a PASS row resting on a simulation-only quantity, so it is worth having — but it is a program-wide convention, not a dcl-data-local detail."
  - "SCOPE-CREEP RISK: a data repo without an enforced scoping rule becomes an unusable bulk store needing LFS within months. The recipe+hash rule is the only thing keeping it viable and it is currently just a recommendation."
  - "NOT URGENT YET, BUT ORDER MATTERS: nothing is blocked today because successor-architecture coding has not begun. It becomes urgent the moment it does — instrumentation outputs will otherwise land ad hoc in dcl-core and be expensive to relocate."
decisions:
  - "Recommend storing run manifests + output HASHES + small decision-bearing artifacts (census tables, band summaries, T1-T13 verdicts, figures) — NOT bulk per-tick histories, which regenerate."
  - "Recommend pip-installable distribution with tagged releases, matching the existing dcl-core-into-.venv-win pattern; papers cite a pinned `dcl-data vX.Y` the way deposits cite a DOI."
  - "Recommend a per-artifact God-eye flag in the schema (see flags)."
  - "Deliberately did NOT create the repo or a board issue from this session — standing up a repo touches wcde setup, the board, and every downstream consumer, so it is routed as a proposal."
consumed_by: PM (dcl-website session)
consumed_at: 2026-07-29
pm_decision: "APPROVED to stand up dcl-data. Board issue #29 (internal 028, 'Infrastructure') opened in discrete-causal-lattice-project and added to project 6, linking this handoff. Repo CREATION is HARD-GATED on a dcl-core bit-reproducibility verification (see checklist) — if runs are not bit-reproducible from (version, config, seed), re-scope to bulk+LFS before creating anything. R3 audit-authority conflict left UNRESOLVED for deliberate ruling (recorded on the issue), R2 God-eye flag noted as a program-wide convention. δp_min finding routed to dcl-delta-p-min (2026-07-29-dpmin-geometric-fitted-branch-input); referee M6 routed to paper-04 (2026-07-29-paper04-referee-M6-answered-bell-note)."
---

## Summary

The successor-architecture thread in `dcl-mathematics` has produced a test plan
(T1-T13) and an instrumentation spec whose outputs several repos need to share:
`dcl-core` produces them, `dcl-mathematics` cites them in the paper and Lean,
`dcl-delta-p-min` bears on one of them, and the paper repos' audit tables should
be reconciled against them. There is currently **no shared home for data** —
only for code, via dcl-core releases into `.venv-win`. This handoff proposes a
new **`dcl-data`** repo, states the requirements that keep it viable, and asks
the PM for a decision. Nothing is blocked today; it becomes blocking the moment
successor-architecture coding starts, because instrumentation output will
otherwise land ad hoc.

## Shipped

- `883f0ea` — `notes/successor_geometries_simplex_face_lattice.md` (the simplex
  face lattice, the (d+1):1 anisotropy theorem, isotropy-at-k=d+1 vs
  chirality-at-k=d, the four electron filters selecting architecture A2, the
  T1-T13 test plan and A0-A4 results table, and the sector-relative correction);
  `notes/dcl_core_handoff_queue.md` (staging list for the eventual dcl-core
  handoff, explicitly not itself a handoff); §11 of the Bell note (calibration
  invariance / the interface argument); §4.9 and §5.1 of the philosophy note.
- `c4beff8` — the philosophy thread and figure this rests on
  (`figures/philosophical.drawio`, `notes/platos_cave_invariant_observer.md`,
  Bell note §10).

## Verification

n/a — no software. The proposal's technical premise (bit-reproducibility) is
**unverified** and is flagged as such; that check is a consumer action, not
something this session could run.

## Remaining

The decision itself, plus the four requirement areas below. All of it is
cheap to settle now and expensive to retrofit later.

### Why a data repo is needed

1. **Cross-repo consumption.** `dcl-mathematics` is paper + Lean and holds no
   Python by convention, but it needs numbers to cite (the {1,4,4} eigenvalues,
   the (d+1):1 check, T1-T13 verdicts) and figures. Today those would have to be
   copy-pasted out of a dcl-core working tree.
2. **Citable pinning.** A paper citing a computed number needs a *versioned*
   source, the same discipline already applied to Zenodo deposits. Otherwise
   "the number changed" is untraceable.
3. **Downstream blast radius.** Paper IV's no-go forced re-versioning of Papers
   I and II. A shared verdict store is how the next such event finds every
   affected row instead of relying on memory.

### Requirement R1 — scoping rule (the thing that keeps it usable)

> Store the **recipe** and the **hash**, plus decision-bearing artifacts.
> Do **not** store bulk output.

The state is exact integers (a partition of N units; cells hold 0..N), so runs
are deterministic and outputs verifiable by hash rather than by tolerance
comparison. Bulk histories regenerate; the hash proves the regeneration is
bit-identical. **Conditional on the reproducibility flag above.**

Store: run manifests (code version, config, seed), output hashes, the local
pattern census, band-structure summaries, T1-T13 verdicts, figures.
Do not store: per-tick histories for every run.

### Requirement R2 — God-eye flag in the schema

Every artifact carries `observer-accessible: true|false`. Amplitude-layer
products (phase fields, joint states, anything read by inspecting an array) are
God-eye: legitimate for debugging and positive controls, **never evidence about
the world**. With the flag in the schema, `claim-auditor` can mechanically
refuse a PASS row resting on a God-eye quantity, instead of that discipline
depending on vigilance. See `dcl-mathematics/notes/platos_cave_invariant_observer.md` §6.

### Requirement R3 — audit-verdict integration (needs the convention resolved)

Verdicts (PASS/PART/STUB/FAIL per test per architecture) are the natural
contents of dcl-data, and would let paper audit tables be *reconciled against* a
pinned version rather than independently typed. **This conflicts with the
current documented authority of `audit_table.tex`** — see flags. PM decides
which way it resolves.

### Requirement R4 — distribution

Pip-installable with tagged releases, matching the dcl-core-into-`.venv-win`
pattern already in use. Works for manifests plus small canonical artifacts;
works badly for bulk, which is a second reason R1 is load-bearing rather than
tidiness.

## Decisions & flags

See frontmatter. The two that most need a human decision:

**Bit-reproducibility.** The entire design is a bet that a dcl-core run is
reproducible from its recipe. If it is not, `dcl-data` must instead be a bulk
store with LFS, which is a materially different repo with different costs. This
is checkable in an afternoon and should be checked *before* the repo is created,
not after it fills up.

**Audit authority.** `dcl-mathematics/CLAUDE.md` states that the claim auditor
treats `paper/sections/audit_table.tex` as authoritative and that the CLAUDE.md
mirror is orientation only. Making dcl-data the verdict source of truth inverts
that. Both are defensible; what is not defensible is having two sources of truth
and discovering the drift during a release. Flagged so it is decided
deliberately.

Two adjacent items surfaced by the same thread, routed here because they are
cross-repo rather than dcl-data-specific:

- **δp_min gate (`2026-07-16-dpmin-derived-or-fitted-gate`, still open).** New
  evidence from the geometry side: if the facet index is selected with equal
  weight over d+1 facets then δp_min = 1/(d+1) *by construction*, and
  1/δp_min − 1 = d identically — true for every d, therefore selecting nothing.
  That is the gate's **fitted** branch arriving from geometry rather than
  experiment. Source: successor-geometries note §6.
- **Paper IV referee major M6** (A=1 nonlinear QM / signalling:
  Weinberg / Gisin / Polchinski) is **answered** by the Bell note §10.5-10.6 —
  the Gisin tension between an entangling nonlinearity and non-signalling, with
  floor-as-admissibility rather than floor-as-clamp as the proposed resolution.

## → Consumer actions

- [x] **Decide:** APPROVED (PM, 2026-07-29). Opened board issue **#29**
      (internal 028, "028 Infrastructure Stand up dcl-data shared data repo …")
      in `discrete-causal-lattice-project`, added to project 6, links this
      handoff. Repo creation still gated on the bit-reproducibility verify below.
- [ ] **Verify before creating:** confirm `dcl-core` runs are bit-reproducible
      from (version, config, seed) — check RNG seeding, thread/parallel
      reduction order, and any dict/set iteration dependence. If NOT
      reproducible, R1 is void and the proposal must be re-scoped to bulk +
      LFS before any repo is created.
- [ ] **Resolve the authority conflict:** rule on whether `audit_table.tex`
      remains authoritative with dcl-data advisory, or dcl-data becomes the
      source of truth and audit tables become derived. Update
      `dcl-mathematics/CLAUDE.md` and the `claim-auditor` agent brief to match
      whichever is chosen.
- [ ] **Gate:** do NOT begin instrumentation / discovery-view coding in
      `dcl-core` until the data contract (R1, R2) is decided — otherwise
      outputs land ad hoc and relocating them is expensive.
- [x] **Route the δp_min finding** to `dcl-delta-p-min` — DONE (PM, 2026-07-29):
      handoff `2026-07-29-dpmin-geometric-fitted-branch-input.md` (equal-weight
      facet selection ⇒ δp_min = 1/(d+1), degenerate in d ⇒ the *fitted* branch).
- [x] **Route referee major M6** to the Paper IV session — DONE (PM, 2026-07-29):
      handoff `2026-07-29-paper04-referee-M6-answered-bell-note.md` (answered in
      Bell note §10.5-10.6, floor-as-admissibility).
- [ ] **Note for later:** `dcl-mathematics/notes/dcl_core_handoff_queue.md` is a
      staging list for a future dcl-core handoff. It is NOT a handoff and must
      not be actioned as one; the author will call for it when coding starts.
