# Stage 1.2 — what's left

Working checklist. Not a deliverable — delete it before you submit if you'd rather.
Due 11 September.

---

## Already done

- [x] `spec.md` committed
- [x] `model.xlsx` committed **after** the spec (the commit order is graded, and it's correct)
- [x] Workbook has 25 named ranges, 733 formulas, 0 pasted values, 0 error cells
- [x] Check figures reproduce: 10/20/30 beds, $42,761.68 profit, crossings at 10 / 10 / 6
- [x] V1 hand check passes: one tomato bed = 99 hours

That's the build done. What's left is the spec and the audit.

---

## Sitting 1 — finish the spec (~45 min)

Open `spec.md`. Every TODO in it is a question you wrote for yourself. Answer each
one in a sentence and delete the TODO. Nothing here needs new analysis.

**Three are already settled — just write down the answer:**

- [ ] **Temp labor basis.** The stage page says temps cover leftover hours at
      $17.36/hr. Your check figure confirms it. Say so, delete TODO 3.
- [ ] **Temp worker constraint.** The stage page states it as *workers ≤ 4*.
      Write that form, delete the TODO asking which form it is.
- [ ] **Solver method.** GRG Nonlinear with integer decisions, per the stage page.

**Three are answerable from what the workbook already shows:**

- [ ] **Rounding.** Exact quotients, not the printed $34.72 / $17.36. The typed
      values give $42,768 against a published check figure of $42,762.
- [ ] **Standalone schedules (TODO 5).** The crossings only land on 10 / 10 / 6 if
      each crop draws on the full 720 permanent hours by itself. State the rule.
- [ ] **`PERM_RATE` and `TEMP_RATE`.** The workbook derives both. Write the two
      formulas into §3 so they're specified, not inferred.

**The rest are your judgment. These are the ones being graded:**

- [ ] **The crossing rule.** Marginal cost is not monotonic. Which q gets reported
      when MC goes above price and later comes back below? (See defect 1 below —
      this one is live, not hypothetical.)
- [ ] **Blended rate.** The stage page gives you two rules: the farmer's hours are
      consumed first, *and* the P&L allocates labor at the blended rate. Your spec
      has one of them. It calls having only one "the most common structural defect."
- [ ] **`MC(q)` definition.** Per crop, includes fertilizer, excludes fixed cost —
      say it, because §3E defines `TOTAL_COST` at farm level and they conflict.
- [ ] **Name the decision variables.** The three bed counts are the Solver changing
      cells and have no names anywhere in the spec or the workbook.
- [ ] **Integer bed counts.** Not stated anywhere.
- [ ] **Validation region.** Say the checks are computed *in the workbook*, and what
      a check cell outputs (PASS/FAIL or OK/VIOLATED).
- [ ] **V2 expected value.** Which marginal cost you'll compare to the Farm Profit
      Lab, and what it must equal.
- [ ] **V3 pass condition.** What result from the two Solver runs is acceptable.
- [ ] **Tolerance.** "Approximately" appears twice with no number attached.
- [ ] **Name the outputs** in §5 as a list, and add the tomato MC dip location as
      one of them.
- [ ] **Naming consistency.** §3 says `HRS_PER_WEEK_PER_BED`, `DIM_PCT`,
      `PRICE_PER_BED`; §1 defines `TOM_HPB`, `TOM_DIM`, `TOM_PRICE`. Also
      `TOTAL_LABOR` vs `TOTAL_LABOR_HOURS` for the same quantity. Pick one set.

- [ ] **Commit.** "Close the open specification questions before rebuilding" or similar.

---

## Sitting 2 — rebuild and run Solver (~30 min)

- [ ] Hand the corrected spec back to the AI tool and regenerate `model.xlsx`.
      Do **not** hand-patch the workbook — a workbook that no longer matches its
      spec is one nobody can rebuild.
- [ ] If you catch yourself explaining the model in the chat window: stop, that
      explanation belongs in `spec.md`. Add it, commit, regenerate.
- [ ] Open it in Excel. Set up Solver: maximize season profit, changing the three
      bed counts, constraints = bed caps, 64 total, temp workers ≤ 4, integers.
- [ ] Run Solver from **0/0/0**. Record the result.
- [ ] Run Solver again from **20/0/0**. Record the result. If they disagree, that's
      a finding, not a nuisance — it's what the check is for.
- [ ] Check every constraint cell reads OK.
- [ ] **Commit.**

---

## Sitting 3 — audit and the three small files (~30 min)

### Audit findings — append to the end of `spec.md`

You need at least three. Each says what you checked, what you found, what you did,
and what the check would have caught. V1 is already written. Here are the checks
already run and what they returned — the write-up is yours:

- [ ] **V1 — labor at q=1.** 99 hours, matches by hand. Already in your spec. ✓
- [ ] **V2 — Farm Profit Lab cross-check.** *Only you can run this one.* Take one
      intermediate marginal cost and compare. It's the only check that tests your
      model against a separate implementation instead of against itself.
- [ ] **V3 — two Solver starting points.** From sitting 2.
- [ ] **V4 — check figures.** All three reproduce.
- [ ] **V5 — integrity.** 733 formula cells, 0 pasted values in calculated cells,
      0 error cells, all inputs named ranges. One stray `W` in `Optimal Mix!E32`.

**Defects found in the first build** — worth writing up, because each one traces
back to a spec line that allowed it:

1. **The Plant/Stop column contradicts itself.** Carrots read Plant 1–10, Stop
   11–16, then **Plant again 17–20**. Mesclun read Plant 1–6, Stop 7–13, then
   **Plant again 14–30**. The sheet header says "the crossing point is where green
   ends" — but green ends and restarts. You predicted exactly this in your spec's
   crossing-rule TODO. That's the strongest finding available to you: the gap you
   left became a visible defect.
2. **No validation region built** — your §2 named four areas, the workbook has three.
3. **`BLENDED_RATE` computed in the spec, never used** — so the builder dropped it.
4. **Decision variables unnamed** — the Solver changing cells have no names.

- [ ] **The dip.** Note where it is. Don't explain it — that's Stage 3.

### The three small files

- [ ] **`README.md`** in this folder. It's currently 1 byte. Needs what the
      capability is and an "exercised in:" line. This is the same empty-file
      problem Adam already caught once.
- [ ] **`prompt-log.md`** in the repo root — an entry for this stage.
- [ ] **`README.md`** in the repo root — add this engagement under "Engagements"
      (it currently says none are logged).

- [ ] **Commit.**

---

## Before you close

- [ ] Open github.com in a browser and confirm `model.xlsx` and `spec.md` are
      visible at `capabilities/marginal-analysis/`. If it isn't visible there,
      it isn't submitted.
- [ ] At least two descriptive commits for this stage — you'll have more than two.
- [ ] Reply on PR #2 with what you changed and what you pushed back on.

---

## One correction owed to your brief

Not part of Stage 1.2, but do it while it's fresh. The brief's labor table says
"Labor, first bed | 2.50 hrs/wk × 36 wks = 90 hrs" and says each new bed costs
"about 10% more labor than the one before it." The stage page settles both: one
tomato bed needs 1 × 2.5 × 36 × 1.10 = 99 hours, and the growth factor raises the
labor requirement of *every* bed rather than compounding bed to bed. 90 is the base
rate before escalation, so the column label is wrong, not the number — and your
brief's own $9,390 figure already uses the correct formula.

Fixing a mislabeled input is not revising your hypothesis to match the model. Say
so in your PR reply so it reads as a correction rather than a quiet edit.
