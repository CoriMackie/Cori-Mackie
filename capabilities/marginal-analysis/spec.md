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

> **TODO —** State that the Cost / Marginal Analysis area holds **three separate
> schedules**, one per crop, each running from q = 0 to that crop's bed cap.
> As written, a builder could produce one combined schedule.

> **TODO —** State what a Validation cell outputs (PASS/FAIL, or OK/VIOLATED).

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

> **TODO — `MC(q)` is ambiguous.** `TOTAL_COST` is defined in §E at farm level,
> including fixed costs and all three crops. State that marginal cost is per
> crop, includes fertilizer, and excludes fixed cost.

> **TODO — The permanent/temporary split inside one bed.** §B applies the rule to
> the farm total only. Bed 5 of tomatoes is split 192.92 farmer hours / 4.73 temp
> hours — that split is what produces the marginal-cost dip. State the rule at
> the level of a single bed's incremental hours.

> **TODO — `BLENDED_RATE` is computed and never used.** State what it is for, or
> remove it. If it is for a per-crop P&L, §5 has to ask for one.

> **TODO — Bed counts must be integers.** Not stated anywhere.

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

> **TODO — V2 has no expected value.** Name which marginal cost is compared and
> what it must equal.

> **TODO — V3 has no pass condition.** Say what result is acceptable. Note that
> 20/0/0 is an infeasible starting point: 20 tomato beds needs 12,109 hours,
> about eight temp workers against a cap of four.

> **TODO — "approximately" appears twice** with no tolerance.

**V6 — Solver.** The optimization runs GRG Nonlinear with integer decisions,
maximizing season profit over the three bed counts.

> **TODO — Enumerate the constraints** V5 refers to.

> **TODO — State the crossing rule.** Marginal cost is not monotonic; once it
> exceeds price and later falls back below, which q is reported?

---

## 5. Outputs

The finished workbook should clearly show the optimal number of beds for each
crop; total beds used versus the 64-bed capacity; total, farmer, and temporary
labor requirements; number of temporary workers required; revenue; fertilizer and
labor costs; fixed and total costs; season profit; marginal cost by crop and bed;
P vs. MC; and whether all constraints have been satisfied.

> **TODO — Name the outputs** rather than listing them in prose, so §4 can refer
> to them.

> **TODO — Add the location of the tomato marginal-cost dip** as a reported
> output (Stage 3 needs it).

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
