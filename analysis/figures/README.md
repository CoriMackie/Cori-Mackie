# Figures

Charts and visual outputs referred to by findings in `analysis/` and
`docs/decisions/`. All three are generated from
`capabilities/marginal-analysis/model.xlsx` and carry no data of their own.

Each figure ships as a `.png` — the version a Markdown file embeds, and the one
that renders on the GitHub page — and a `.html` beside it, the same chart with
figures on hover, the full schedule as a table, and light and dark themes. Open
the `.html` in a browser.

| Figure | Referred to by |
|---|---|
| `tomato-marginal-cost` | [`perfect-competition-decision.md`](../../docs/decisions/perfect-competition-decision.md) |
| `carrot-marginal-cost` | Stage 1.3 analysis |
| `price-vs-avc` | Stage 1.3 analysis |

**`tomato-marginal-cost`** — marginal cost of each tomato bed against the
fixed $8,800 price, beds 1 to 14. Each bar is split by what the cost is
made of, so the colour change at bed 6 *is* the finding: the farmer's own
720 hours run out inside bed 5, and everything after is hired labor at
$17.36. That is why marginal cost falls $2,754.58 before resuming its
climb to the crossing between beds 10 and 11.

**`carrot-marginal-cost`** — the same crop costed two ways, beds 1 to 21. The
standalone schedule from `Marginal Analysis!A33:J52` gives carrots the farmer's
whole 720 hours and crosses the $2,094 price at bed 11; in the recommended plan
tomatoes and mesclun have absorbed those hours first, so every carrot hour is
hired at $17.36 and the line never reaches the price. Bed 20 costs $1,688.95.
Bed 21 — which the case forbids — would cost $1,741.51 and add $352.49, so the
chart prices the constraint as well as showing that it binds.

**`price-vs-avc`** — three panels, one crop at a time, each asking the shutdown
question: does the price of a bed cover what a bed costs to work, before any of
the $20,000 fixed cost? Shaded where it does not. Carrots clear their AVC at
every bed; mesclun does not at beds 13 and 14, and tomatoes stop clearing theirs
at bed 16 — so the textbook line that price exceeds AVC everywhere is false in
this model, and true where the optimum plants. Average variable cost is not a
cell in the workbook: it is built here from the labor hours in
`Marginal Analysis!B7:B87` and the rates on `Inputs`.
