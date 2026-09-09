# Farm Labor & Profit Model — Working Specification

**Author:** Cori Mackie
**Capability:** `marginal-analysis` · **Engagement:** `perfect-competition`
**Status:** DRAFT — open items marked TODO. Remove every TODO before committing.

---

## 1. Inputs

The model uses farm-wide assumptions and crop-specific assumptions. Every input
below is a named range so that formulas can be read without reference to cell
addresses.

### Farm-wide

| Name | Value | Unit | Source |
|---|---|---|---|
| `WEEKS`            | 36    | weeks                       | Case scenario — season length |
| `PERM_HOURS`       | 720   | hours per season            | Case scenario — half the farmer's season |
| `FARMER_SALARY`    | 50000 | $ per season                | Case scenario |
| `TEMP_WORKER_PAY`  | 25000 | $ per worker per season     | Case scenario |
| `TEMP_WORKER_HRS`  | 1440  | hours per worker per season | Case scenario |
| `TEMP_WORKERS_MAX` | 4     | workers                     | Case scenario constraint |
| `FIXED_COST`       | 20000 | $ per season                | Case scenario |
| `FARM_BED_CAP`     | 64    | beds                        | Case scenario — 16 beds × 4 plots |

### Per crop

| Name | Value | Unit | Source |
|---|---|---|---|
| `TOM_HPB`   | 2.5    | hours per week per bed | Case table |
| `TOM_DIM`   | 0.10   | fraction, per bed      | Case table |
| `TOM_FERT`  | 880    | $ per bed              | Case table |
| `TOM_PRICE` | 8800   | $ per bed              | Case table |
| `TOM_CAP`   | 20     | beds                   | Case table |
| `CAR_HPB`   | 5/6    | hours per week per bed | The case shows 0.833. That figure is rounded. Use 5/6. |
| `CAR_DIM`   | 0.025  | fraction, per bed      | Case table |
| `CAR_FERT`  | 440    | $ per bed              | Case table |
| `CAR_PRICE` | 2094   | $ per bed              | Case table |
| `CAR_CAP`   | 20     | beds                   | Case table |
| `MES_HPB`   | 1.25   | hours per week per bed | Case table |
| `MES_DIM`   | 0.0125 | fraction, per bed      | Case table |
| `MES_FERT`  | 880    | $ per bed              | Case table |
| `MES_PRICE` | 2700   | $ per bed              | Case table |
| `MES_CAP`   | 30     | beds                   | Case table |

### Decision variables

The three bed counts are the only cells the optimizer changes. They are named
ranges like every other input, and they are constrained to whole numbers — a bed
is planted or it is not.

| Name | Unit | Bounds |
|---|---|---|
| `TOM_BEDS` | beds, integer | 0 to `TOM_CAP` |
| `CAR_BEDS` | beds, integer | 0 to `CAR_CAP` |
| `MES_BEDS` | beds, integer | 0 to `MES_CAP` |

### Not inputs — derived in §3

`PERM_RATE` and `TEMP_RATE` are computed from the values above and must never be
entered as constants.

---

## Conventions

Decisions the case does not state, settled here so the builder does not guess.

**1. Carrot labor.** The case shows 0.833. That figure is rounded. Use 5/6.

**2. The farmer's salary.** Only the field half — `PERM_RATE` × 720 hours — is a
cost in the model. The other $25,000 is used for costs not related to the labor
of farming, so it is not charged against the planting decision.

**3. Temporary labor.** Temps are charged per hour worked at `TEMP_RATE`, not per
whole seasonal contract. Hourly costs $79,118 at the optimum; charging four whole
contracts costs $100,000 and misses the check figure.

**4. Rounded figures.** The exact quotients govern, not the printed $34.72 and
$17.36. `PERM_RATE` and `TEMP_RATE` are derived at full precision and are never
entered as constants. Typing the printed values returns a season profit of
$42,768 against a check figure of $42,762.

**5. Standalone schedules.** Each crop's marginal-cost schedule draws on the full
720 permanent hours by itself. The pool is not divided across crops. This is what
puts the standalone crossings at 10, 10 and 6 beds.

---

## 2. Structure

The workbook should contain four main areas:

- **Inputs** — farm and crop assumptions
- **Cost / Marginal Analysis** — labor, costs, MC, and P vs. MC
- **Optimization** — best combination of the three crops
- **Validation** — checks that calculations and Solver results are correct

The economic principle behind the marginal analysis is P ≈ MC: continue adding
production while the revenue from the next bed justifies its marginal cost.

The Cost / Marginal Analysis area holds **three separate schedules, one per crop**
— not one combined schedule. Each runs from q = 0 to that crop's bed cap, and each
is built as though that crop were the only thing planted, per convention 5. A
single blended schedule cannot produce a per-crop crossing point and is not what
this specifies.

Every check cell in the Validation area displays `OK` or `VIOLATED`. No other
wording, so a failed check is visible at a glance rather than read for.

### Naming

The crop-prefixed names in §1 are the only names. `TOM_HPB`, `TOM_DIM`,
`TOM_PRICE` and their carrot and mesclun equivalents are what formulas reference;
the generic forms used in the logic below (`HRS_PER_BED`, `DIM_PCT`,
`PRICE_PER_BED`, `BEDS`) are shorthand for "the value for the crop this schedule
is about" and are never named ranges themselves.

---

## 3. Calculation Logic

The calculations should flow in this order.

**A. Labor required for each crop**

    LABOR_HRS(q) = q × HRS_PER_WEEK_PER_BED × WEEKS × (1 + DIM_PCT)^q

The exponential term captures the case's diminishing returns.

**B. Total farm labor**

    TOTAL_LABOR = TOMATO_LABOR + CARROT_LABOR + MESCLUN_LABOR
    PERM_HOURS_USED = MIN(TOTAL_LABOR, PERM_HOURS)
    TEMP_HOURS      = MAX(0, TOTAL_LABOR − PERM_HOURS)

The farmer's hours are used first. Any labor beyond them is temporary labor.

**C. Labor cost**

    PERM_RATE       = FARMER_SALARY / 2 / PERM_HOURS
    TEMP_RATE       = TEMP_WORKER_PAY / TEMP_WORKER_HRS
    PERM_COST       = PERM_HOURS_USED × PERM_RATE
    TEMP_COST       = TEMP_HOURS × TEMP_RATE
    TOTAL_LABOR_COST = PERM_COST + TEMP_COST
    BLENDED_RATE     = TOTAL_LABOR_COST / TOTAL_LABOR_HOURS

**D. Revenue and fertilizer**, per crop

    REVENUE   = BEDS × PRICE_PER_BED
    FERT_COST = BEDS × FERT_PER_BED

**E. Profit**

    VARIABLE_COSTS = TOTAL_LABOR_COST + FERT_COST
    SEASON_PROFIT  = TOTAL_REVENUE − VARIABLE_COSTS − FIXED_COST

**F. Marginal cost / P ≈ MC**

    MC(q) = TOTAL_COST(q) − TOTAL_COST(q−1)

Marginal cost is calculated, not assumed to increase continuously.

`MC(q)` is per crop, not farm-wide. It is the labor cost of that crop's qth bed
plus the fertilizer for one bed. It excludes `FIXED_COST`, which does not change
with the number of beds and so cannot belong in the cost of the next one. The
farm-level `TOTAL_COST` in §E is a different quantity and is not what this uses.

**The split inside a single bed.** §B applies "farmer first" to the farm total.
The marginal-cost schedules apply the same rule one bed at a time, to that bed's
incremental hours:

    MARGINAL_HRS(q)  = LABOR_HRS(q) − LABOR_HRS(q−1)
    PERM_HRS(q)      = MAX(0, MIN(MARGINAL_HRS(q), PERM_HOURS − LABOR_HRS(q−1)))
    TEMP_HRS(q)      = MARGINAL_HRS(q) − PERM_HRS(q)
    MC(q)            = PERM_HRS(q) × PERM_RATE + TEMP_HRS(q) × TEMP_RATE + FERT

A bed can therefore be split across both rates. Tomato bed 5 takes 192.92 of the
farmer's remaining hours and 4.73 temporary hours, because the permanent pool runs
out partway through it.

This rule is not optional. Pricing the schedules at the blended rate instead moves
the tomato crossing from 10 beds to 9 and fails the acceptance criteria.

**H. Per-crop P&L — what `BLENDED_RATE` is for**

The workbook reports a profit and loss line for each crop. Labor is allocated to
crops at the blended rate:

    CROP_LABOR_COST  = CROP_HOURS × BLENDED_RATE
    CROP_PROFIT      = CROP_REVENUE − CROP_FERT_COST − CROP_LABOR_COST

The blended rate works in this situation, and not the sequential one, for the P&L.
It is because the permanent versus temporary labor split is about the farm and not
the crop. Charging a crop the temporary rate because the farmer's hours ran out
would price the same hour differently depending on the order it happened in.

Because `BLENDED_RATE` is total labor dollars divided by total labor hours, the
three crop labor costs add back to `TOTAL_LABOR_COST` exactly. The per-crop P&L
reconciles to the season P&L with nothing left over.

`FIXED_COST` is not allocated across crops. It does not vary with what is planted,
which is the same reason `MC(q)` excludes it. So the three crop profits less
`FIXED_COST` equal `SEASON_PROFIT`.

**The two rules, and where each applies.** The marginal-cost schedules in §F use
two different rates, the farmer's hours first and then the temporary workers'
hours. They answer what each bed costs as it is planted. The per-crop P&L uses the
blended rate because it answers what each crop costs against the farm-level total.
Same hours, different purposes, two rates.


**G. Temporary workers**

    TEMP_WORKERS = ROUNDUP(TEMP_HOURS / TEMP_WORKER_HRS, 0)

The constraint is on whole workers, not on hours: `TEMP_WORKERS ≤ TEMP_WORKERS_MAX`.
Temps are hired by the season, so a worker needed for one hour is a worker hired.

---

## 4. Validation

I will test the model rather than accept the generated spreadsheet.

**V1 — Hand check, one tomato bed.**

    1 × 2.5 × 36 × 1.10 = 99 hours

**V2 — Cross-check** at least one intermediate MC against the Farm Profit Lab.

**V3 — Solver from two starting points**, 0/0/0 and 20/0/0, to determine whether
both produce the same solution.

**V4 — Acceptance criteria.** The finished model must reproduce:

| Check | Value |
|---|---|
| Optimal mix | 10 tomatoes · 20 carrots · 30 mesclun |
| Season profit | $42,762 |
| Standalone P ≈ MC points | Tomatoes ~10 · Carrots ~10 · Mesclun ~6 |

**V5 — Integrity.** Calculated cells contain formulas, no spreadsheet errors, all
constraints satisfied.

**V2 detail.** The cross-check is taken from the middle of a schedule rather than
from either end, because an endpoint can agree by accident where the interior
cannot. The comparison is the marginal cost of tomato bed 10, which this model
returns as $8,249. The Farm Profit Lab's figure for the same bed must agree to
the dollar.

**V3 detail.** Both Solver runs have to agree on season profit. They do not have
to arrive by the same route. If the profit differs between the two starting
points, one of them found a local optimum and the result is not the answer.

Note that 20/0/0 is an infeasible starting point: 20 tomato beds needs 12,109
hours, about eight temp workers against a cap of four. It is run anyway — the
point of the second start is to see whether Solver lands somewhere different, and
starting outside the feasible region is a harder test than starting inside it.

**Tolerance.** Season profit must round to $42,762 and must not exceed it. The
standalone crossing points are exact bed counts, not approximate: 10, 10 and 6.
Wherever this document says P ≈ MC it means the last bed whose marginal cost is
at or below price, which is a whole bed and carries no tolerance.

**V6 — Solver.** The optimization runs GRG Nonlinear with integer decisions,
maximizing season profit over the three bed counts.

**The constraints.** These are what V5 means by "all constraints satisfied," and
each one gets its own check cell:

| Constraint | Rule |
|---|---|
| Tomato bed cap | `TOM_BEDS ≤ TOM_CAP` (20) |
| Carrot bed cap | `CAR_BEDS ≤ CAR_CAP` (20) |
| Mesclun bed cap | `MES_BEDS ≤ MES_CAP` (30) |
| Farm bed cap | `TOM_BEDS + CAR_BEDS + MES_BEDS ≤ FARM_BED_CAP` (64) |
| Temporary workers | `TEMP_WORKERS ≤ TEMP_WORKERS_MAX` (4) |
| Whole beds | all three bed counts are integers |
| Non-negative | all three bed counts are ≥ 0 |

The farmer's own 720 hours are not a constraint. She works them or she does not;
what is beyond them is hired.

**V7 — The crossing rule.** Marginal cost does not always move in one direction. A
schedule can go above price and later fall below it. The **first** bed where
marginal cost exceeds the price is where we stop. At that point we report the bed
before it, whatever marginal cost does further down. Carrots stop at 10, although
beds 17 through 20 come back under price, and mesclun stops at 6 for the same
reason.

The decision column must implement this rule rather than labelling each bed
independently. A per-bed label produces Plant, then Stop, then Plant again, which
reports no crossing point at all.

This rule governs the three standalone schedules. It is not the optimization: the
optimizer works on total season profit and may land on bed counts above a crop's
standalone crossing. Both results are reported, and they are not the same
question.

---

## 5. Outputs

Each of these is a named, labelled cell in the workbook, so §4 can refer to it by
name rather than by description.

**The decision**

| Output | What it reports |
|---|---|
| `OUT_TOM_BEDS` · `OUT_CAR_BEDS` · `OUT_MES_BEDS` | Optimal beds, per crop |
| `OUT_BEDS_USED` | Total beds planted |
| `OUT_BEDS_IDLE` | `FARM_BED_CAP` − `OUT_BEDS_USED` |

**Labor**

| Output | What it reports |
|---|---|
| `OUT_TOTAL_HOURS` | Total field hours required |
| `OUT_PERM_HOURS` | Hours worked by the farmer |
| `OUT_TEMP_HOURS` | Hours worked by temporary labor |
| `OUT_TEMP_WORKERS` | Temporary workers required |
| `OUT_BLENDED_RATE` | Total labor dollars ÷ total labor hours |

**Money**

| Output | What it reports |
|---|---|
| `OUT_REVENUE` | Total season revenue |
| `OUT_LABOR_COST` · `OUT_FERT_COST` · `OUT_FIXED_COST` | Costs, by kind |
| `OUT_TOTAL_COST` | All three added |
| `OUT_SEASON_PROFIT` | Revenue less total cost — the objective |

**Per-crop P&L**

One row per crop, labor allocated at `OUT_BLENDED_RATE` per §3H.

| Output | What it reports |
|---|---|
| `OUT_CROP_REVENUE` | Revenue, per crop |
| `OUT_CROP_FERT_COST` | Fertilizer cost, per crop |
| `OUT_CROP_LABOR_COST` | Labor cost, per crop, at the blended rate |
| `OUT_CROP_PROFIT` | Crop profit before fixed costs |
| `OUT_PNL_RECONCILES` | `OK` when the three crop labor costs sum to `OUT_LABOR_COST`, and the three crop profits less `OUT_FIXED_COST` equal `OUT_SEASON_PROFIT` |

**Marginal analysis**

| Output | What it reports |
|---|---|
| `OUT_MC_SCHEDULE` | Marginal cost by crop and bed, all three schedules |
| `OUT_P_MINUS_MC` | Price less marginal cost, bed by bed |
| `OUT_CROSSING_TOM` · `OUT_CROSSING_CAR` · `OUT_CROSSING_MES` | Standalone crossing point per crop, per V7 |
| `OUT_TOM_DIP_BED` | The bed at which tomato marginal cost falls below the bed before it |
| `OUT_TOM_DIP_SIZE` | The size of that fall, in dollars |

**Checks**

| Output | What it reports |
|---|---|
| `OUT_CONSTRAINTS_OK` | `OK` only when every constraint check reads `OK` |

`OUT_TOM_DIP_BED` and `OUT_TOM_DIP_SIZE` are reported and not explained. Locating
the dip is this stage's job; accounting for it is Stage 3's.

---

## Audit Findings

*To be completed after the build. One entry per check: what I checked, what I
found, what I did.*

**V1 — Labor function, hand-checked at q = 1.** Calculated 2.5 × 36 × 1.10 = 99
hours by hand and compared against the workbook, which returns 99.00. PASS. This
check would have caught a dropped `(1 + dim)^q` term — without the exponent the
same cell returns 90 hours, which looks entirely reasonable and is wrong in every
figure downstream.

> **TODO —** V2, V3, V4, V5 after the build.
