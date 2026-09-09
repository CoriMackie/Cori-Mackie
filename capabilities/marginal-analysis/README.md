# Marginal Analysis

Finding the profit-maximizing quantity by comparing the price of one more
unit against what that unit costs to produce — the point where P = MC.

The capability is general; the engagement that exercises it is
`perfect-competition`, a 64-bed vegetable farm choosing a crop mix under
land, labor and time constraints. The brief that opened that engagement is
[`docs/briefs/perfect-competition-brief.md`](../../docs/briefs/perfect-competition-brief.md).

## What is here

| File | What it holds |
|---|---|
| `README.md` | this file |
| `spec.md` | the modeling approach, the conventions, and the validation plan |
| `model.xlsx` | the working model — four sheets, Solver-ready |

## The workbook

Four sheets, and every cell outside the shaded input constants is a formula.

- **Inputs** — every assumption as a named range carrying its unit and its
  source. The three decision variables (`TOM_BEDS`, `CAR_BEDS`,
  `MES_BEDS`) live at `B36:B38`; they are the only cells Solver changes.
- **Marginal Analysis** — one standalone MC schedule per crop, each built
  as though that crop were the only thing planted. The Decision column
  applies the crossing rule: a schedule stops at the first bed whose
  marginal cost exceeds price and stays stopped.
- **Optimization** — season profit at the current bed counts.
  `OUT_SEASON_PROFIT` (`B32`) is the Solver objective.
- **Validation** — every check computes to `OK` or `VIOLATED`, so a broken
  check is visible rather than something you have to read for.

## Running Solver

Solver models are stored **per worksheet**. Select the **Optimization**
sheet before opening Solver, or it will look at a sheet that has no model
and report that it has not executed the optimization.

| | |
|---|---|
| Objective | `Optimization!$B$32`, **Max** |
| By changing | `Inputs!$B$36:$B$38` |
| Constraints | `$B$36<=20`, `$B$37<=20`, `$B$38<=30`, `Optimization!$B$9<=64`, `Optimization!$B$20<=4`, `$B$36:$B$38 = integer` |
| Engine | GRG Nonlinear, *Make Unconstrained Variables Non-Negative* checked |

Run it from both start points named in V3 and confirm the two runs agree
on season profit.

## The result

**10 beds of tomatoes, 20 of carrots, 30 of mesclun** — 60 of 64 beds,
5,277 of 6,480 field hours, four temporary workers, **season profit
$42,761.66**.

An exhaustive sweep of all 9,726 feasible integer bed combinations confirms
this is the global optimum and that it is unique. Steepest-ascent from every
feasible starting point reaches it, so the model has no local optima to
strand Solver.

Standalone crossing points are 10 tomatoes, 10 carrots, 6 mesclun. Only
tomatoes cross where the whole-farm answer also stops; carrots and mesclun
are held by their bed caps, not by price.

## One finding worth carrying forward

The fourth falsification condition in the brief fired. Marginal cost does
not rise smoothly: at tomato bed 6 the farmer's own 720 hours run out and
the rate drops from $34.72 to $17.36, so MC **falls** from $7,660 to
$4,905 — a dip of **$2,754.58** — before resuming its climb. The model
locates the dip (`OUT_TOM_DIP_BED`, `OUT_TOM_DIP_SIZE`); accounting for
what it means is Stage 3's job.
