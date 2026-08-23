# Case Brief: [CASE TITLE]

Date: 2026-08-23
Author: CoriMackie

---

## 1) One-line summary

Describe the case in one sentence. Example: "Evaluate whether change X reduces failure rate Y by at least Z%."


## 2) Background and context

Concise background: what system/feature/process the case involves, why it's important, and any previous findings or constraints.


## 3) Hypothesis

Write a clear, testable hypothesis using the format:

If [action/intervention], then [measurable outcome], because [rationale].

Example hypothesis (replace placeholders):

If we deploy the new caching strategy to the API layer, then average response latency will decrease by >= 20% under peak load, because the cache will serve the majority of repeated reads and reduce backend load.


## 4) Scope and success criteria

- In scope: (data sources, components, time window, metrics)
- Out of scope: (what we will not touch)
- Success criteria (explicit, measurable): e.g., "P95 latency drops from 420ms to <= 336ms over a 7-day evaluation window with no increase in error rate > 0.1%".


## 5) Data sources and provenance

List every data source you will use and where it comes from. For each, include:
- file path or query
- snapshot timestamp
- owner or contact

Example entry:
- telemetry/requests_2026-08-20.csv — pulled from monitoring cluster by @ops on 2026-08-20. Stored in data/telemetry/requests_2026-08-20.csv with commit message describing the pull.

(When you add the actual files, place them under data/ and record provenance in a README in that folder.)


## 6) Method / Analysis plan

Stepwise plan for how you will test the hypothesis and analyze results.
1. Reproduce baseline metrics from the last 14 days.
2. Implement the intervention in a staging environment behind the feature flag.
3. Run a controlled load test (specify tool/config) and collect the same metrics.
4. Compare baseline vs intervention across primary and secondary metrics (mean, median, p95, error rate).
5. Run statistical test or bootstrap if needed to estimate confidence in observed differences.
6. If results meet success criteria, schedule a canary rollout and monitor.


## 7) Risks and mitigations

- Risk: [what could go wrong]
  - Mitigation: [how to reduce risk]


## 8) Stakeholders and communication plan

- Owner: @YourName
- Reviewers: @team1, @team2
- Communication cadence: daily standups while running tests; post-mortem if rollout fails.


## 9) Timeline and milestones

- Day 0: finalize brief and gather data
- Day 1–2: build and test in staging
- Day 3: run controlled experiments
- Day 4: analyze results and decide
- Day 5+: rollout or iterate


## 10) Decision record (placeholder)

Once work is complete, record the outcome in docs/decisions/ with a link to this brief. Include a short decision summary, the final data, and the rationale.


## 11) Walkthrough: how to run this scenario (practical steps)

1. Create this brief in docs/briefs/ (done).
2. Create a data folder for this case under data/cases/[case-slug]/ and add provenance README.
3. Instrument or export the baseline telemetry and commit it to data/cases/[case-slug]/ with a timestamped filename.
4. Implement the change behind a feature flag in a branch: feature/[case-slug].
5. Run staged verification and capture logs/metrics into data/cases/[case-slug]/staging/.
6. Run controlled load tests, capture results in data/cases/[case-slug]/tests/.
7. Analyze results (notebooks or scripts go into analysis/cases/[case-slug]/).
8. Draft decision note in docs/decisions/[case-slug]-decision.md summarizing outcome and linking to data and analysis.
9. Add a short entry to prompt-log.md for any AI sessions that materially changed the approach or artifacts.


## 12) Templates and filenames (recommended)

- docs/briefs/[case-slug]-brief.md  ← this file
- data/cases/[case-slug]/README.md  ← provenance
- data/cases/[case-slug]/baseline-YYYYMMDD.csv
- data/cases/[case-slug]/staging-YYYYMMDD.csv
- analysis/cases/[case-slug]/analysis.ipynb
- docs/decisions/[case-slug]-decision.md


---

Notes: Replace bracketed placeholders (e.g., [CASE TITLE], [case-slug]) with your real values. Keep this brief minimal and actionable — it exists to make the hypothesis testable and to keep provenance clear.
