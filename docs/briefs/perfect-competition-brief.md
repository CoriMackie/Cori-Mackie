# Engagement Brief — Perfect Competition

**Author:** Cori Mackie
**First committed:** 2026-08-25, before any modeling work
**Capability:** `marginal-analysis` · **Engagement:** `perfect-competition`

---

## The problem

A farmer has 64 beds to plant a mix of tomatoes, mesclun and carrots within 36 weeks. Farmer
needs to generate the highest return while having constraints on land, labor and time. She won't
be able to change the mix due to the short time, so initial needs to be as close to correct as
possible.

The farm has fixed costs of $20,000 for the season. The farmer earns $50,000 and spends half her
time in the field, which is 720 hours at an implied $34.72 per hour. There is the opportunity to
hire up to four temporary workers at $25,000 each for the season, 1,440 field hours each, which
works out to $17.36 per hour.

Under perfect competition, the farmer should continue allocating beds to a particular crop while
the market price is greater than the cost of producing the next bed, which would mean the profit
maximizing point where price equals marginal cost. The farmer cannot change what the vegetables
earn, only how many beds she can plant. That is what makes it perfect competition.

## What I first thought

I guessed initially the 10 tomatoes and 43 mesclun just looking at the math working out, but
realizing that there was a cap, I had to go back and follow the parameters.

## Hypothesis

I hypothesize that the optimal crop mix will be **10 beds of tomatoes, 20 beds of carrots, and 30
beds of mesclun**, using 60 of the 64 available beds. My prediction is based on the relationship
between revenue, labor requirements, and diminishing returns for each crop per bed.

The rule is P = MC. She adds beds of a crop until the next bed will cost more than it earns. As you
plant more beds of the same crop, the labor cost of each additional bed goes up. For tomatoes, each
new bed costs about 10% more labor than the one before it. Whereas for carrots and mesclun, each new
bed only costs 2.5% and 1.25% more, respectively.

Tomatoes earn the most per bed at $8,800, but there is a limit to how many the farmer can plant
because each additional bed costs more than the one before it. Tomatoes, although most profitable,
will be the least amount because that cost keeps climbing. Carrots and mesclun don't increase too
much per bed and earn $2,094 for carrots and $2,700 for mesclun, so they stop at their caps rather
than on price.

To plant the last four beds would cost more than they earn. Carrots and mesclun are at their
limit, only tomatoes can be planted more but it would cost $9,390 against the $8,800 it earns. Even
though labor is still within budget, planting more loses money.

## Labor and cost per bed

Each bed carries a labor requirement and a fertilizer cost, and the labor is what grows as more
beds of the same crop go in.

| Crop | Labor, first bed | Fertilizer $/bed | Price $/bed | Labor growth per added bed | Bed cap |
|---|---|---|---|---|---|
| Tomatoes | 2.50 hrs/wk × 36 wks = 90 hrs | $880 | $8,800 | 10.00% | 20 |
| Carrots | 0.833 hrs/wk × 36 wks = 30 hrs | $440 | $2,094 | 2.50% | 20 |
| Mesclun | 1.25 hrs/wk × 36 wks = 45 hrs | $880 | $2,700 | 1.25% | 30 |

The farmer supplies the first 720 field hours at an implied $34.72/hr. Everything beyond that is
temporary labor at $17.36/hr, up to four workers at 1,440 hours each — so the farm cannot use more
than 6,480 field hours in a season no matter what it plants.

## How I would know I was wrong

Each of these is an outcome the model can produce. Any one of them would break a claim I have
made above.

**If the model plants more than 10 tomato beds**, the labor isn't as costly as I thought.

**If both the carrots and mesclun come out below their maximum allowed**, then that isn't what
stopped the farmer from planting more.

**If all 64 beds get planted**, then it would mean that the empty beds were not the profit
maximizing choice that I claimed.

**If the tomato cost doesn't rise smoothly**, it isn't a complete reason. The farmer has 720
hours at $34.72 and temp hours are $17.36. When adding the four additional tomato beds, if the
farmer switched from her higher labor of $34.72 for her own hours to the temp hours of $17.36,
there would be a dip in the cost of each bed. The marginal cost doesn't rise smoothly but dips,
so my reasoning is incomplete.
