# Cori Mackie — feedback, sweep of 2026-10-08

## Research paper review — pre-deadline read

**What I read.** The paper you uploaded to Lamaku, in full; it is the same file as `analysis/research-paper.pdf` · your point-by-point response under `papers/mahi-pono-east-maui-water/feedback/2026-09-24-adam.md` · `docs/briefs/2026-10-07-research-brief.md` and `capabilities/economic-research/spec.md` in full · `analysis/figures/README.md` and `data/README.md` · your prompt-log reflection · the commits since my last read, and a search of the repository for each number in the paper.

**What I did not open this pass.** The five dated drafts, beyond that search · `outline.md`, which my last read covered · the figure images on their own (I read them in the PDF) · your Case 1 files. If something in those changes an item below, say so and I will look.

---

All four items from my last read are done, and you answered each one in writing under the feedback file, which is where I asked for it. The numbers are new and better sourced: the $62 million holdback from A&B's 10-K against the $292,000 permit rent from the DLNR board submittal. The decision-maker is named in the first line of section 2: "BLNR sets the price for East Maui water through annual revocable permits." Figure 2 now carries measured data, more than a century of Honopou Stream flow from a USGS gauge, and section 6 gives Mahi Pono its best case before the recommendation answers it. The access value of "about $1.9–$3.1 million annually" and the "$1.6–$2.8 million" gap both check from your own inputs. This is a good subject for this paper: local, live, with a real price in it.

**Which quantity is six to eleven times the rent?** Section 3 says "The gap—about $1.6–$2.8 million, or 6–11 times the rent—is economic rent." Divide each end of the gap by $292,000, then each end of the access value by $292,000. Which of the two gives 6–11? Make the sentence and the multiple name the same quantity.

**What volume is the 2.5 cents spread over?** Section 4 says Mahi Pono pays "approximately 2.5 cents per 1,000 gallons," but the paper does not say how many gallons the $292,000 covers. Is it the 31.5 million gallon a day cap, every day of the year, or what EMI actually diverts? If diversions run below the cap, which way does the rent per gallon move, and what does that do to the comparison with the County's $1.31?

**What is the $62 million a price of?** Section 3 treats the holdback as "the market value of secure water access," and also says "A one-year permit may not fully reflect the economic value of that reliable access." Is money held back pending access a price for the water, or a discount for the risk of not getting it? Which reading does turning it into a yearly value at 3% and 5% assume, and does the paper say so?

**What would the scarcity price respond to?** Section 7 recommends "a pricing model that responds to water scarcity." Who sets it, and which measure moves it: which gauge, which flow? Your brief also set a test for being wrong: "if the price that Mahi Pono paid was the same as with the farmers and the community pay for the resources." Section 4 runs that comparison without calling it the test. Would naming it there make the verdict on your hypothesis plain?

**Commit the calculation.** Nothing in the repository computes the numbers the paper rests on: the access value, the gap, the 2.5 cents and the 14% Honopou decline appear only in the paper's own text and drafts, `data/` holds only its README, and Figure 2's flow series is not saved. A small sheet or script, plus the USGS series, would let a reader check every number back to its source. On github.com, open `data/`, choose **Add file**, then **Upload files**, add the USGS download and your calculation sheet, and commit. Or, in Claude Code or Codex opened in your portfolio repository: "Help me save the USGS Honopou flow data and a small calculation into data/ that reproduce the access value, the gap, the rent per 1,000 gallons and the 14% decline from the inputs in my paper. Do not change the paper."

You can re-upload before the deadline, and the latest upload is the one I grade.

**In order:**

1. Answer in section 3 which quantity is six to eleven times the rent, and make the sentence say it.
2. State the volume behind the 2.5 cents, and answer which way diversions below the cap would move it.
3. Answer in section 3 what the $62 million is a price of, and what the 3% and 5% conversion assumes.
4. Answer in section 7 who sets the scarcity price and what moves it, and decide whether to name your brief's test in section 4.
5. Commit the calculation and the USGS series to `data/`.
