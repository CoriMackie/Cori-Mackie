# Stage 1.3 — what's left

Four things. Everything else for this stage is done and pushed.

If a term is in the way rather than the idea, [`VOCABULARY.md`](VOCABULARY.md) translates them into farm terms and says which column to read each one in.

Order matters and it is the graded part: **write it, commit it, then** hand it to
a model for structure only, apply what you agree with in your own words, commit
again. The two commits are what make "I only used it as an editor" checkable.

---

## 1 · `analysis/perfect-competition-analysis.md` — 1 to 2 pages

**Three of six done and pushed** (16 September). The file exists, your prose is in
it under your own commits, and both new figures are referenced.

You are not computing anything here — the model already answered. Each bullet is
a column to read and a question to answer out loud in your own words.

- [x] **Why tomatoes stop at 10** — written, cited to `G16:G18` and `C16:C18`,
      `tomato-marginal-cost.png` referenced.

- [x] **Which constraints bind, and what relaxing one is worth** — written for
      both crops, $352.49 and $246.47 both on the page and marked as derived,
      `carrot-marginal-cost.png` referenced.

- [ ] **Name the slack.** ← **start here when you come back.** The shortest one:
      four facts and one distinction, no argument to build.

      | | Cell | |
      |---|---|---|
      | Beds planted | `B9` | 60 of 64 |
      | Beds idle | `B10` | 4 |
      | Field hours needed | `B17` | 5,277.22 of 6,480 |
      | Hours never worked | — | 1,202.78 |
      | Temp workers hired | `B20` | 4, of a maximum of 4 |

      **The distinction:** the stage page says the four-worker cap "never binds."
      Not quite — she hires all four, so it is **tight**. But its shadow price is
      **$0**: a fifth worker adds nothing when 1,202.78 hours already go unworked.
      Tight says where you are; binding says whether it costs you.

      **The other half**, already in your memo: four workers make 5,760 hours
      available and the plan uses 4,557 — **$20,881.66** of capacity paid for and
      never worked. Labor is not scarce here, it is oversupplied.

      *Answer* what the farm never ran out of, and what that tells her not to buy.

- [ ] **The dip, by mechanism.**
      *Open* `Marginal Analysis`, tomato columns `D` and `E`, rows 12–13.
      *You'll see* `D` (her own hours) go to zero and `E` (hired) take over —
      and `G` fall $2,754.58 while column `C` keeps rising.
      *Answer* why cost fell when the work per bed never stopped growing.
      **Already written** in the memo, including the line Adam called the
      sharpest reading anyone produced.

- [x] **Why grow crops that lose money alone** — written, with the AVC tables,
      `price-vs-avc.png`, and the scoping paragraph saying where the rule stops
      holding. **This was the largest gap in Adam's review.**

- [ ] **Close with the hypothesis paragraph.**
      *Open* `docs/briefs/perfect-competition-brief.md`, the four falsification
      conditions, next to what the model did.
      *Answer* which held and which fired, and that what you had wrong was
      *where* the dip is. **Already written** in the memo.

Both remaining sections are already written in `perfect-competition-decision.md` —
the dip under "How the hypothesis held up," and the hypothesis paragraph itself.
The job there is moving them across and citing cells.

**Still open in the file:** two grammar knots you flagged yourself — "with the
rule that price always cover AVC would be making a loss" is tangled around the
middle — plus the figure captions, if you want them.

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
