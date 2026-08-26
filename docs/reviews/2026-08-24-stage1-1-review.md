<!-- PR TARGET: https://github.com/CoriMackie/Cori-Mackie | Stage 1.1 (2.5 pts) -->
# Stage 1.1 review — engagement brief · **80 / 100** (B-) · 2.00 / 2.5 pts

**Brief:** [`docs/briefs/Case1.md`](https://github.com/CoriMackie/Cori-Mackie/blob/main/docs/briefs/Case1.md)

> Graded 2026-08-26. This stage was held at the last pass because there was no case brief in the repository — only an unfilled generic template. There is one now, so the stage is graded and entered. It lands at the floor: the hypothesis is there and it is specific, and most of the reasoning behind it is not.

| Criterion | Earned | Notes |
|---|---|---|
| Problem restated in your own voice | 17 / 30 | The opening two sentences are yours and they are good ones — 64 beds, three crops, a few weeks to plan, and a commitment to a whole season made with limited manpower. "He has a few weeks to plan and commit to an entire season" gets at something the case README does not say outright, which is that this is an irreversible decision made under a deadline. Everything after that is a bulleted transcription of the case facts, several of them word for word including the arrows and the "implied $34.72/hr". Restating is not copying: if you cannot say it differently from the source, you do not have it yet. Three things the case gives you are missing entirely — the per-crop bed caps of 20 / 20 / 30, the diminishing-returns rates, and the fact that the farm is a price taker, which is the reason this is a perfect-competition case at all. |
| Hypothesis names a specific mix | 19 / 25 | Twenty carrot beds and 30 mesclun beds are real, committed numbers. Tomatoes are "no more than 10", which is a ceiling rather than a prediction — an outcome of 3 beds and an outcome of 10 beds would both satisfy it, so it cannot be shown wrong from below. Say the number you actually expect. There is also an arithmetic thread worth pulling: you write 64 total beds in the facts, then "10 of the 60 beds", and 10 + 20 + 30 comes to 60. Four beds are unaccounted for. If leaving beds empty is deliberate, that is a genuine economic claim and a good one — say it and say why. If it is a slip, fix it. Either way it should not be silent, because a reader cannot tell which it is. |
| Economic mechanism | 12 / 25 | "The farmer will add the beds of each crop until the market price will equal the cost of producing the next bed" is P = MC, stated correctly, and that is the rule this case runs on. But it is the general rule, and it is the only reasoning in the brief. It would produce the same sentence for any farm, any crop, any price. What is missing is why these three numbers rather than some other three: nothing about tomatoes earning $8,800 a bed against carrots' $2,094, nothing about labor rising 10 percent per tomato bed against 2.5 percent for carrots and 1.25 percent for mesclun, and no statement of which crops you think stop because marginal cost catches the price and which stop because they run into a bed cap. Worth knowing: the text you pasted into the Stage 0 submission box had more of this than the brief does. You wrote there that you doubted you would plant all 20 tomato beds because labor rises 10 percent with each one. That is exactly the missing sentence, and it was already yours. |
| Falsifiability and process | 6 / 20 | There is no statement of what result would show the hypothesis wrong, and that is the criterion this stage exists for. A prediction that survives every possible outcome is not a prediction. Two or three lines is all it takes: "if carrots finish below 20 beds, then something other than the bed cap bound first," "if tomatoes come in well above 10, the 10 percent compounding matters less than I assumed." Process credit where it is due: the brief was committed before any modeling work, which is the one thing in this stage that cannot be fixed later, and you have it right. Two deductions on the file itself — it is at docs/briefs/Case1.md rather than the graded path docs/briefs/perfect-competition-brief.md, and it is named for the case number rather than the engagement, which is the same reason the repo is not named after a course. |
| **Raw total** | **54 / 100** | — |
| **Floor applied** | **+26** | 80% floor: a committed brief that states the problem and names a specific mix |
| **Final** | **80 / 100** | floored |

### Why the floor applies

The raw total came to 54. Any committed brief that states the problem in your own words and names a specific mix is floored at 80, so 80 is what is recorded. I am telling you the raw number rather than hiding it because the gap between 54 and 80 is the work, and it is about ninety minutes of it.

The distance is not knowledge. You demonstrated the mechanism in the Stage 0 box three days before you wrote this brief. What is missing is putting it in the file.

### What I'd do, in order

- Move the file to docs/briefs/perfect-competition-brief.md. Copy the contents, create the file at the new path, commit, delete Case1.md. Name things after the engagement, not the assignment number.

- Turn the fact bullets into two or three paragraphs of your own. What the farm is deciding, what is fixed, what limits the choice. Add the three things missing: the per-crop caps of 20 / 20 / 30, the diminishing-returns rates of 10 percent, 2.5 percent, and 1.25 percent, and the price-taker point — the farm cannot choose what it earns per bed, only how much it plants.

- Commit to a tomato number. Not "no more than 10" — the number you expect.

- Say why each number, using the case's own figures. This is where most of the 25 points sit, and you already have the argument: labor rises 10 percent per tomato bed, so tomatoes stop early on economics; carrots barely rise at 2.5 percent, so they run to the cap and stop on the constraint rather than on price. Say which crops stop on which.

- Add three lines on how you would know you were wrong. Name the outcome and name the assumption it would break.

- Account for the four beds. If they stay empty, say why leaving land idle can be the profitable choice.

### Housekeeping in docs/briefs

Two files in that folder are noise and should go. initial-case-brief.md is the unfilled generic template, still carrying [CASE TITLE] and an example hypothesis about caching strategies and API latency — nothing to do with a farm. Case-1.docx is a Word document in an otherwise Markdown repository, so it cannot be read on github.com or diffed between versions.

This is worth doing for a reason beyond tidiness. A portfolio repo is read by people who did not watch you build it, and an abandoned template with somebody else's example in it reads worse than an empty folder — it suggests the folder was populated rather than used.

### Looking ahead

Stage 1.2 asks for capabilities/marginal-analysis/spec.md written before the workbook exists, then an audit of what gets built from it. Your capability folder exists now. The reasoning you put in this brief is the reasoning that spec runs on, so filling the gaps above is not a box to tick on the way past — it is the thinking Stage 1.2 is built on top of, and the vaguer the brief, the more the spec has to invent.

Stage 3 asks you to compare what you predicted against what your model found. That comparison is only worth writing if the prediction had a reason behind it. "I predicted 20 carrots and got 20 carrots" tells you nothing; "I predicted 20 because I expected the cap to bind before marginal cost did, and here is what the schedule actually shows" is the memo.

---

### How to work this review

Treat this PR the way an analyst treats feedback from a senior reviewer — a review is a proposal to engage with, not a checklist to rubber-stamp.

1. **Read it yourself first.** Form your own view before you change anything. Disagreeing *with a documented reason* is a legitimate, senior response.
2. **Stress-test it with an LLM.** Paste this review and your brief into your assistant and ask it to (a) explain anything you are unsure of, and (b) argue the *other side* — where might the reviewer be wrong, and what would you give up by making each change.
3. **Then write the changes yourself.** For a brief, this matters more than usual: a hypothesis you did not generate cannot be honestly compared against your model in Stage 3, and that comparison is the entire point of writing the brief first.
4. **Close the loop.** Reply in this thread with what you changed and what you pushed back on, then commit and push.

*One standing rule for this stage: do not revise your hypothesis to match what your model later tells you. If the model contradicts the brief, that is a finding, not an error — Stage 3 asks you to explain the gap, and a brief quietly edited to be right afterwards has nothing left to explain.*

— Adam
