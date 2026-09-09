# Figures

Charts and visual outputs referred to by findings in `docs/decisions/`.

| Figure | Referred to by |
|---|---|
| `tomato-marginal-cost.png` · `.html` | [`perfect-competition-decision.md`](../../docs/decisions/perfect-competition-decision.md) |

**`tomato-marginal-cost`** — marginal cost of each tomato bed against the
fixed $8,800 price, beds 1 to 14. Each bar is split by what the cost is
made of, so the colour change at bed 6 *is* the finding: the farmer's own
720 hours run out inside bed 5, and everything after is hired labor at
$17.36. That is why marginal cost falls $2,754.58 before resuming its
climb to the crossing between beds 10 and 11.

The `.png` is the version the decision document embeds. The `.html` is the
same chart with hover figures, a table of all twenty beds, and light/dark
themes; open it in a browser. Both are generated from
`capabilities/marginal-analysis/model.xlsx` and carry no data of their own.
