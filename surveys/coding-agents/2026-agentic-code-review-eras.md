**English** | [日本語](2026-agentic-code-review-eras.ja.md)

# From Human-Centric to Agentic Code Review: How Generations of Generative AI Affect Review Quality (1.02M PRs, 207 projects)

## Overview

- **What it is**: An arXiv preprint (2607.13196) analyzing about 1.02 million reviewed pull requests from 207 GitHub projects across three eras of AI code review.
- **What it says**: It compares the pre-LLM, LLM and AI-agent eras and finds that projects adopt AI reviewers in three ways, with faster reviews in the agent era for the Gradual and Rapid AI Agent groups.
- **Caveat**: It is observational and measures only six review smells, not defect detection or comment usefulness, so it does not show that AI reviewers cause better review.

## Key points for people and PMOs

- **What we learned**: about 1.02 million reviewed pull requests (PRs) from 207 GitHub projects were compared across three eras: before AI reviewers (pre-LLM), LLM-assisted (LLM era), and AI-agent (agent era). Projects adopt AI reviewers in three ways (Gradual 46%, Rapid LLM 22%, Rapid AI Agent 32%). Gradual and Rapid AI Agent adoption saw faster reviews in the agent era (−2.5 / −4.5 days/KLOC), but no significant improvement in the review-quality indicators (review smells) was found. Rapid LLM adoption saw more smells.
- **What it is useful for**: evidence for adopting AI reviewers selectively rather than uniformly; and an idea to monitor "dependence on the same reviewer (Review Buddies)" and "concentration on large changes" after AI adoption.
- **Caution**: this is an observational study, and the paper itself says the regression analysis is explanatory, not causal. "Quality" means only those of six review smells that detection rules can measure; accuracy of defect detection and usefulness of comments are not measured. The agent era is a time period, and not every reviewer in it is an agent. The extracted text of Table VI is garbled, so this record uses only the paper's prose for those results.
- **Next step**: this record reflects a reading of the primary source (arXiv HTML v1 in full) only. No PDF cross-check, replication-package check or reproduction was done.

## Survey record

- **Status**: fully read (arXiv HTML v1: body, tables, and the end matter). No PDF cross-check, no close reading of the references, no check of the replication package. Table VI (impact scores of the logistic regressions) is garbled in the extracted text, so individual coefficients are not quoted. No reproduction.
- **Title, authors, year, venue, DOI / arXiv ID, primary URL**: *From Human-Centric to Agentic Code Review: The Impact of Different Generations of Generative AI Technology on Review Quality* / Suzhen Zhong, Shayan Noei, Bram Adams, Ying Zou (Queen's University) / 2026 / peer-reviewed venue unconfirmed (arXiv preprint, cs.SE). [arXiv:2607.13196v1](https://arxiv.org/abs/2607.13196v1) (submitted 2026-07-14 UTC), [HTML](https://arxiv.org/html/2607.13196), [PDF](https://arxiv.org/pdf/2607.13196).
- **Date checked and version examined**: 2026-10-16 (abs page fetched at 11:27 UTC) / v1. The submission history lists only [v1] 2026-07-14, so v1 was the latest version available at the time of checking. We do not claim that no later version will appear. No venue was stated on the page, and it remains unconfirmed.
- **Research question** (§I):
  - RQ1: what are the common AI-reviewer adoption practices, and how do they relate to review quality?
  - RQ2: how do human, LLM and AI-agent collaboration patterns affect review quality?
  - RQ3: how do collaboration patterns relate to traditional factors of review quality (PR characteristics, review activity, participant experience)?
- **Method, data, and comparison conditions**:
  - **Project selection** (§II-A): GitHub advanced search for projects with continuous review activity from May 2022 to February 2026. Criteria: at least 100 stars, created before May 2022, and at least one reviewed PR every month in the window. This gave 2,490 candidates.
  - **Data** (§II-B): reviewed PRs (review events, reviewers, timestamps, decision: accepted if merged, rejected if closed without merge, and comments) collected through the GitHub REST API.
  - **Reviewer labeling**: human / rule-based bot / traditional ML / LLM / AI agent, by manually checking each tool's official documentation. To validate the agent labels, 384 agent-era PRs (95% confidence, 5% margin of error) were inspected: 360 showed evidence of agentic behavior (planning, repository-context retrieval, commit actions); the other 24 had only natural-language comments, but documentation and configuration showed no sign that agentic review was disabled, so they were labeled as agent.
  - **Eras**: per project, defined by the first participation of an LLM or AI-agent reviewer (pre-LLM: before any AI reviewer; LLM era: from the first LLM-involved PR until the first agent-involved PR; agent era: from the first agent-involved PR). **Only projects with more than 400 reviewed PRs in each era were kept, giving 207 projects and about 1.02 million PRs.**
  - **PR types** (§II-C): the 11 types of Watanabe et al. (Table I), assigned by GPT-4.1-mini from the title and description (following Li et al.). Agreement with 384 manual labels was Cohen's κ=0.91.
  - **Review-quality measures** (§II-D): review efficiency = days from PR creation to final decision divided by change size in thousands of lines (days/KLOC; smaller is faster). Six review smells adapted from Doğan and Tüzün (Table II): Sleeping Review (decision takes over two days), Review Buddies (the same reviewer reviews at least 50% of an author's PRs), Large Changeset (over 500 changed lines), Ping-Pong (more than three change-request rounds), Missing Context (empty description or no linked context), Lack of Review (no participant other than the author).
  - **RQ1 method** (§III-A): the monthly era-specific AI-reviewer participation rate was linearly interpolated to 10 points per era, the three eras were concatenated, and the series were clustered with soft-DTW. Three clusters (silhouette 0.40, described as "fair"). Differences in AI participation by PR type use chi-square tests; era comparisons use the Wilcoxon signed-rank test with Bonferroni correction.
  - **RQ2 method** (§III-B): each PR becomes a time-ordered sequence of reviewer types plus the final decision, grouped into collaboration patterns with Markov chains fitted by expectation-maximization. The number of patterns (10) minimizes BIC. Efficiency is ranked with the Scott-Knott ESD test; smells and PR types are compared against human-only review with chi-square tests (Bonferroni).
  - **RQ3 method** (§III-C): logistic regression. The dependent variables are efficiency (within each adoption practice and era, PRs below the median days/KLOC are "efficient"; 9 models) and presence of a smell (the three most prevalent: Review Buddies 46.9%, Sleeping Review 38.6%, Large Changeset 20.6%; 27 models), 36 models in all. Predictors are collaboration pattern (reference: human-only), PR characteristics, review activity and participant experience (Table III). All VIFs are below 5. Models were trained on 90% of the data and AUC was evaluated on the held-out 10%, as described. Impact (Imp%) is the difference between the changed and baseline probability divided by the baseline probability.
- **Claims and evidence**: based on the numbers below and the §III prose (the authors' claims). The recorder's inferences are kept in a separate item.
- **Limitations and threats to validity** (§V, the authors' wording):
  - Construct validity: the agent era is a time period, not a guarantee that every AI reviewer in it is an agent (LLM-involved patterns also occur; older patterns with under 5% support are excluded from the Table V comparisons).
  - Internal validity: the RQ3 logistic regressions are explanatory, not causal.
  - External validity: AI reviewer capabilities change quickly, so the observed associations may shift. The data cover May 2022 to February 2026.
- **Comparison with related work** (§VI, the authors' positioning): human-centric code review studies (review intervals, smell taxonomies, effects of reviewer experience and change characteristics) and evaluations of individual LLM-assisted tools (Cihan et al.: review time may increase; Aðalsteinsson et al.: lower cognitive load; Sun et al.: LLM comments are concise and more likely to lead to code changes). The authors position the work as going beyond individual tools by examining adoption practices and collaboration patterns at project and PR level, and claim "the first large-scale quantitative studies of agentic code review". That novelty is the authors' claim; we did not verify it with an exhaustive prior-work search.
- **Free-to-run reproduction plan**: not done. The paper cites an anonymized replication package (anonymous.4open.science), which we did not fetch or check (and whether it stays reachable is unknown). If obtainable, recomputing descriptives and the time-series clustering and smell-detection rules is a candidate.
- **Usage status**: proposed only (no evidence of trial or adoption).
- **Unconfirmed points and next checks**: existence and content of the replication package, v2 or later, peer-review or acceptance information, a PDF cross-check (especially Figure 2 and Tables IV to VI), reported AUC values (we could not find reported values in the text), and the content of the references.

### Numbers and evaluation unit

**Distribution of adoption practices** (§III-A): Gradual AI Adoption 46%, Rapid LLM Adoption 22% (45 projects, back-calculated from "12 of the 45 (27%) are web applications"), Rapid AI Agent Adoption 32%.

| Practice | LLM participation in LLM era (mean) | Agent participation in agent era (mean) | Notes (text) |
|---|---:|---:|---|
| Gradual | 8% | 36% | domains spread from operating systems to education |
| Rapid LLM | 91% | 93% | higher share of web applications |
| Rapid AI Agent | 19% | 76% | includes 12 Microsoft and 3 Google projects |

**Efficiency and smells by era** (Table IV; \* marks differences the authors call significant; pre-LLM is the baseline)

| Practice | Era | Efficiency (days/KLOC), change | Smell rate, change | Review Buddies, change |
|---|---|---:|---:|---:|
| Gradual | pre-LLM (baseline) | 8.5 | 83.8% | 47.8% |
| | LLM | −1.6 | +3.8 | +15.1 |
| | agent | −2.5\* | +2.0 | +15.6 |
| Rapid LLM | pre-LLM (baseline) | 5.4 | 83.6% | 45.9% |
| | LLM | +0.6 | +8.0\* | +26.0\* |
| | agent | −0.1 | +4.4\* | +23.2\* |
| Rapid AI Agent | pre-LLM (baseline) | 10.4 | 81.0% | 36.4% |
| | LLM | −3.4 | +4.4 | +16.6\* |
| | agent | −4.5\* | +2.5 | +12.4 |

- The smell-rate and Review Buddies changes appear in the table as bare numbers such as "+8.0". The text says "8.0% points" for the smell rate but "26%" for Review Buddies, so percent versus percentage points is inconsistent in the wording (the table values read as amounts added to the baseline).
- Review Buddies in the LLM era of Rapid AI Agent adoption carries a significance mark, but we could not find the RQ1 text (which reports significant smell increases for Rapid LLM) commenting on this.

**PR types and AI participation** (§III-A, Gradual): in the LLM era, LLM reviewers participate at 2.0 times the rate of other types for chore and 1.2 times for fix. In the agent era, agent reviewers participate at 1.4 times for feature and 1.3 times for refactoring.

**Collaboration patterns** (Table V, §III-B): 10 patterns identified (Human-Only, Human-Bot, Human-Bot-ML, LLM-Assist, Multi-LLM, LLM-Bot-Assist, Agent-Init, Agent-Assist, Multi-Agent, Agent-ML-Assist). Table V lists the relevant patterns per era (Human-Only and Human-Bot appear in several eras).
- LLM era: LLM-Assist is less efficient than human-only review under all three practices (R2–R3 vs. R1). Multi-LLM is as efficient as human-only under Gradual and Rapid AI Agent (both R1) but less efficient under Rapid LLM (R2 vs. R1). Under Rapid LLM, all LLM-involved patterns are slower than human-only.
- Agent era: Agent-Init and Multi-Agent are faster than human-only review under Gradual and Rapid AI Agent (R1–R2 vs. R2–R3). Under Rapid LLM there is no significant difference (human-only ranks first, with 61% of its PRs resolved in a two-turn exchange).
- In Multi-LLM, the LLM contributes a median of two comments and in 75% of PRs the human replies with a single comment. In LLM-Assist, the median number of human comments is four, against two in human-only review (cited to the replication package; not checked here).
- In Agent-Init and Multi-Agent, the agent posts a summary of the change in 75–95% of PRs and the human replies briefly (the authors' account, with an example quote).
- Smell prevalence (share of PRs with at least one smell): 69–76% for human-only review (LLM and agent eras) and 78–94% for AI-involved patterns (the authors' statement). It is mainly driven by Review Buddies: 16% for human-only, an average of 60% for LLM-involved and 53% for agent-involved patterns (cited to the replication package; not checked here).

**RQ3 results** (§III-C, impact Imp%; Table VI is garbled, so only the prose is used)
- Efficiency: in the pre-LLM era, author experience and PR characteristics (chore, refactoring) are the main factors; author experience lowers delay by −17 to −22% under all three practices. In the LLM era, patterns involving LLMs or bots tend to increase delay. In the agent era, Multi-Agent and Agent-Init reduce delay under Gradual and Rapid AI Agent adoption; under Rapid LLM adoption traditional factors are no longer significant and AI collaboration patterns are consistently associated with more delay.
- Review Buddies: author experience is positively associated in all eras. Build PRs are negative (Rapid LLM: −43 in the LLM era and −55 in the agent era; chore −39 / −25; refactoring −19 / −12; Rapid AI Agent: build −15, −20, −19 over the three eras). Refactoring under Rapid AI Agent is positive in all three eras (+29, +20, +33).
- Sleeping Review: commit count (+27 to +70) and inline threads (+26 to +51) are consistently positive; author experience, build and chore are negative (−10 to −50). In the LLM era, LLM-Assist and LLM-Bot-Assist are +26 to +214. In the agent era, Multi-Agent and Agent-Init are −16 to −48 under Gradual and Rapid AI Agent; under Rapid LLM, Agent-Init is +42 and Agent-ML +94.
- Large Changeset: agent-involved patterns in the agent era are +25 to +48 (Gradual) and +20 to +54 (Rapid AI Agent).

### Separating the paper's claims from the recorder's inferences

**The paper's claims**

- Gradual and Rapid AI Agent adoption make reviews faster in the agent era without improving smells. Rapid LLM adoption increases smells (+8.0 / +4.4) without an efficiency gain.
- No collaboration pattern consistently beats human-only review on both efficiency and quality. Most AI-involved patterns show more smells (especially Review Buddies) than human-only review.
- Collaboration patterns are the "strongest explanatory factor" for review efficiency once LLM and agent reviewers participate (abstract). The RQ3 summary, however, describes them as a strong factor alongside traditional factors (the wording varies).
- Implications (§IV): adopt AI reviewers selectively based on PR context and observed efficiency and quality; context-aware tooling to decide whether a PR stays human-led, gets lightweight LLM summarization, or gets agent inspection; combine AI with traditional review practices; multi-agent setups to avoid depending on a single default AI reviewer; research on developers' reasons; benchmarks that reflect PR context.

**The recorder's inferences** (not the paper's claims)

- Efficiency is "days to decision divided by change size", so small PRs have a small denominator and a large value. Differences in size distributions could affect the comparison; we found no sensitivity analysis in the text.
- Review Buddies is defined as the same reviewer (human, LLM or agent) reviewing at least 50% of an author's PRs, so it rises when adoption rests on one default bot. Part of the increase in projects where an AI reviewer reviews nearly every PR is therefore a consequence of the definition, and not necessarily lower quality. The paper itself calls the smells indicators of "quality risk".
- "Quality" here excludes defect-detection rate and comment usefulness. The conclusion that efficiency rises without quality improving holds only within these indicators.
- Eras are defined per project by the first AI-reviewer participation, and other changes over the same period (project maturity, tool changes, scale) are not controlled for (we found no such control in the text).

### Text and table points to check (recorded unresolved)

1. **Table VI**: the columns and values are garbled in the extracted text, so individual coefficients cannot be assigned. This record uses only the prose.
2. **Unit wording**: the Review Buddies increase is written as "26%" and "23.2%", while Table IV shows only "+26.0" (percent versus percentage points is unclear).
3. **Strength as a factor**: the abstract says "strongest explanatory factor"; the RQ3 introduction says "a strong explanatory factor alongside traditional review factors".
4. **AUC**: the method is described, but we could not find reported values in the text, so the fit of the models cannot be read.
5. **Cited replication package**: an anonymized link, not checked in this record.

### Scope of verification

- Checked: bibliographic data (title, authors, version, date, category), the submission history, the project-selection criteria and counts (2,490 → 207, about 1.02M PRs), the manual validation of agent labels (360 of 384), the PR-type κ, smell detection rules, the share of adoption practices, consistency of Table IV values with the text, the Table V and collaboration-pattern prose, the RQ3 method and prose, and the threats.
- Not checked: PDF figure and table cross-check, the Table VI coefficients, the replication package, AUC values, the references, and v2 or later.

### Scope of the repository duplicate check

We searched the full text of the **main branch** of the public repository moruku36/independent-cs-research-2026 (after PR #12 was merged; retrieved 2026-10-16) and found no mention of arXiv ID 2607.13196. Other branches and forks were not covered. No open PRs existed at the time of checking.

## Applying this to this repository's practice

These are **this record's proposals**, not measures whose effect the paper demonstrated. Implementation, adoption and effect measurement are not done.

1. When introducing AI reviewers, consider choosing among human-led review, light LLM summarization, and agent inspection by PR type, change size and discussion volume, rather than a uniform setup (in line with the paper's implications).
2. After adopting AI reviewers, monitor Review Buddies (concentration on one reviewer), Large Changeset and Sleeping Review. Account for the bias built into the definitions, and measure defect detection and comment usefulness separately.
3. If measuring in-house, record before and after with the same indicators and unit (days/KLOC), and record when each AI reviewer was introduced.

## 日本語

[From Human-Centric to Agentic Code Review](2026-agentic-code-review-eras.ja.md)（arXiv:2607.13196v1、cs.SE、2026-07-14投稿、プレプリント・会場未確認）：207プロジェクト・約102万PRを、pre-LLM／LLM期／エージェント期で比較。導入は3種（段階的46%、LLM先行22%、エージェント急速32%）。段階的とエージェント急速では効率が向上（−2.5／−4.5日/KLOC）したがスメルの有意な改善はなく、LLM先行ではスメルが増加（+8.0／+4.4）。AI関与の協働パターンは人のみよりスメル（特にReview Buddies）が多い。回帰は説明的で因果ではない。表6は未使用、PDF照合・再現未実施。

Source sections: [§II](https://arxiv.org/html/2607.13196#S2) · [§III-A](https://arxiv.org/html/2607.13196#S3.SS1) · [§III-B](https://arxiv.org/html/2607.13196#S3.SS2) · [§III-C](https://arxiv.org/html/2607.13196#S3.SS3) · [§IV](https://arxiv.org/html/2607.13196#S4) · [§V](https://arxiv.org/html/2607.13196#S5)

[Collection index](README.md) | [Reading list](../../docs/reading-list.md)
