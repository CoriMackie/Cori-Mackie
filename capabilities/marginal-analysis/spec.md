# Model Spec: Marginal Analysis — Planting Mix Under Perfect Competition

Date: [DATE]
Author: CoriMackie

Status: DRAFT — not yet ready to hand to a builder.

---

## 1) Inputs

Every input the model needs, as a named contract: name, value, unit,
source in the case scenario. One row per input — do not skip an input
because "it's obvious," and do not leave a value blank because you
haven't decided the name yet.

| Name (named range) | Value | Unit | Source |
| --- | --- | --- | --- |
| [e.g. TOM_PRICE] | [ ] | [ ] | [where in the case scenario this came from] |
| [e.g. TOM_HRS_PER_BED] | [ ] | [ ] | [ ] |
| [e.g. TOM_DIM_PCT] | [ ] | [ ] | [ ] |
| [repeat for carrots, mesclun] | | | |
| [WEEKS] | [ ] | weeks | [ ] |
| [OWNER_HRS] | [ ] | hours | [ ] |
| [OWNER_WAGE] | [ ] | $/hr | [ ] |
| [TEMP_WAGE] | [ ] | $/hr | [ ] |
| [BED_CAP_TOTAL] | [ ] | beds | [ ] |
| [TEMP_WORKER_CAP] | [ ] | workers | [ ] |
| [per-crop bed caps, fixed costs, yields, other case inputs] | [ ] | [ ] | [ ] |

## 2) Structure

Every sheet or region the workbook will have, and what it's for
(inputs, cost structure, marginal-cost schedules, optimization,
checks). Name them; a builder should be able to lay out the file from
this list alone.

- [Sheet/region name] — [purpose]
- [ ]

## 3) Calculation logic

State every formula in named-range notation — never cell addresses.
The labor-hours mechanism (given) is:

```
LABOR_HRS(q) = q × HRS_PER_BED × WEEKS × (1 + DIM_PCT)^q
```

State, at minimum, in the same notation:
- How labor hours convert to labor cost, including the two
  allocation rules: owner hours consumed first (up to OWNER_HRS,
  at OWNER_WAGE), temporary hours covering the remainder (at
  TEMP_WAGE) — and that the P&L allocates cost at the *blended*
  rate (total labor $ / total hours), farm-level, not per crop.
- Revenue per crop.
- Marginal cost per crop (standalone, and how it's computed from
  LABOR_HRS).
- Profit (the Solver objective) as a function of the three bed
  counts.
- [any other calculated quantity the model needs]

Do not describe the *shape* you expect (e.g. "marginal cost rises
with quantity") — describe the *mechanism*. Let the model produce the
shape, including the non-monotonic dip mentioned in the case.

## 4) Validation rules

Acceptance criteria the finished workbook must pass. Include, at
minimum:

- q = 1 hand calculation: [state the expected value and how you
  derived it]
- No error cells anywhere in the workbook.
- Every calculated cell contains a formula — none are pasted values.
- Published check figures (treat as acceptance criteria, not just an
  answer key):
  - Optimal mix: Tomatoes [ ] · Carrots [ ] · Mesclun [ ] ([ ] beds)
  - Season profit: $[ ]
  - Standalone P ≈ MC points: Tomatoes ~[ ] · Carrots ~[ ] · Mesclun ~[ ] beds
- [any additional check you want the build held to]

## 5) Outputs

Name every result the model has to report (e.g. optimal bed counts
per crop, season profit, marginal-cost schedules per crop, shadow
prices on binding constraints, the P=MC chart). State the name, not a
cell address.

- [OUTPUT_NAME] — [what it is]
- [ ]

---

## Open questions / gaps found by AI critique

(Populated by an AI critique pass before the spec is finalized —
not filled in by the AI, only listed. Answer these yourself, edit the
sections above, then commit.)

- [ ]

## Audit findings (post-build)

(Populated after the workbook comes back — see the five required
checks. What was checked, what was found, what was done about it.)

- [ ]
