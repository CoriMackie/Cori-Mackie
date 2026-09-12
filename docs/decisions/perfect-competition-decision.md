# Engagement Decision — Perfect Competition

**Author:** Cori Mackie
**Decided:** 2026-09-09, after the model was built and validated
**Capability:** `marginal-analysis` · **Engagement:** `perfect-competition`
**Brief:** [`docs/briefs/perfect-competition-brief.md`](../briefs/perfect-competition-brief.md)
**Model:** [`capabilities/marginal-analysis/model.xlsx`](../../capabilities/marginal-analysis/model.xlsx)

---

## The recommendation

Plant **10 beds of tomatoes, 20 of carrots and 30 of mesclun**. Leave four
beds empty. The season earns **$42,761.66**.

| | Beds | Revenue | Field hours |
|---|---|---|---|
| Tomatoes | 10 | $88,000 | 2,334 |
| Carrots | 20 | $41,880 | 983 |
| Mesclun | 30 | $81,000 | 1,960 |
| **Planted** | **60** | **$210,880** | **5,277** |
| Idle | 4 | — | — |

Against that: $44,000 of fertilizer, $104,118 of labor and $20,000 of fixed
cost, for $168,118 total. The farm hires all four temporary workers and
uses 5,277 of the 6,480 field hours they and the farmer make available.

## Why this is the answer

At the margin every additional bed is worked by temporary labor at $17.36
an hour. The farmer's own 720 hours are gone before the eleventh bed of
anything goes in, so the decision at every margin that matters is priced
the same way. From there the three crops stop for two different reasons.

**Tomatoes stop on price.** The eleventh bed costs $9,390.72 to plant and
earns $8,800. That is the P = MC crossing, and it is the only one of the
three that the price actually causes.

**Carrots and mesclun stop because they run out of beds.** The twentieth
carrot bed costs $1,688.95 against a price of $2,094. The thirtieth mesclun
bed costs $2,420.10 against $2,700. Both are still making money when they
stop — they stop because the case caps them at 20 and 30, not because the
next bed would lose.

**The four idle beds follow from those two facts.** Carrots and mesclun
have no headroom left. The only crop that could take another bed is
tomatoes, and an eleventh tomato bed loses $590.72. Labor is not what
stops the farm: it finishes the season with 1,203 field hours unused.
Planting the last four beds is possible and it is not worth doing.

![Marginal cost of each tomato bed, shown as stacked bars against the fixed $8,800 price. Beds 1 to 5 are carried by the farmer's own hours at $34.72; bed 6 onward is hired labor at $17.36, and marginal cost falls $2,754.58 at that switch before climbing again to cross the price between beds 10 and 11.](../../analysis/figures/tomato-marginal-cost.png)

*Each bar is split by what the cost is made of, so the colour change at bed 6
is the wage switch itself. The interactive version, with figures on hover and
all twenty beds as a table, is at
[`analysis/figures/tomato-marginal-cost.html`](../../analysis/figures/tomato-marginal-cost.html).*

## How the hypothesis held up

The brief predicted 10 / 20 / 30 and 60 beds planted. That is exactly what
the model returns, and I set four conditions that would have shown me wrong.

**Three of them survived.** The model did not plant more than 10 tomato
beds. Carrots and mesclun did not come out below their caps — both landed
exactly on them, which is what I said would have to be true if the caps,
rather than price, were what stopped them. And not all 64 beds were
planted; four stayed empty.

**The fourth fired.** I wrote that if the farmer switched from her own
$34.72 hours to $17.36 temporary hours, marginal cost would dip rather than
rise smoothly, and that my reasoning would then be incomplete. It does dip.
Her 720 hours run out partway through the fifth tomato bed, and the sixth
bed is charged entirely at the temporary rate — so marginal cost falls from
$7,660.86 to $4,906.28, a drop of **$2,754.58**, before it resumes climbing.

What I had wrong was where it happens. I expected the dip somewhere around
the four extra tomato beds, at 11 through 14. It is at bed 6, five beds
before the decision point. By the time tomatoes reach the crossing, beds 10
and 11 are both priced entirely at the temporary rate, so the break sits
upstream of the margin and never touches it.

So the conclusion in the brief holds, and the arithmetic in it was already
right — I had the eleventh bed at $9,390 against $8,800, and the model says
$9,390.72. What was incomplete was the reason. The crossing is clean not
because marginal cost rises smoothly, which it does not, but because the
discontinuity is finished with well before the margin is reached.

## The standalone crossings are not the answer

Each crop also has its own schedule, built as though it were the only thing
planted. Those cross at **10 tomatoes, 10 carrots and 6 mesclun** — and only
the tomato figure matches the recommendation.

The difference is not an error, and it is worth being able to explain.
Every standalone schedule gives that crop the farmer's full 720 cheap-to-
her, expensive-to-charge hours to itself at $34.72. Carrots priced that way
stop at bed 11, which costs $2,140.11 against $2,094. Mesclun stops at bed
7 by $10.71. But the farm only has 720 such hours once. In the real
allocation they are absorbed early, and carrots and mesclun are worked at
$17.36 throughout — where that same eleventh carrot bed costs $1,290.06,
nowhere near the price.

The standalone schedules locate each crop's crossing under the assumption
that it is alone. The farm is not alone, so they should not be read as the
plan. The mesclun figure in particular turns on $10.71 and I would not put
weight on it.

## What I am not claiming

**Temporary workers are lumpier than the model prices them.** Labor is
charged by the hour, but a worker is hired for the season. The plan uses
4,557 temporary hours out of the 5,760 that four workers make available —
about $20,882 of capacity that is paid for and not worked. That does not
change the recommendation, but it means the labor cost is a floor rather
than what the farmer would actually write cheques for.

**The farmer's own hours are charged, not sunk.** Half her salary, $25,000,
is charged against her 720 field hours. She earns it either way. If those
hours were treated as already spent, the same mix would still be optimal
and the season would report $67,761.66 instead. The mix does not depend on
this choice; the profit figure does.

**One season, and prices are fixed.** No rotation, soil or carry-over
effects, and the farmer cannot move her prices — that last one is the
perfect-competition assumption the engagement is built on, not a finding.

**The dip is located, not accounted for.** Knowing marginal cost breaks at
tomato bed 6 is enough to show it does not disturb this answer. It is not
enough to say what a farmer should do about a cost curve that falls before
it rises. That is the next piece of work.

## How far this was checked

The checks in the workbook read that it is OK, but they fall into two groups.
The first group is the evidence. The second group is only as reliable as the
arithmetic I did by hand behind it.

The majority of the workbook checks itself. That is the seven constraints,
the figures of the mix, season profit and the three standalone crossings, the
integrity checks, and the rule that once a crop stops planting it never
starts again. All of those compute from the model's own cells, so they
re-test themselves each time a bed count moves. V1 is computed by hand — the
hours for one bed, 1 × 2.5 × 36 × 1.10 = 99 — against the cell that should
return it.

The other two are different. V2 and V3 do not check themselves — I put those
numbers into the sheet myself.

V2 is the marginal cost of tomato bed 10. The model returns $8,248.59, and I
worked the same figure out by hand from the case table. They agree to the
dollar. V3 is the season profit Solver reported from two different starting
points, and both runs came back $42,761.66.

What the sheet is checking there is that two numbers match. It has no way of
knowing where mine came from, or whether I ran Solver the way I said I did.

V2 is also weaker than I meant it to be. I wrote it as a cross-check against
the Farm Profit Lab, which is an outside model of the same case. The Lab is
out of reach now, so V2 became a hand computation instead. The trouble with
that is that I am working the same way the model works — so if the model and
I are wrong in the same way, the check still reads OK. It will catch bad
arithmetic. It will not catch a bad idea.

(V6 in the workbook is the Solver setup itself, not a test.)

Beyond the workbook's own checks, all 9,726 feasible bed combinations were
evaluated against the live model. 10 / 20 / 30 is the global optimum and it
is unique, and a steepest climb from every feasible starting point reaches
it, so there is no local optimum for Solver to have settled on instead.

### A correction to this section

I wrote here that every validation check read OK. The sheet showed
**VIOLATED** on V2 and V3. I wrote what I thought to be true, not what the
workbook actually showed.

The fault was not in the checks. The observed values were sitting in their
cells; the two check cells were still showing the result from before those
values were entered, because the file was last written by a tool that does
not recalculate formulas. Formula and inputs were both right, and the file
as committed still showed two failed checks to anyone who opened it. The
workbook now carries the recalculated results and is set to recalculate when
it opens, so a check cell cannot show a stale answer again.

The claim is true now. It was not true when I made it, and the whole
difference is that I had not opened the sheet while writing the sentence
that described it.
