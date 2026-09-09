# Spec — Marginal Analysis

The approach behind `model.xlsx`. Section numbers and convention numbers
here are the ones the workbook's own cell notes refer to.

---

## §1 Conventions

**Convention 1 — Exact quantities, never the printed rounding.**
Where the case prints a rounded figure, the workbook enters the exact
quotient. `CAR_HPB` is `=5/6`, not `0.833`. `PERM_RATE` and `TEMP_RATE`
are formulas, not the printed `$34.72` and `$17.36`. This is not
fussiness: typing the rounded rates returns a season profit of $42,768
against a check figure of $42,762. Validation V5 enforces it.

**Convention 2 — Only the field half of the farmer's salary is charged.**
She earns `FARMER_SALARY` and spends half her time in the field, so
$25,000 covers `PERM_HOURS` = 720 hours. The other half is not field labor
and is not charged to a bed.

**Convention 3 — Temporary labor is charged per hour worked.**
Cost accrues at `TEMP_RATE` per hour, not as a whole seasonal contract.
The *constraint*, separately, is on whole workers (§3E): a worker needed
for one hour is a worker hired. Cost is continuous, headcount is not.
This is a deliberate simplification — a real temp costs $25,000 whether
worked for one hour or 1,440 — and it is the first thing to revisit if
the answer is ever sensitive to it.

**Convention 4 — Whole beds only.** A bed is planted or it is not. The
three decision variables are integers, declared to Solver as such and
checked independently in V5.

**Convention 5 — Standalone schedules stand alone.** Each per-crop MC
schedule is built as though that crop were the only thing planted, each
drawing on the full 720 permanent hours by itself. The three schedules
therefore do not add up to the whole-farm answer and are not meant to.
They locate each crop's own crossing point; the Optimization sheet
allocates hours across crops jointly.

## §2 Inputs

Every input is a named range on the Inputs sheet carrying its value, unit
and source. Shaded cells are the only typed constants in the workbook.
Nothing downstream restates a number — everything refers to the name.

## §3 The model

**§3A Decision variables.** `TOM_BEDS`, `CAR_BEDS`, `MES_BEDS` at
`Inputs!$B$36:$B$38`.

**§3B Labor hours.** For a crop with `q` beds:

```
LABOR_HRS(q) = q x HRS_PER_WEEK_PER_BED x WEEKS x (1 + DIM_PCT)^q
```

The diminishing-returns term applies to the whole planting, not to the
last bed alone, so total hours grow faster than linearly and marginal
hours grow with every bed added. V1 hand-checks this at `q = 1`.

**§3C Derived rates.** `PERM_RATE = FARMER_SALARY / 2 / PERM_HOURS` and
`TEMP_RATE = TEMP_WORKER_PAY / TEMP_WORKER_HRS`. Never typed (Convention 1).

**§3D Permanent before temporary.** The farmer's hours are used first:
`OUT_PERM_HOURS = MIN(total, PERM_HOURS)`, and everything above that is
temporary.

**§3E Temporary headcount.** `OUT_TEMP_WORKERS = ROUNDUP(temp hours /
TEMP_WORKER_HRS, 0)`, capped at `TEMP_WORKERS_MAX`. With the cap at four,
the farm cannot use more than 6,480 field hours in a season no matter what
it plants.

**§3F Splitting a bed across two rates.** In the standalone schedules,
permanent hours are consumed one bed at a time, so a single bed can be
charged partly at `PERM_RATE` and partly at `TEMP_RATE`. This is what
makes the marginal cost curve non-monotonic (§5).

**§3G Marginal cost.** `MC(q)` is the labor cost of that crop's `q`th bed
plus one bed of fertilizer. It excludes `FIXED_COST`, which is fixed and
belongs in no marginal comparison.

**§3H The blended rate.** For the per-crop P&L only, labor is allocated at
`OUT_BLENDED_RATE` = total labor dollars / total labor hours. No crop
hires the temporary workers; the season does. Because the rate is an
average over the season, the three crop labor costs add back to
`OUT_LABOR_COST` exactly — checked by `OUT_PNL_RECONCILES`.

## §4 The objective and the constraints (V6)

Maximize `OUT_SEASON_PROFIT` (`Optimization!$B$32`) by changing
`Inputs!$B$36:$B$38`, subject to:

| # | Constraint |
|---|---|
| 1 | `TOM_BEDS <= TOM_CAP` (20) |
| 2 | `CAR_BEDS <= CAR_CAP` (20) |
| 3 | `MES_BEDS <= MES_CAP` (30) |
| 4 | `OUT_BEDS_USED <= FARM_BED_CAP` (64) |
| 5 | `OUT_TEMP_WORKERS <= TEMP_WORKERS_MAX` (4) |
| 6 | all three bed counts integer |
| 7 | all three bed counts `>= 0` |

Engine: GRG Nonlinear. The model is nonlinear in the decision variables —
`(1 + DIM_PCT)^q` carries `q` in the exponent — and non-smooth through
`MIN`, `MAX` and `ROUNDUP`, so Simplex LP does not apply.

The farmer's 720 hours are **not** a constraint. She works them or she does
not; what lies beyond them is hired.

## §5 Reported, not explained

Marginal cost does not rise smoothly. When a crop's cumulative hours pass
`PERM_HOURS` mid-bed (§3F), the rate on the next bed falls from
`PERM_RATE` to `TEMP_RATE` and MC dips before resuming its climb. For
tomatoes the dip lands at bed 6, worth $2,754.58 — MC falls from $7,660
to $4,905.

This stage locates the dip and reports it (`OUT_TOM_DIP_BED`,
`OUT_TOM_DIP_SIZE`). It does not adjust for it. That is Stage 3's job.

## §6 Validation

Every check computes to `OK` or `VIOLATED` — no other wording.

| | Check | What it would catch |
|---|---|---|
| **V1** | `LABOR_HRS(1)` for tomatoes equals 99 hours, computed by hand | A dropped `(1 + dim)^q` term — the same cell returns 90 without it |
| **V2** | MC of tomato bed 10, computed by hand, agrees with the model to the dollar | An error in the cost machinery mid-schedule, where the permanent hours are gone and every term of `MC(q)` is in play. Taken from mid-schedule, where an endpoint could agree by accident |
| **V3** | Solver run from two start points agrees on season profit | A local optimum reported as the answer |
| **V4** | Mix is 10/20/30, profit rounds to $42,762 and does not exceed it, crossings are 10/10/6 | Any drift in the headline result |
| **V5** | Zero error cells; constraints satisfied; per-crop P&L reconciles; rates derived rather than typed | Silent breakage anywhere in the sheets |
| **V7** | Every `Plant` precedes every `Stop` in each schedule | A schedule that stops and restarts — which would mean the per-bed labels report no single crossing point at all |

**On V3's start points.** Both must be **feasible**. An infeasible start
returns no profit figure, and the check requires a number from each run.
`20/0/0` — used in an earlier draft — needs 12,109 hours and about eight
temp workers against a cap of four, and every single-bed neighbour of it
is also infeasible, so a local search has no route out. The second start
is therefore `15/0/0`: the nearest tomato-only start that fits the
four-worker cap, and thirty hill-climb steps away from the answer.

**On V2.** `B25` is an observed input, not a calculated cell, and V2 reads
`VIOLATED` until a figure is entered. That is the intended state, not a
failure.

V2 originally cross-checked against an external reference implementation,
the Farm Profit Lab. That tool is no longer reachable, so the check is now
a hand computation instead:

```
LABOR_HRS(10) - LABOR_HRS(9) = 2,334.3682 - 1,909.9376 = 424.4306 hours
424.4306 x TEMP_RATE + TOM_FERT = $8,248.59
```

Be clear about what was lost in the substitution. An external
implementation could catch a model that is *conceived* wrongly — someone
else's formulas, arrived at independently, disagreeing with mine. A hand
computation cannot: it works the same model design, so it catches
arithmetic and formula-entry errors mid-schedule but shares any error in
how the model was conceived. V1 and V2 together now check the hours
function at `q = 1` and the full cost of a bed at `q = 10`; neither is an
independent check on the design itself. If a reference implementation
becomes available again, V2 should go back to being one.

## §7 Result

**10 tomatoes / 20 carrots / 30 mesclun — season profit $42,761.66**, using
60 of 64 beds and 5,277 of 6,480 field hours with four temporary workers.

Confirmed by exhaustive evaluation of all 9,726 feasible integer
combinations against the live workbook. The optimum is unique, and
steepest-ascent from every feasible start reaches it — the model has no
local optima.

The last four beds stay empty because the only crop not already at its cap
is tomatoes, and an eleventh tomato bed costs $9,391 against a price of
$8,800. Carrots and mesclun stop at their caps, not on price.
