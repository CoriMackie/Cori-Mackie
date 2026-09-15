@CoriMackie

Reviewed below, criterion by criterion. This is entered.

CRITERION BY CRITERION

* **Spec completeness — inputs, structure, calculation flow** — The status line no longer says DRAFT and no TODOs remain, so the document finally describes the model that exists. Both costing rules, and — rarer — an explanation of *why there are two* and where each applies. §3F splits permanent and temporary hours inside a single bed: "Tomato bed 5 takes 192.92 of the farmer's remaining hours and 4.73 temporary hours." Computed independently: 192.924 and 4.7295.
* **Spec validation rules** — Full marks. V4 states mix, profit and crossings as acceptance criteria before the build, with a tolerance rule saying profit must round to the check figure and must not exceed it. V7 is the best rule anyone wrote: MC is non-monotonic, so the crossing is the *first* bed above price and the schedule stays stopped — with the observation that carrots come back under price at beds 17–20. Verified: they do.
* **Workbook satisfies the contract** — 42,761.66, 57 named ranges, 791 formulas, no error cells, per-crop P&L reconciles. Your own Validation sheet reads VIOLATED on V2 and V3.
* **Audit note** — V1 was written properly. **V2–V5 are now written, and they are the best audit on this stage.** See below. The criterion asks for at least three concrete checks; you have one.

**V3 IS A FINDING ABOUT THE CHECK ITSELF, AND THAT IS RARE**

You wrote it plainly:

> **V3 could not have passed as it was first written, and running it is what showed that.**

Your second Solver start was 20/0/0. Twenty tomato beds need about 12,109 hours — roughly eight
temporary workers against a cap of four — so the start is infeasible, and so is every single-bed
neighbour of it. Solver has no route out and the check cell has nothing to read.

Then the sentence that earns the marks: *"A validation rule that cannot be satisfied is worse than no
rule, because it looks like diligence."*

You moved the start to 15/0/0. I checked that choice: 15 tomato beds need 5,639.29 hours, which is
3.42 temporary workers — feasible. Sixteen beds need 6,616.76 hours, which is 4.09 workers —
infeasible. **15 is exactly the nearest tomato-only start that fits the cap**, which is what you
claimed, and it is right.

**THE EXHAUSTIVE SEARCH, VERIFIED**

> all 9,726 feasible bed combinations were evaluated against the live model

I enumerated the same space: 13,615 combinations satisfy the bed caps and the 64-bed total, and
**9,726** of those also satisfy the four-worker cap. Your count is exact. 10/20/30 is the global
optimum, it is unique, and the runner-up (10/20/29) sits $279.90 behind.

That converts V3 from "two runs agreed" into "there is no local optimum for Solver to have settled
on" — which is the thing the check was written to detect and the thing two runs can only ever suggest.

**V5, AND WHY YOUR WORKBOOK NEVER CARRIED THE DEFECT THAT COST OTHERS $6.67**

> both labor rates are derived, not typed … typing those two printed figures in place of the quotients
> returns a season profit of $42,768 against a check figure of $42,762 — a $6 error produced by
> nothing but two roundings … **This check was specified before the workbook existed, which is the
> only reason the workbook never carried the defect.**

That last clause is the entire argument for spec-first, and you are the person on this stage entitled
to make it, because your spec did it and your workbook is clean. The exact figure is $6.67.

**V2, AND KNOWING WHAT A CHECK CANNOT DO**

> A hand computation works the same design the model works. It will catch a mis-typed exponent or a
> term dropped from `MC(q)`; it cannot catch a model conceived wrongly, because the conception being
> checked is the one doing the checking.

This is the most sophisticated sentence written about verification on this case. You downgraded your
own check's standing when the Farm Profit Lab went out of reach, said exactly what was lost, and left
instructions to restore it. Your arithmetic is exact as well — marginal hours for tomato bed 10 are
**424.4306**, and MC is **$8,248.59** against your workbook's $8,248.5865.

Choosing bed 10 rather than an endpoint "because at q = 1 the permanent hours cover the whole bed and
most of `MC(q)` is dormant" shows you understand what makes a test informative rather than merely
passable.

**THE DEFECT YOU CAUGHT IN YOURSELF**

The check cells displayed `VIOLATED` while their inputs were correct, because the file had last been
written by a tool that does not recalculate — so each check showed a verdict from before its input
arrived. And you say where it went:

> it got past me into the decision memo, which claimed a verification the sheet did not show.

That is the exact contradiction I flagged last sweep, and you closed it from the inside rather than
patching the sentence. The rule you drew — *"the memo gets written last from now on, with the
validation sheet open beside it"* — is the correct generalization.

**WHERE THIS LEAVES YOU**

The audit that was four TODOs is now the strongest on the stage, and three separate items in it
are findings about the *checks* rather than about the model. That is a harder and more valuable thing
to produce.

**WHAT YOU GOT THAT ALMOST NOBODY DID.** Your Convention 4: "The exact quotients govern, not the
printed $34.72 and $17.36... Typing the printed values returns a season profit of $42,768 against a
check figure of $42,762." That is right to the dollar — 42,768.33 with those two rounded and the carrot
rate exact. You wrote it before building, so your workbook never had the defect that cost several
people in this cohort real time to find.

**THE MEMO PROBLEM.** Your memo claims a verification your own Validation sheet does not support — it
reads VIOLATED on V2 and V3. Your prompt log and your working checklist both state the situation
accurately; the memo is the one document that ran ahead of the work.

This is worth separating from a mistake, because it is not one. It is what happens when a summary is
drafted from what you expect the result to be rather than from the artifact in front of you, and it is
the single easiest way for careful work to acquire a claim it cannot support. The fix is mechanical:
write the memo last, with the validation sheet open beside it. It is addressed again in your Stage 1.3
review, where the same document is in scope.

---

**How to reply to this review.** Comment on this pull request with what you changed, or push another
commit to `main` and say so here. If you disagree with something, say that too — a disagreement you
can support is worth more to me than a correction you make because I asked. This stage is still open.

