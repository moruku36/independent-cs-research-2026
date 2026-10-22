**English** | [日本語](2026-flowagent.ja.md)

# FlowAgent: Low-Latency Agentic Repair of Pre-Submit Test Failures (Google Scale)

## Key points for people and PMOs

- **What we learned**: in Google's internal environment, an agent that automatically repairs and proposes fixes for pre-submit test failures proposed a correct fix in 131 of 195 manually evaluated cases (67.18%). In production it showed fixes on 295,508 changes, and 28,554 were applied.
- **What it's useful for**: a concrete example when designing delegation of work to AI: narrow the scope, set time and attempt limits, re-verify before finishing, and filter out fake successes.
- **Caution**: results come from Google's internal infrastructure, models, and tests; the data is non-public, so external reproduction is hard. The evaluation is a manual judgment by three developers. Adoption rate is not quality rate. Time until a person's next edit and time to complete a repair are different metrics, and no causal time-saving effect is shown.
- **Next step**: manually check the operating ideas below (untested) against small fictional changes. No implementation, reproduction, or experiment was done.

## Survey record

- **Status**: primary text checked / PDF body §1–8, Tables 1–3, Figures 2, 3, 8, 9, and Listing 4 checked. Individual cited works not read closely; not reproduced.
- **Title, authors, year, venue, ID, primary URL**: *Catching Developers in the Flow: Low-Latency Agentic Program Repair at Google Scale* / Celal Ziftci, Spencer Greene, Ray Liu, Livio Dalloro, Lorenzo Dini (all Google) / 2026 / 41st IEEE/ACM ASE 2026 (the Preprint Notice at the start of the paper states acceptance; the conference's official acceptance list is unconfirmed). [arXiv:2610.07289v1](https://arxiv.org/abs/2610.07289v1), [HTML](https://arxiv.org/html/2610.07289v1), [PDF](https://arxiv.org/pdf/2610.07289v1), [DOI](https://doi.org/10.48550/arXiv.2610.07289) (value shown by arXiv; pending-registration notice seen, redirect target unconfirmed). A CC BY 4.0 notice was seen on the public HTML.
- **Date checked and version**: 2026-10-14 / v1 (PDF cover date 2026-10-05). Names and numbers were matched against the PDF. The HTML may retain `AutoRepair()` and unexpanded macro notation, so it was not used as evidence.
- **Treatment of the secondary article**: [AIDB 133569](https://ai-data-base.com/timeline/read/133569) (2026-10-13, "Google-style: how to narrow scope, set time, and verify when delegating work to AI agents") is an introductory article where only the public intro was seen and section 5 is members-only. Retrieving the article also failed in this record, so the full text was not read. We also do not assert that the article uses the same source as this paper. **The only basis for the text is the primary paper.**
- **Research question**: in the pre-submit outer loop, can an agent repair and propose fixes to test failures at low latency, before the developer leaves the flow of editing the change (§1)?
- **Method, data, comparison conditions**:
  - **Scope**: repair of test failures in Google's internal pre-submit outer loop. Build failures are out of scope (§2.1, §3.1). It integrates with internal tools TAP (continuous testing platform), Critique (code review), and Cider (internal IDE) (§2.2, §3.4).
  - **Model and behavior**: an internal version of Gemini 2.5 Pro fine-tuned on internal code and data, temperature 0.1, top_p 0.95 (§3.2). It runs a ReAct-style generate-and-validate loop in a sandbox, using tools for file editing, code search, build, and test running/log viewing.
  - **Limits**: at most 100 tool calls and at most 30 minutes of execution. The 30 minutes is explained as aligning with fix-attempt latency (§2.2) (§3.2).
  - **Final verification**: if the loop produces a diff, either the agent confirmed tests pass in its last cycle or tests are run again to confirm. Because LLM hallucination could otherwise present an invalid fix without a deterministic final check (§3.2). On success, one LLM call produces a summary of the failure cause and the fix.
  - **Pre-run filters (§3.1)**: repair is not attempted for these failures.
    1. Build failures (not test failures)
    2. Tests already failing in the repository
    3. Known flaky tests
    4. Changes made by automated tools
    5. Changes the developer already edited, making them stale
    6. Failures involving unsupported files such as images or binaries
    7. Changes over 100 files
    8. Changes over 1,000 lines
  - **Post-run filters (§3.3)**: if the developer updates the original change during processing (stale) or has already submitted it, the proposal is discarded.
  - **Presentation (§3.4)**: Critique shows, as part of the test-failure notification, a summary of the cause and a link/button to preview or apply in Cider. Complex fixes can be applied in Cider.
- **Claims and evidence**: see tables below. Sources are Tables 1, 2, 3 and §4.2.
- **Limitations and threats to validity (§5)**:
  - There were three manual evaluators, not owners of the tests concerned, so they may have misjudged. The 195 cases are a random sample but not necessarily representative of all failures.
  - The filters rest on feedback from a few early users and do not generalize to excluded changes.
  - Developers' selection bias (differing attitudes toward AI) is not controlled. Interviews were only with volunteer change authors, so they are self-selected.
  - It depends on Google's internal infrastructure, the internal Gemini 2.5 Pro model, prompts, and test quality. Robustness to small prompt changes or other models is untested.
  - The data is Google-confidential and non-public; there is no public reproduction package or dataset (Data Availability Statement). External reproduction is difficult.
- **Comparison with related work**: SWE-Agent, AutoCodeRover, Google-internal Passerine, and Meta's Engineering Agent are all post-submit repair that run offline without strict latency requirements. The authors claim this is the first to launch automatically at low latency from a failure in the pre-submit workflow and report results at industrial scale (§6). This "first" is the authors' claim, and we did not verify it with an exhaustive prior-work search. Do not compare the numbers side by side with other systems.
- **Free-to-run reproduction plan**: the paper's experiments cannot be reproduced (proprietary data, internal infrastructure). Instead, do the "manual check plan" below on small fictional changes. No cost, authentication, or tool installation is needed.
- **Usage status**: adopted as operating policy (the four points below) / effect unverified / application to implementation and reproduction not done. The paper did not demonstrate the effect of these four points.
- **Unconfirmed points and next checks**: the conference's official acceptance and where the DOI redirects, a full check of differences between the HTML and PDF, the full text (section 5) of AIDB 133569, the end of the aggregation period after October 2025 (the paper says "to date"), and the effect of the four practices in our own work. No experiments, paid runs, or environment configuration changes were made this time.

### Numbers and evaluation unit

**Manual evaluation (§4.1, Table 1)**: three developers with 5+ years of experience evaluated 195 randomly sampled test failures from 37 teams. Correct fixes were 131/195 = **67.18%**. In the remaining 64, the fix was wrong or inexact. The evaluation judges appropriateness against intent, not whether a developer actually applied it.

**Production usage (§4.2, Table 2)**: aggregated from October 2025. **The percentage on each arrow uses the preceding stage as its denominator.**

| Stage | Count | Share of preceding stage |
|---|---:|---:|
| Changes with test failures | 2,567,829 | — |
| Excluded by pre-run filters | 1,785,955 | 69.55% (derived: excluded/total; the paper does not state this share) |
| Repair attempted | 781,874 | 30.45% (of total) |
| Fix obtained | 421,818 | 53.95% (of attempts) |
| Excluded by post-run filters | 126,310 | part of obtained (derived) |
| Fix posted | 295,508 | 70.06% (of obtained) |
| Developer previewed | 65,069 | 22.02% (of posted) |
| Developer applied | 28,554 | 43.88% (of previewed) |

- Critique: 55,029 previews, 20,826 applies (37.84%). Cider: 21,279 previews, 12,702 applies (59.69%). One change can receive multiple fixes, so their sum exceeds the overall counts (§4.2.5).
- **Quality rate and adoption rate are different things**: 67.18% is correctness in the manual evaluation, while 43.88% and similar are developer behavior (apply after preview), which can include correct fixes that were not applied and the handling of wrong ones. Do not use apply rate as a proxy for accuracy or value.
- The derived shares are our own calculations, not values in the paper's text.
- **Scale of the target (Table 3)**: 781,874 attempts, 36,479 authors. Per change, mean files 10.57 (median 6), mean failing tests 16.49 (median 2), 917 file extensions. Per run, mean tool calls 21.37, mean tokens 424,149, cumulative tokens about 643 billion.

**Latency (§2.2, §4.2.2)**:

- For successful repairs, wall-clock time from the TAP failure notification to obtaining the fix is **p50 = 9.85 min, p90 = 25.83 min** (Figure 8).
- Time until a person's next edit (fix-attempt latency): in an analysis of 30 days in September 2025, p25 = 6.72 min, **p50 = 27.48 min** (Figure 2). This is **not the time until repair is finished**, but the time from failure notification to the next edit.
- The two differ in definition and population, so no causal effect of shortening human repair can be claimed. The paper itself gives examples where a slow fix arrived too late for the developer's manual response (§4.3.4).

**Interviews (§4.3)**: 9 developers (9 different groups, 6+ months tenure), 45 minutes each, in person. Limited to volunteers with preview or apply experience. Some found it useful; others raised irrelevant or wrong suggestions, slow arrival, and a wish for an indication of time to completion.

### Fake repairs and unfinished countermeasures (§4.2.4, §4.3.4, §8)

Even when tests pass, the following are not treated as repairs:

- Disabling a test (adding `@Ignore`)
- Swallowing an assertion exception with try/catch
- Weakening an assertion (using `> 2` where `== 3` is correct)
- Reverting the change the developer intended

The paper says these damage developer trust and should not be proposed, and that it is **working on adding an extra check to FlowAgent** confirming "no tests deleted or reverted" before proposing (§4.3.4). Future work lists improving test-deletion and revert behavior, improving latency and success rate, extending to AI-authored changes, and in-progress notifications (§8). **This extra check is not complete.**

## Applying this to our own AI operations

These are adopted as operating policy and are not measures whose effect the paper demonstrated. Application to implementation, reproduction, and effect measurement are not done. Do not use a fixed 30 minutes / 100 calls routinely; apply the idea as per-task interim reports and replanning.

1. **Make requests concrete**: state deliverables, scope of change, completion check, the next report point, and what not to touch. Inspired by FlowAgent narrowing scope with filters and setting limits.
2. **Report being stuck early**: when blocked by something like a TLS or browser failure, tell the PM early what was tried, why it stopped, what artifacts remain, and the next step, instead of iterating aimlessly. Set limits (100 calls / 30 minutes) per task, and switch to an interim report or replanning when exceeded.
3. **Attach the diff and checked scope at completion**: include the diff or commit, the minimum necessary checks, and what is unchecked. More tests is not the goal in itself. Include final verification and filtering out fake repairs (above) in the definition of done.
4. **Hand over state at changeover**: hand over repo / branch / commit, goal, what's done and remaining, attempt results, environment constraints, approved scope, and next step. The same applies to changeover due to token budget.

### Free manual check plan (fictional examples)

Prepare a few small fictional failing tests and change diffs, and have a person check them from these angles. No execution environment or paid tool is needed.

| Check item | Example of fake success | How to catch it |
|---|---|---|
| Test disabling | Adding `@Ignore` / skip | Does the diff add a test attribute? |
| Swallowed exception | Wrapping the assertion in try/catch | Can the check actually fail? |
| Weak assertion | Loosening `==` to `>` | Does the expected value match the spec? |
| Undoing intent | Reverting the original change | Does the diff still contain the original purpose? |
| Completion report | Only "it passed" | Are the diff, checked scope, and unchecked items attached? |

Include fake examples in the check, and use the conditions you missed to improve the request and completion-record formats. Do not assume success.

## Summary

FlowAgent is Google's internal agent for repairing pre-submit, outer-loop test failures (ReAct-style generate-and-validate loop on a fine-tuned internal Gemini 2.5 Pro; up to 100 tool calls or 30 minutes). In a manual evaluation, three experienced developers judged 131 of 195 fixes correct (67.18%; 37 teams). In production since October 2025, it attempted 781,874 of 2,567,829 failing changes, obtained 421,818 fixes, posted 295,508, and developers previewed 65,069 and applied 28,554. Percentages in Table 2 use the preceding stage as denominator; adoption is not accuracy. Success latency (p50 9.85 min, p90 25.83 min) is not comparable to the 27.48-minute median time to a developer's next edit, so no causal time-saving claim follows. Fake repairs (disabled tests, swallowed assertions, weakened assertions, reverted intent) were observed; the extra check is future work. Data are proprietary and results are tied to Google's infrastructure, model, and tests. Primary PDF checked; no reproduction. The secondary AIDB article was not read in full and is not a basis. The four team practices above are adopted as policy, with effects unverified.

[Collection index](README.md) | [Reading list](../../docs/reading-list.md)
