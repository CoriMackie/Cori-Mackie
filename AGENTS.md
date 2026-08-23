# AGENTS.md

This is the canonical file for how AI assistants (Claude, or any other
agent) should work in this repository. Other agent-specific files (e.g.
`CLAUDE.md`) point back here rather than duplicating these conventions.

## Repository Structure

```
README.md            who I am + the index of engagements
RESUME.md            resume
AGENTS.md            this file — AI conventions
CLAUDE.md            one line pointing back to AGENTS.md
prompt-log.md        running record of AI sessions that mattered
.gitignore           what must never enter the history
.claude/skills/       personal sandbox
capabilities/         one folder per capability
  <capability>/
    README.md · spec.md · model.xlsx
docs/
  briefs/            BEFORE the work: scope + hypothesis
  decisions/         AFTER the work: the recommendation
data/                 sourced inputs, with provenance
analysis/figures/     the findings, and the charts they refer to
```

## Conventions

-   **Briefs before decisions.** Start new work with a brief in
    `docs/briefs/` (scope + hypothesis) before doing the analysis. Record
    the outcome in `docs/decisions/` once the work is done.
-   **Provenance in `data/`.** Every file under `data/` should be
    traceable to a source (where it came from, when it was pulled). Note
    this in a README alongside the data or in the commit message.
-   **One folder per capability.** Each folder under `capabilities/`
    is self-contained: a `README.md` explaining what it does, a `spec.md`
    describing the approach, and any supporting model/workbook.
-   **Log AI sessions that mattered.** Add an entry to `prompt-log.md`
    for sessions that produced a meaningful change — not every
    back-and-forth, but anything that shaped a file in this repo.
-   **Keep secrets out.** Nothing that belongs in `.gitignore` should
    ever be committed, even temporarily.

## Commit Style

Short, descriptive commit messages that explain why a change was made,
not just what changed.
