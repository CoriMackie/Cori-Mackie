<!-- PR TARGET: https://github.com/CoriMackie/Cori-Mackie | Stage 1.1 (2.5 pts) -->
# Stage 1.1 review — engagement brief · **98 / 100** (A+) · 2.45 / 2.5 pts

**Brief:** [`docs/briefs/perfect-competition-brief.md`](https://github.com/CoriMackie/Cori-Mackie/blob/main/docs/briefs/perfect-competition-brief.md)

> Re-graded 2026-08-31. Your previous score was 80, and that 80 was the floor rather than a total you had earned — your raw was 54. This one is 98 on merit, and it is the largest improvement anyone has made on any stage in this course so far. Read the last section.

| Criterion | Earned | Notes |
|---|---|---|
| Problem restated in your own voice | 29 / 30 | Rewritten, and it is now among the two or three best in the cohort. You name the stakes in a way nobody else did: "She won't be able to change the mix due to the short time, so initial needs to be as close to correct as possible." That is what makes this a decision rather than an exercise — the choice is made once, before the season, and cannot be revised when the information arrives. You then define perfect competition from the farm's position rather than from a textbook: "The farmer cannot change what the vegetables earn, only how many beds she can plant. That is what makes it perfect competition." That sentence is the definition, derived rather than quoted. |
| Hypothesis names a specific mix | 25 / 25 | 10 tomato, 20 carrot, 30 mesclun — 60 of the 64 beds, with the four idle beds stated as a deliberate choice rather than a rounding error. You also kept the "What I first thought" section showing the 10-and-43 guess you started from and why the cap forced you off it. Leaving the wrong first answer visible next to the right one is a professional habit, not a confession. |
| Economic mechanism | 25 / 25 | Full marks, and the reason is that you stopped describing the mechanism and started computing it. The labor table converts hours per bed-week into a season: 2.50 x 36 = 90 hours for the first tomato bed, 30 for carrots, 45 for mesclun. You derive the labor ceiling — four workers at 1,440 hours plus the farmer's 720 — and get 6,480 hours, which is a number nobody else in this cohort produced. And then the sentence that earns this criterion outright: "only tomatoes can be planted more but it would cost $9,390 against the $8,800 it earns." That is P = MC as an arithmetic fact about one specific bed, not a principle. Every other brief in the cohort asserts that marginal cost eventually catches price. You are the only person who says where. |
| Falsifiability and process | 19 / 20 | Four conditions, each naming an outcome the model can actually produce and the claim it would break. The fourth one is the best thing written in this stage by anyone, so I want to quote it back: "When adding the four additional tomato beds, if the farmer switched from her higher labor of $34.72 to the temp hours of $17.36 there would be a dip in the cost of each bed. The marginal cost doesn't rise smoothly but dips, so my reasoning is not complete." You predicted, before building anything, that your own argument has a hole in it, named where the hole is, and named the mechanism that puts it there. That is not a falsification condition on your prediction. It is a falsification condition on your reasoning, which is a harder and rarer thing to write. The one point off is only that the first three conditions would be sharper with a number attached, the way the fourth one has $34.72 and $17.36 in it. |
| **Final** | **98 / 100** | earned on merit |

### What changed, and why it is worth saying out loud

Your previous brief scored 54 raw. The gaps were specific: the mechanism stopped at "the farmer will add beds until price equals the cost of the next bed," which is the rule rather than an application of it, and there was no falsification section at all.

You did not add a paragraph to each. You rewrote the brief, and the rewrite is a different kind of document — it has a table in it, it does arithmetic, and it argues against itself in the last section. Your commit history shows how: "Say what the $8,800 is: what a tomato bed earns", "Rewrite the idle-beds paragraph in my own words", "Rewrite the first two falsification conditions in my own words", "Rewrite the remaining falsification conditions in my own words". Four commits over two sessions, each fixing one thing, each named for what it fixed.

Two of those messages say "in my own words" explicitly, which tells me what happened: you got the structure from somewhere and then went back and made the sentences yours. That is the correct use of an assistant on a brief, and the reason it matters is Stage 3. In Stage 3 you explain why your prediction and your model disagreed. A prediction you did not personally reason your way to has nothing to explain.

### The one thing worth sitting with before Stage 2

You have located the marginal-cost dip, and you did it from the wage structure rather than from a chart. That dip is the single most interesting thing in this case and it is what Stage 3 is built around. Do not resolve it now.

What I would do instead: write down, today, exactly what you expect the shape to be — where the dip starts, roughly how deep, and whether it happens for all three crops or just tomatoes. Put it in the brief or in your prompt log. Then build the model and see. If you are right, you have predicted a non-obvious feature of a system from its cost structure alone, which is the whole skill this case is teaching. If you are wrong, the gap between what you expected and what happened is the most interesting paragraph you will write all term.

One caution, and it is the standing rule for this stage: do not revise the brief to match what the model tells you. If the model contradicts you, that is a finding.

### A note on your stage 0 feedback

There is a correction in your Stage 0 comment that I want you to actually read rather than skim. I credited you with two folder README files that exist but are 1 byte — empty files with the right names. I graded the filename instead of opening the file.

I am telling you because it is the same failure mode this case is about to test you on. A spreadsheet cell that displays $42,762 looks identical whether a formula produced it or someone typed it. Stage 1.2 asks you to check, and the reason it asks is that nobody checks by default.

---

### How to work this review

Treat this PR the way an analyst treats feedback from a senior reviewer — a review is a proposal to engage with, not a checklist to rubber-stamp.

1. **Read it yourself first.** Form your own view before you change anything. Disagreeing *with a documented reason* is a legitimate, senior response.
2. **Stress-test it with an LLM.** Paste this review and your brief into your assistant and ask it to (a) explain anything you are unsure of, and (b) argue the *other side* — where might the reviewer be wrong, and what would you give up by making each change.
3. **Then write the changes yourself.** For a brief, this matters more than usual: a hypothesis you did not generate cannot be honestly compared against your model in Stage 3, and that comparison is the entire point of writing the brief first.
4. **Close the loop.** Reply in this thread with what you changed and what you pushed back on, then commit and push.

*One standing rule for this stage: do not revise your hypothesis to match what your model later tells you. If the model contradicts the brief, that is a finding, not an error — Stage 3 asks you to explain the gap, and a brief quietly edited to be right afterwards has nothing left to explain.*

— Adam
