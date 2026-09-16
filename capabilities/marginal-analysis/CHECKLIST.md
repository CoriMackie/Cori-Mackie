# Stage 1.3 — what's left

Working checklist. Not a deliverable — delete it before you submit if you'd rather.
Last updated 16 September.

Stage 1.2 is closed and merged; its checklist is in the history if you want it
(`git show 750d0ca:capabilities/marginal-analysis/CHECKLIST.md`).

---

## Where the stage stands

Adam's review is [PR #7](https://github.com/CoriMackie/Cori-Mackie/pull/7).
Provisional **74, held, nothing recorded, nothing can go down.** Four things are
open, and he says plainly that what is missing is assembly rather than insight.

| Open | Where it goes |
|---|---|
| The analysis file does not exist | `analysis/perfect-competition-analysis.md` |
| The at-a-loss section is not attempted | inside that file |
| One figure where the stage asks for at least two | done — see below |
| No reflection | `prompt-log.md`, ≤ 300 words |

---

## Done in this session — none of it is the writing

- [x] **Two more figures**, both generated from `model.xlsx` and both rendering on
      GitHub as `.png` with an interactive `.html` beside them:
      `carrot-marginal-cost` and `price-vs-avc`. The stage wants at least two and
      wants each one pointed at in the text — a figure you do not reference earns
      nothing, so if you only use two, delete the third.
- [x] **The numbers you need**, computed from the workbook's own inputs and
      reconciled against it. They are in the next section.
- [x] `capabilities/marginal-analysis/README.md` — the "exercised in" line.
- [x] A `prompt-log` skill so the bookkeeping half of the log stops depending on
      you remembering to write it. It is barred from the reflection.

---

## The numbers, and where they came from

Every figure below was computed from the `Inputs` sheet by the same formulas the
workbook uses, and every one that the workbook also holds agrees with it to the
cent. The ones the workbook does **not** hold are marked *derived* — AVC and the
shadow prices are not in `model.xlsx`, so if you cite them, cite the cells they
are built from rather than a cell that does not exist.

**Shadow prices** — profit at 10/20/30 against profit with one more bed of one
crop, everything else held. *Derived* from `Optimization!B32`.

| One more bed of | Season profit | Change |
|---|---|---|
| carrots (the 21st) | $43,114.16 | **+$352.49** |
| mesclun (the 31st) | $43,008.14 | **+$246.47** |
| tomatoes (the 11th) | $42,170.95 | −$590.72 |

Each of those equals price less the marginal cost of that next bed exactly —
$2,094 − $1,741.51 and $2,700 − $2,453.53 — because the next bed is hired labor
either way. Worth one sentence: it is why the shadow price and the MC schedule
give the same answer here, and it would stop being true if the farmer's own hours
were not already spent.

Note the stage page says "carrot MC reaches $1,742 at bed 20." In your numbering
that is bed **21** — bed 20 costs $1,688.95 (`Marginal Analysis!G52`). Same
figure, different label. Use your own.

**Average variable cost at the planted quantity** — *derived* from
`Marginal Analysis!B7:B87` and the `Inputs` rates. Labor plus fertilizer, divided
by beds; the $20,000 is excluded because it is owed either way.

| | AVC at the planted quantity | Price | Price − AVC |
|---|---|---|---|
| Tomatoes, 10 beds | $6,182.72 | $8,800 | +$2,617.28 |
| Carrots, 20 beds | $1,918.45 | $2,094 | +$175.55 |
| Mesclun, 30 beds | $2,430.74 | $2,700 | +$269.26 |

**Two places the generalization is false in your model, and Adam has already said
these are the version worth writing:**

- Mesclun's AVC is **above** its price at beds 13 and 14 — $2,716.35 and
  $2,702.51 — and comes back under once the wage switch lands. Tomatoes' AVC
  passes $8,800 at bed 16 and never returns.
- So "price exceeds AVC everywhere" is not true here. It is true **where the
  optimum plants**, which is the claim the recommendation actually needs.

**One more the stage page gets wrong for your farm.** It says any single crop run
by itself loses money at every quantity. Two of yours do — carrots lose
$16,488.92 at 20 beds, mesclun $11,922.19 at 30. **Tomatoes alone make $6,172.77
at 10 beds.** The at-a-loss question is a real question about carrots and mesclun
and not about tomatoes, and saying so is the difference between reading your
model and reciting the stage page.

**Already in the memo and still good** — the three crops contribute $62,761.66
together (`Optimization!G40`) against the $20,000, for $42,761.66; 1,202.78 field
hours unused; $20,881.66 of temp capacity paid for and never worked; $67,761.66
if her own hours were treated as sunk.

One thing to decide rather than inherit: AVC above charges the farmer's own hours
at $34.72 as a variable cost. She earns that $25,000 whether or not she plants,
which is the same argument you already make about the fixed cost. Treating it as
variable makes AVC higher and your shutdown claim harder to pass, so the version
you have is the conservative one — but it is a call, and the analysis is the place
to say you made it.

---

## Yours to write — do not hand these to a model

The stage is explicit and so is the order: **write it, commit it, then** ask for
structural editing, apply what you agree with in your own words, commit again, log
the session. The commit is the control. Without it, "I only used it as an editor"
is a claim nobody can check afterwards, including you.

- [ ] **`analysis/perfect-competition-analysis.md`** — one to two pages, the four
      questions: why tomatoes stop at 10, which constraints bind and what relaxing
      one is worth, the dip by mechanism, and the at-a-loss resolution. Much of
      the first three is already written in the decision memo; the job is mostly
      moving it and citing cells. **Nothing in this repo has touched that path
      yet, which is the point — the first commit on it should be yours.**
- [ ] **Close with the hypothesis paragraph.** Four conditions, three survived, one
      fired, and what you had wrong was where the dip happens rather than whether
      it would. That paragraph is already in the memo and Adam called it excellent.
- [ ] **The memo, cut back to half a page.** The plan, the judgment call — which
      ground to buy first and what a bed of it is worth — and one line naming the
      variable your answer is most sensitive to. What is in `perfect-competition-
      decision.md` today is doing both jobs at once.
- [ ] **The reflection, ≤ 300 words.** Never AI-touched. Name something concrete
      you verified and how. You have a real one: the memo claimed every check read
      OK and the sheet said VIOLATED, and you found it by opening the sheet.
- [ ] **Two descriptive commits at least**, and the stage wants them on `main`
      before it counts as submitted.

## One thing to decide before you write

The stage's deliverable table names **`docs/decisions/perfect-competition-memo.md`**.
What is in the repo is `perfect-competition-decision.md`. Adam read it fine at the
current path and did not raise it — but Stage 1 cost you a move to the graded path
once already. Either rename it (`git mv`, and fix the links in the root README,
`analysis/figures/README.md` and the capability README) or leave it and say why in
your PR reply. It is your call, not a cleanup for anyone else to make quietly.

## Reply on PR #7 when you push

Say what you changed and what you pushed back on. Two candidates for the second
kind: tomatoes alone are profitable in your model, and price does not exceed AVC
everywhere in it. Both are you reading your own schedules against a generalization,
which is the thing he has been rewarding all term.
