---
name: prompt-log
description: Append a factual entry to prompt-log.md after a session that changed a file in this repository. Use at the end of any session that produced a commit, a file, a figure or a computed figure for graded work. Records what was asked and what was produced — never the reflection, never what the model got wrong, never how the work was verified.
---

# prompt-log

`prompt-log.md` at the repository root is a curated record of AI sessions that
shaped something here. It accretes across engagements; it does not start fresh.

## When to append

After any session where you helped with graded work and a file in this
repository changed. Not every exchange — a session that answered a question and
touched nothing does not belong in the log.

## What to write

One row in the table, in the existing format:

| Date | Session | Outcome |

- **Date** — today, `YYYY-MM-DD`.
- **Session** — a short name for what the session was about.
- **Outcome** — what was asked for and what was produced. Facts, and the files
  that changed. Where the numbers came from and whether they reconcile against
  the workbook is a fact and belongs here. Say plainly which parts were the
  model's and which were Cori's.

Keep it to what happened. If a session produced nothing worth keeping, say so
in the reply and do not append a row — a log that records everything is a
transcript, and a transcript shows only that someone was present.

## What you must never write

Three things in this log are Cori's alone, and an entry that supplies them is
worse than no entry:

- **The reflection.** Never drafted, never edited, never suggested.
- **Where AI was wrong.** A model auditing its own errors has an obvious
  conflict of interest.
- **How she verified.** "It seemed right" is not verification and neither is
  anything a model writes on her behalf.

Leave them out entirely rather than leaving a placeholder for her to fill.

## Also hers

The analysis and the memo are written by her and committed before a model sees
them. A model may act as a structural editor on a draft already in the history —
this paragraph belongs earlier, this claim is unsupported, this recommendation
does not follow from this evidence — and never as the writer. Do not create or
draft `analysis/perfect-competition-analysis.md` or the decision memo.
