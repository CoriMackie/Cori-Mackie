# Figures

Charts and visual outputs referred to by the analysis in `analysis/` and the
findings in `docs/decisions/`.

| Figure | Referred to by |
|---|---|
| `tomato-marginal-cost.png` · `.html` | [`perfect-competition-decision.md`](../../docs/decisions/perfect-competition-decision.md) · [`perfect-competition-analysis.md`](../perfect-competition-analysis.md) |
| `carrot-marginal-cost.png` · `.html` | [`perfect-competition-analysis.md`](../perfect-competition-analysis.md) |

**`tomato-marginal-cost`** — marginal cost of each tomato bed against the
fixed $8,800 price, beds 1 to 14. Each bar is split by what the cost is
made of, so the colour change at bed 6 *is* the finding: the farmer's own
720 hours run out inside bed 5, and everything after is hired labor at
$17.36. That is why marginal cost falls $2,754.58 before resuming its
climb to the crossing between beds 10 and 11.

**`carrot-marginal-cost`** — marginal cost of each carrot bed against the
fixed $2,094 price, all twenty beds, standalone, with average variable cost
drawn as a dashed line. Marginal cost passes the price between beds 10 and
11, then falls $881.20 at bed 17 when the farmer's hours run out, and beds
17 to 20 come back under the price. Average variable cost stays under the
price at every bed, which is why carrots are worth growing even though a
carrot-only season loses money.

Each `.png` is the version the documents embed. Each `.html` is the
same chart with hover figures, a table of all the beds, and light/dark
themes; open it in a browser. Both are generated from
`capabilities/marginal-analysis/model.xlsx` and carry no data of their own.
