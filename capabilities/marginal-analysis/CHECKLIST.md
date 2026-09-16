# Stage 1.3 — what's left

Four things. Everything else for this stage is done and pushed.

Order matters and it is the graded part: **write it, commit it, then** hand it to
a model for structure only, apply what you agree with in your own words, commit
again. The two commits are what make "I only used it as an editor" checkable.

---

## 1 · `analysis/perfect-competition-analysis.md` — 1 to 2 pages

Does not exist yet. Nothing in this repo has touched that path, deliberately.

- [ ] **Why tomatoes stop at 10.** Bed 10 costs $8,248.59, bed 11 costs
      $9,390.72, the $8,800 price sits between them. `Marginal Analysis!G17:G18`.
      Point at `tomato-marginal-cost.png`.
- [ ] **Which constraints bind, and what relaxing one is worth.** Carrots and
      mesclun stop at their caps with margin left — $1,688.95 against $2,094
      (`G52`), $2,420.10 against $2,700 (`G87`). One more bed is worth **$352.49**
      and **$246.47**. Buy carrot ground first. Point at `carrot-marginal-cost.png`.
- [ ] **Name the slack.** 60 of 64 beds. And the four-worker cap is *tight* —
      you hire all four — but worth **$0**: a fifth worker changes nothing,
      because 1,202.78 field hours go unused. Tight and binding are not the
      same thing, and that sentence is yours to make.
- [ ] **The dip, by mechanism.** Bed 6, $2,754.58, her 720 hours run out and the
      marginal hour goes from $34.72 to $17.36. `B95:B96`. **Already written** —
      "How the hypothesis held up" in the memo, including the part Adam called the
      sharpest reading anyone produced: the break sits upstream of the margin.
- [ ] **Why grow crops that lose money alone.** The table below. Point at
      `price-vs-avc.png`.
- [ ] **Close with the hypothesis paragraph.** Four conditions, three survived,
      one fired, and what you had wrong was *where* the dip is. **Already
      written** in the memo.

Three of those six are already drafted in `perfect-competition-decision.md`. The
job is mostly moving them and citing cells.

## 2 · Cut the memo back to half a page

- [ ] The plan — 10/20/30, one sentence a non-economist accepts.
- [ ] The judgment call — both caps bind, carrot ground is worth $352.49 a bed
      and mesclun $246.47, so buy carrot ground first.
- [ ] What would change your answer — one line, one variable.

## 3 · The reflection — ≤ 300 words, in `prompt-log.md`

- [ ] **Never AI-touched.** You have a concrete one: the memo claimed every check
      read OK, the sheet read VIOLATED, and you found it by opening the sheet.

## 4 · Ship it

- [ ] Two descriptive commits, merged to `main` — it is not submitted until it is
      visible on `main`.
- [ ] Reply on [PR #7](https://github.com/CoriMackie/Cori-Mackie/pull/7).

---

## The numbers

AVC and the shadow prices are **not cells in the workbook** — they are built from
`Marginal Analysis!B7:B87` and the `Inputs` rates. Cite what they are built from.
Everything the workbook does hold agrees with it to the cent.

| At the planted quantity | AVC | Price | Covered by |
|---|---|---|---|
| Tomatoes, 10 beds | $6,182.72 | $8,800 | +$2,617.28 |
| Carrots, 20 beds | $1,918.45 | $2,094 | +$175.55 |
| Mesclun, 30 beds | $2,430.74 | $2,700 | +$269.26 |

Together the three contribute $62,761.66 (`Optimization!G40`) against the
$20,000 — which is the whole at-a-loss answer.

**Two places to disagree with the stage page, using your own schedules:**

1. It says price exceeds AVC everywhere. Not here — mesclun's AVC is **above**
   price at beds 13 and 14 ($2,716.35, $2,702.51) and tomatoes' from bed 16.
   True where the optimum plants; false elsewhere.
2. It says any crop run alone loses money at every quantity. Carrots lose
   $16,488.92 and mesclun $11,922.19 — but **tomatoes alone make $6,172.77**.
   The paradox is about two crops, not three.

Both belong in your PR reply.

## Two calls only you can make

- **The memo's path.** The deliverable table says
  `docs/decisions/perfect-competition-memo.md`; yours is
  `perfect-competition-decision.md`. Adam read it fine where it is. Rename it
  (and fix three links) or say why not.
- **The farmer's own hours in AVC.** Charged at $34.72 above, which makes AVC
  higher and your shutdown claim harder to pass — the conservative choice. She
  earns that $25,000 either way, which is the same argument you make about fixed
  cost. Say which you chose.
