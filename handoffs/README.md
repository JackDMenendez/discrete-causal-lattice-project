# Handoffs

Formal handoff records between parallel Claude sessions in the A=1 DCL
program. One file per handoff, `YYYY-MM-DD-slug.md`, scaffolded by the
`/handoff` skill.

A handoff replaces lossy chat-paste status reports: it is committed (durable
+ diffable), carries required frontmatter (`from/to/repo/branch/commits/
status/semver/flags/decisions`), and ends with an explicit **Consumer
actions** list so the receiving session acts rather than infers.

- **Produce** (focused session, after a unit of work): `/handoff`.
- **Consume** (PM session): `/handoff read` → work the actions, then flip
  `status: open → consumed`.

`flags` must never be empty when an unverified convention, sign choice, or
deliberate deviation exists — that buried-risk case is the reason this
convention exists.
