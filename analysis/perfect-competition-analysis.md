# Perfect Competition — Analysis

**Author:** Cori Mackie
**Capability:** `marginal-analysis` · **Engagement:** `perfect-competition`
**Brief:** [`docs/briefs/perfect-competition-brief.md`](../docs/briefs/perfect-competition-brief.md)
**Model:** [`capabilities/marginal-analysis/model.xlsx`](../capabilities/marginal-analysis/model.xlsx)

---

## Why tomatoes stop at 10 beds

In my analysis the tomatoes stop at 10 beds (`Marginal Analysis!B92`) but actually
stop somewhere between 10 and 11. Any additional beds after that is not worth
planting because of the rise in labor cost. The reason why we stop planting is the
cap for mesclun and carrots for tomatoes it is the labor. Bed 11 costs $9,390.72
(`Marginal Analysis!G18`), and $8,510.72 of that is labor — 90.6% (490.22 temp
hours at `E18`, priced at `Inputs!B43`). Fertilizer is flat at $880 a bed
(`Inputs!B19`), so every dollar of the rise in every MC curve here is labor hours.
Beds 9, 10, 11 go $7,243.78 → $8,248.59 → $9,390.72 (`G16:G18`), and the entire
climb is the escalating hours (`C16:C18`). The climb and the crossing are plotted
in `figures/tomato-marginal-cost.png`.

![Marginal cost of each tomato bed against the fixed $8,800 price, beds 1 to 14. Cost climbs to $8,248.59 at bed 10 and $9,390.72 at bed 11, crossing the price between them.](figures/tomato-marginal-cost.png)

## What stops carrots and mesclun, and what moving it is worth

For the beds of carrot and mesclun it never is in the negative before the caps
(`I33:I52` and `I58:I87`), what stops them is the limit. In the 20th carrot bed the
earned would be $405.05 (`I52`) and the 21st it begins to go down at $352.49 (not
in the workbook — a 21st bed is past the schedule; derived). The 30th mesclun bed
earns $279.90 (`I87`) and the 31st would be $246.47 (derived). Both crops are
making money but the farmer cannot continue due to the fence. One more bed of
carrots in the ground outranks one more bed of mesclun in the ground. $352.49 is
the most that she should pay per season for carrots, per bed. The carrot schedule
and the bed the cap forbids are in `figures/carrot-marginal-cost.png`.

![Marginal cost of each carrot bed against the fixed $2,094 price, beds 1 to 21. The in-plan line never reaches the price; bed 20 costs $1,688.95 and a twenty-first would cost $1,741.51, leaving $352.49 on the table.](figures/carrot-marginal-cost.png)

## Why grow crops that lose money on their own

Average variable cost is every variable dollar a crop spends at that acreage —
labor for its hours, plus fertilizer — divided by the beds planted. It excludes
the $20,000 fixed cost, which is owed whether or not anything is planted. AVC is
not a cell in the workbook: it is built from the labor hours in
`Marginal Analysis!B7:B87` and the rates on `Inputs`.

| At the quantity the plan plants | AVC | Price | Price − AVC |
|---|---|---|---|
| Tomatoes, 10 beds | $6,182.72 | $8,800 | +$2,617.28 |
| Carrots, 20 beds | $1,918.45 | $2,094 | +$175.55 |
| Mesclun, 30 beds | $2,430.74 | $2,700 | +$269.26 |

The three crops contribute $62,761.66 between them (`Optimization!G40`), the
$20,000 comes off that, and the farm clears $42,761.66 (`Optimization!B32`).

Run alone, each crop carries the whole $20,000 by itself:

| Run alone, at its best quantity | Season result |
|---|---|
| Carrots, 20 beds | −$16,488.92 |
| Mesclun, 30 beds | −$11,922.19 |
| Tomatoes, 10 beds | +$6,172.77 |

Price does not cover AVC everywhere in this model. Mesclun's AVC is above its
price at bed 13 ($2,716.35) and bed 14 ($2,702.51); tomatoes' passes $8,800 at
bed 16 ($8,840.90) and does not come back under it.

![Price against average variable cost, one panel per crop. Carrots clear their AVC at every bed; mesclun does not at beds 13 and 14, and tomatoes stop clearing theirs at bed 16.](figures/price-vs-avc.png)
