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
maximizing point where price equals marginal cost.

## What I first thought

<!-- Three or four sentences, your words. The three things to cover:

     1. Your first prediction: 10 tomatoes, 0 carrots, 43 mesclun. Why mesclun hardest?
        (1.25% is the flattest penalty of the three.) Why no carrots?
        ($2,094 a bed looked negligible next to tomatoes at $8,800.)

     2. What you had missed: mesclun is capped at 30 beds, so 43 was never available.

     3. The reasoning error worth naming: you were pricing carrots against tomatoes
        instead of against their own cost. A carrot bed takes about 30 hours and $440
        of fertilizer, and earns $2,094 — it covers itself comfortably, which is why
        carrots run all the way to their cap.

     Delete this comment when you've written the paragraph. -->

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

To plant the last four beds would cost more than they would earn. Nothing forces them to stay
empty — carrots and mesclun are at their caps, so the only crop with room left is tomatoes, and an
eleventh tomato bed costs about $9,390 against a price of $8,800. Labor is not the limit either:
this mix uses roughly 5,277 of the 6,480 field hours the farm can buy. The four beds stay empty
because planting them loses money, not because the farm runs out of anything.

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

**If tomatoes come out well above 10 beds**, then the 10% labor penalty matters less than I
assumed. I have claimed the eleventh bed costs about $9,390 against a price of $8,800; if the
schedule shows it under $8,800, my picture of how fast tomato cost climbs is wrong.

**If carrots or mesclun finish below their caps**, then marginal cost caught the price before the
constraint did, and I was wrong that these two crops are stopped by the cap rather than by
economics. That would mean their 2.5% and 1.25% penalties bite harder than I gave them credit for.

**If all 64 beds get planted**, then leaving land idle was never the profitable choice and the
eleventh tomato bed pays for itself after all.

**If tomato marginal cost does not rise smoothly**, my reasoning is incomplete rather than wrong.
The farmer's own 720 hours cost $34.72 and temp hours cost $17.36, so somewhere in the tomato
schedule the marginal hour gets cheaper, not dearer. I have not accounted for that, and I expect
it to show up as a dip in the cost curve.

