# The vocabulary, in farm terms

A reading aid, not a deliverable — delete it before you submit if you'd rather.
It translates the words the stage uses into what they are on this farm, and says
where to see each one in the workbook. The sentences in the analysis still have
to be yours; this is only so the terms stop getting in the way of writing them.

## What the engagement actually is

A farmer has 64 beds, three crops she can plant, one season, and prices she
cannot change. She wants to know how many beds of each to plant. Stage 1 asked
the question, Stage 2 built the model that answers it, and this stage explains
why the answer is the answer.

The answer is 10 tomatoes / 20 carrots / 30 mesclun, and $42,761.66.

---

## The one word that unlocks the rest

**Marginal** means **the next one**. Not the total, not the average — the next
bed. Every term below is a variation on it.

| The word | What it means | On this farm |
|---|---|---|
| **Marginal cost (MC)** | what the *next* bed costs to plant and work | tomato bed 11 costs $9,390.72 · `Marginal Analysis!G18` |
| **Price** | what a bed brings in | $8,800 a tomato bed, and she cannot change it |
| **Price taker** | a seller too small to move the price — she takes what the market gives | this is the "perfect competition" the engagement is named for; it is an assumption, not a finding |
| **P = MC** | keep planting while the next bed brings in more than it costs; stop where that flips | column `I` for each crop: the row where it goes from + to − |

**Where to read it:** `Marginal Analysis`, column `I` — price minus cost, bed by
bed. Positive means that bed paid for itself. The first negative row is where
the crop stops.

---

## Question 2 words — what stops each crop

| The word | What it means | On this farm |
|---|---|---|
| **Constraint** | a limit you cannot plant past | 20 tomato beds, 20 carrot, 30 mesclun, 64 total, 4 temp workers |
| **Binding** | the limit is what stopped you — you'd do more if you could | the carrot and mesclun bed caps |
| **Slack** | the limit is there but you never reached it | 60 of 64 beds; 5,277 of 6,480 field hours |
| **Shadow price** | what one more unit of a binding limit would earn you | one more carrot bed: **+$352.49**. One more mesclun bed: **+$246.47** |

A shadow price is just *what is this fence costing me* in dollars. It is the
number that turns into advice: it says which ground is worth buying and what to
pay for it.

**A distinction worth making yourself:** the four-worker cap is **tight** — she
hires all four — but its shadow price is **$0**. A fifth worker changes nothing,
because 1,202.78 field hours already go unused. Tight and binding are not the
same thing, and most write-ups miss it.

---

## Question 3 words — the dip

| The word | What it means | On this farm |
|---|---|---|
| **Diminishing returns** | each extra bed takes more work than the one before | hours per bed rise the whole way — 99, 118.80, 141.57 … `column C` |
| **Input price** | what you pay for an hour of work | $34.72 for her own hours, $17.36 for hired |

Marginal cost is those two multiplied together: **hours × the price of an hour.**
That is the whole mechanism of the dip. Hours never stopped rising, but at tomato
bed 6 her own 720 hours run out and the price of the next hour halves — so cost
*falls* $2,754.58 before resuming its climb.

**Where to read it:** columns `D` and `E` for tomatoes. `D` (her hours) goes to
zero between beds 5 and 6; `E` (hired hours) takes over. The colour change in
`tomato-marginal-cost.png` is that same switch.

---

## Question 4 words — growing crops that lose money

This is the one with the most vocabulary and the simplest idea.

| The word | What it means | On this farm |
|---|---|---|
| **Fixed cost** | what you owe whether or not you plant a thing | $20,000 a season |
| **Variable cost** | what you only owe because you planted | labor and fertilizer |
| **Average variable cost (AVC)** | variable cost ÷ beds — what an average bed costs to work | carrots at 20 beds: $1,918.45 |
| **Shutdown rule** | if the price covers AVC, planting beats not planting — even at a loss | carrots: $2,094 covers $1,918.45 |
| **Contribution** | what a bed leaves over toward the fixed cost | $175.55 a carrot bed |

**The idea underneath:** the $20,000 is owed either way, so it has no business in
the decision about what to plant. Run alone, carrots look like a $16,488.92 loss
only because the whole $20,000 is being charged to them. In the mix, the three
crops contribute $62,761.66 between them (`Optimization!G40`), the $20,000 comes
off that, and the farm clears $42,761.66.

It is the same reasoning that keeps an airline flying a half-empty route: the
plane, the crew and the gate are paid for regardless, so a route that covers its
fuel is better than a plane sitting still.

**Where to read it:** AVC is not in the workbook. It is in the table in
`CHECKLIST.md` and plotted in `price-vs-avc.png`.

---

## The test the stage is applying

> "MC rises due to diminishing returns" is a lecture note.
> "Carrot MC reaches $1,688.95 at bed 20, still $405.05 under price — the cap
> binds, not the economics" is analysis.

Same sentence twice. The second one has your cells in it. If a sentence you have
written would be equally true of a farm you have never seen, it is the first kind.
