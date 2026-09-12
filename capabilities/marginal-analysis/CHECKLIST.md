# Stage 1.2 — what's left

Working checklist. Not a deliverable — delete it before you submit if you'd rather.
Due 11 September. Last updated 12 September.

---

## Done

- [x] `spec.md` committed, and committed **before** the workbook (the order is graded)
- [x] All 17 open questions in the spec closed — no TODOs left except the DRAFT
      header and the post-build audit entries
- [x] First workbook built, audited, and its defects traced back to spec lines
- [x] 9 commits on the branch

Nothing is on `main`. Nothing has gone to Adam. No pull request exists.

---

## In flight

- [x] **A fresh session is rebuilding the workbook** from the corrected spec.
      It will push to this branch on its own. When you come back, check whether
      `model.xlsx` has a new commit, and **read its list of guesses and undefined
      terms first** — that list is worth more than the spreadsheet. Each item on it
      is a spec defect with your name on it.

---

## Needs Excel on your desktop — only you can do these

- [x] **Run Solver from 0/0/0.** Maximize season profit, changing the three bed
      counts. Constraints: bed caps, 64 total, temp workers ≤ 4, integers.
      GRG Nonlinear. Recorded at `Validation!B31`: **$42,761.66**.
- [x] **Run Solver again from 15/0/0** — 20/0/0 is infeasible and stranded, so the
      second start was moved to the nearest tomato-only start that fits the
      four-worker cap. Recorded at `Validation!B32`: **$42,761.66**. V3 reads OK.
- [x] **V2 cross-check.** The Farm Profit Lab is out of reach, so V2 became a hand
      computation of the same figure — the marginal cost of tomato bed 10, which
      this model returns as **$8,249**. Recorded at `Validation!B25`: $8,248.59.
      V2 reads OK. The substitution is recorded in `spec.md`: a hand computation
      works the same design the model does, so it is a weaker check than an
      outside implementation would have been.

---

## Then, back here or on your own

- [ ] **Audit findings** appended to `spec.md` — V2 through V5. V1 is already
      written. Four defects from the first build are candidates:
      the Plant/Stop column reading Plant → Stop → Plant again for carrots and
      mesclun; no validation region built; `BLENDED_RATE` computed and dropped;
      decision variables unnamed. Each one names what it would have caught.
- [ ] **The dip** — reported, not explained. `OUT_TOM_DIP_BED` and
      `OUT_TOM_DIP_SIZE` are already specified as outputs.
- [ ] **The voice pass** — see the section at the bottom of this file. Two of the
      five argument passages are done.
- [ ] **Drop the DRAFT header** at the top of `spec.md` once the TODOs are gone.

---

## The three small files

- [ ] **`capabilities/marginal-analysis/README.md`** — still 1 byte. Needs what the
      capability is and an "exercised in:" line.
- [ ] **`prompt-log.md`** — a draft entry is written; rewrite in your words.
      Watch the line claiming the voice pass is done — don't let the log get ahead
      of the work.
- [ ] **Root `README.md`** — add this engagement under "Engagements". It still
      says none are logged.

---

## Before you submit

- [ ] Merge the branch to `main`, or move the files there. **Nothing is submitted
      until it's visible at `capabilities/marginal-analysis/` on the main branch.**
- [ ] Open github.com in a browser and confirm it with your own eyes.
- [ ] Reply on PR #2 with what you changed and what you pushed back on.
- [ ] Consider re-authoring the commits under your name — they currently show
      `Claude` as author.

---

## One correction owed to your brief

The brief's labor table says "Labor, first bed | 2.50 hrs/wk × 36 wks = 90 hrs" and
says each new bed costs "about 10% more labor than the one before it." The stage
page settles both: one tomato bed needs 1 × 2.5 × 36 × 1.10 = 99 hours, and the
growth factor raises the labor requirement of *every* bed rather than compounding
bed to bed. 90 is the base rate before escalation, so the column label is wrong,
not the number — and the brief's own $9,390 figure already uses the right formula.

Fixing a mislabeled input is not revising your hypothesis to match the model. Say
so in your PR reply so it reads as a correction rather than a quiet edit.

---

## Voice pass — where you left off

The spec's tables and formulas don't need your voice. The prose does. There are 18
prose passages; five of them make an argument, and those are the ones a reader
notices.

**The trick that works:** don't rewrite the paragraph. Answer the question out
loud, the way you'd answer a person. Then it comes out in your words.

- [x] **1. The crossing rule** — done, committed `da6c8e9`
- [x] **2. Why the blended rate for the P&L** — done, committed `b340844`
- [x] **3. Two labor rates** — done, committed `2d0d1a1`
- [x] **4. Fixed cost** — reviewed and kept as written; it states a definition
      rather than an argument, and it records the call you made
- [x] **5. The farmer's hours** — done. "They do not stop anything, it just costs
      more."

All five argument passages are done. The remaining thirteen are flat statements of
rule rather than argument — lower stakes, and optional if time is short.

## Held for Stage 3 — do not resolve

Why marginal cost falls and then rises again. You already predicted it in the
brief's fourth falsification condition, before building anything. Both Adam and the
stage page say to leave it alone until Stage 3. Report where it happens and how
deep; don't explain it.

Worth doing while it's fresh, per Adam's own suggestion: write down what you expect
the shape to be — where the dip starts, how deep, all three crops or just tomatoes
— and put it in the prompt log. Then the model either confirms you or doesn't.
