**English** | [日本語](2026-cli-coding-agents-adoption-impact.ja.md)

# Adoption and Impact of Command-Line AI Coding Agents: A Study of Microsoft's Early 2026 Rollout of Claude Code and GitHub Copilot CLI

## Overview

- **What it is**: An arXiv preprint (2607.01418) from Microsoft studying the early-2026 rollout of Claude Code and GitHub Copilot CLI to tens of thousands of engineers.
- **What it says**: It examines who tries and keeps using the tools (social exposure from peers and managers matters most) and whether use goes with more merged pull requests.
- **Caveat**: Merged PRs are only an output proxy and the models are observational, so social contagion cannot be separated from similarity and the PR gain is not shown to be causal.

## Key points for people and PMOs

- **What we learned**: A large-scale observational study tracked tens of thousands of Microsoft software engineers during the early-2026 enterprise rollout (Jan 5 – Apr 29, 2026) of two command-line AI coding agents: GitHub Copilot CLI and Anthropic's Claude Code. In the adoption study (Copilot CLI), initial trial was heavily driven by social exposure (skip-level peers +216% odds, direct manager +82%, reviewer peers +54%). Prior IDE Copilot usage increased the odds of trying the CLI tool (+49% to +83%) but reduced retention odds (−12% to −15%). Retention was instead predicted by high baseline coding activity (+31% for >=2 PRs/week). In the outcomes study, early adopters experienced a +24.0% lift in merged PRs per engineer per day (CausalImpact synthetic-control, 95% CI [+14.5%, +33.7%]), which persisted across the 4-month window (+29.4% Feb vs +20.0% Mar–Apr). Within-person dose-response showed a monotone increase from +15.0% at 3 tool days/week to +50.1% at 5+ days/week. In single-tool comparisons, Copilot CLI adopters saw 2.2x the PR lift of Claude Code adopters (+24.9% vs +11.4%, p < 0.0001).
- **What it is useful for**: Planning organizational rollouts of CLI-based coding agents: prioritize peer visibility, manager adoption, and active coders over demographic targeting. Expect IDE Copilot veterans to need distinct use-case guidance rather than assuming automatic retention.
- **Caution**: The study measures merged pull requests as an output proxy, which may reward smaller or split PRs and does not capture code quality, defect density, or architectural complexity. The adoption models are observational and cross-sectional (cannot distinguish social contagion from homophily). The dose-response is associative, not causal (tool-heavy weeks may involve lighter tasks). Both tools were evaluated inside Microsoft, where Copilot CLI enjoyed native integration and organizational alignment. The authors are Microsoft employees.
- **Next step**: Primary source (arXiv HTML v1) read in full. No replication package or raw telemetry re-analysis was conducted due to proprietary enterprise data.

## Survey record

- **Status**: fully read (arXiv HTML v1: body, figures, tables, bibliography, and acknowledgments). No PDF cross-check, no reproduction (internal proprietary telemetry and HR data).
- **Title, authors, year, venue, DOI / arXiv ID, primary URL**: *Adoption and Impact of Command-Line AI Coding Agents: A Study of Microsoft's Early 2026 Rollout of Claude Code and GitHub Copilot CLI* / Emerson Murphy-Hill, Jenna Butler, Alexandra Savelieva (Microsoft) / 2026 / peer-reviewed venue unconfirmed (arXiv preprint, cs.SE). [arXiv:2607.01418v1](https://arxiv.org/abs/2607.01418v1) (submitted 2026-07-01 UTC), [HTML](https://arxiv.org/html/2607.01418v1), [PDF](https://arxiv.org/pdf/2607.01418).
- **Date checked and version examined**: 2026-10-17 (HTML v1 checked) / v1. The arXiv submission history records [v1] 2026-07-01. No subsequent version or formal conference/journal venue was listed at the time of checking.
- **Research questions** (§4.1, §5):
  - RQ1: Among engineers who could have used Copilot CLI but had not yet, who tries it first?
  - RQ2: Among engineers who adopted Copilot CLI, who keeps using it?
  - RQ3: Does using agentic command-line tools lead to more merged PRs?
  - RQ4: Does the specific tool matter — is Claude Code different from Copilot CLI?
  - RQ5: Among engineers who use these tools, who benefits most?
- **Method, data, and comparison conditions**:
  - **Setting and observation window** (§3, §4.2, §5.1): Microsoft rollout in early 2026. Rollout cutoff set at January 5, 2026. Pre-period for predictors runs October 1, 2025 – January 4, 2026 (13 weeks). Post-period observation runs January 5 – April 29, 2026 (16 weeks / 115 days), ending before internal transitions off Claude Code took effect. For the CausalImpact model, the pre-period spans October 1, 2024 – January 4, 2026 (461 days).
  - **Adoption study sample and exclusions** (§4.2): All Microsoft employees with software engineer job titles eligible for Copilot CLI at rollout. Dropped: members of two large divisions with broad Claude Code access, individual Claude Code licensees outside those divisions, retracted Claude Code licensees, and pre-rollout Copilot CLI preview users. Sample comprises "tens of thousands of engineers."
  - **Adoption statistical models** (§4.5):
    - *Initial-use (RQ1)*: Discrete-time logistic hazard model on engineer-week panel ($A_{i,w}=1$ on first use week). Predictors: career stage (IC2–IC6, M4–M6; ref IC4), tenure (<1y, 1–2y, 2–5y, 15+y; ref 5–15y), baseline PR activity (<=1, 1–2, 2+ PRs/wk; ref 0), prior IDE Copilot use (1–14, 15–60, 60+ days; ref 0), and time-varying social exposure in prior 14 days (reviewer peers, skip-level peers, direct manager). Controlled for calendar week fixed effects, broad-division fixed effects, and clustered standard errors on engineer.
    - *Retention (RQ2)*: Cross-sectional logistic regression on adopters active on >=5 of the 14 days beginning with first use. Excluded adopters whose first use was within 14 days of window close.
  - **Outcomes study sample and models** (§5.1, §5.2):
    - *Metric*: Merged pull requests completing within 28 days of creation (from Azure DevOps). Restricted to active engineers (>=2 merged PRs in 4-week pre-period) with P5–P95 trimming of pre-period PR counts.
    - *Part 1 (Synthetic control)*: Bayesian Structural Time-Series (BSTS) via CausalImpact. Adopters with tool activity in intervention week Jan 5–11, 2026 vs non-adopter control pool (randomly partitioned into 10 daily-mean regressor groups). 461-day pre-period, 115-day post-period.
    - *Part 2 (Within-person)*: Fixed-effects Poisson regression on panel of all adopters (including dual-tool users), with engineer fixed effects ($\alpha_i$) and week fixed effects ($\tau_w$). Standard errors clustered on engineer.
    - *Dose-response*: Weekly tool-use days binned into {0, 1, 2, 3, 4, 5+}.
    - *Tool comparison*: Restricted to single-tool users; binary indicators for any Copilot CLI vs any Claude Code use in a week; Wald test on contrast.
    - *Heterogeneous effects*: Continuous linear dose (days/week) interacted with career stage and tenure, evaluated at 3 days/week; FDR controlled via Benjamini–Hochberg ($\alpha=0.05$).
  - **Qualitative survey** (§4.6): Post-event survey of 609 attendees at Microsoft's internal "Agentic Engineering Day," analyzed for recurring themes.
- **Claims and evidence**: Based on the numbers below and §§4–5 text.
- **Limitations and threats to validity** (§6):
  - *Construct validity*: 5-of-14 retention threshold is arbitrary (sensitivity checks at 3-of-14 and 7-of-14 showed consistent fits). 28-day PR completion window truncates long-running PRs. Merged PR count is a throughput proxy that rewards smaller, frequent PRs and ignores code quality, technical debt, and defect creation.
  - *Internal validity*: Cross-sectional adoption study cannot separate peer contagion from homophily (clustering of similar engineers). Dose-response is an observational association; high-tool-use weeks might coincide with lighter or more automatable task mixes. Single-tool contrast excludes multi-tool developers.
  - *External validity*: Single corporate environment (Microsoft) with enterprise-specific infrastructure; PRs tracked via Azure DevOps only. Four-month window cannot assess multi-year adoption or delayed productivity drag.
  - *Researcher positionality*: Authors are Microsoft employees; Microsoft develops and sells AI tools and owns GitHub.
- **Comparison with related work** (§2, §5.1, §7):
  - *He et al. (MSR 2026)*: Reported that productivity gains from Cursor faded after 2–3 months in OSS. Murphy-Hill et al. find sustained gains across 4 months (+29.4% Feb vs +20.0% Mar–Apr), attributing differences to tool generation (CLI agents vs 2024–2025 IDE assistants) and within-person unit of analysis avoiding compositional drift.
  - *Daniotti et al. (2026), Yang (2026), Robbes et al. (2026)*: Identified adopters via public git commit trailers or config files, lacking an eligible non-adopter denominator. This study directly observes the entire eligible population.
  - *Heilman et al. (2026)*: Replicated within-person fixed-effects dose-response framework for CLI agents, matching findings that throughput scales with usage intensity.
- **Free-to-run reproduction plan**: Not performed. Telemetry, HR career/tenure records, and internal Azure DevOps PR logs are proprietary to Microsoft. Public reproduction without access to internal telemetry is impossible.
- **Usage status**: Adopted and trialed internally at Microsoft; operational deployment recommendations proposed for other engineering organizations.
- **Unconfirmed points and next checks**: Peer-reviewed publication venue; total exact headcount figures (redacted to "tens of thousands"); downstream defect, incident, and code complexity impacts; evaluation in non-Microsoft enterprise environments.

### Numbers and evaluation unit

**Adoption and Retention Predictors (Copilot CLI, §4.7, Figures 1–5)**:
*Values represent percent change in odds relative to reference category; CI=95% confidence interval.*

| Predictor Group | Level / Bucket | Initial-Use Odds Shift (RQ1) | Retention Odds Shift (RQ2) |
|---|---|---:|---:|
| **Social Exposure: Skip-level peers** | 1–10% | +38% (sig) | +12% (sig) |
| | 10–25% | +118% (sig) | +41% (sig) |
| | 25+% | **+216%** (sig) | **+66%** (sig) |
| **Social Exposure: Direct manager** | Manager used CLI | **+82%** (sig) | **+22%** (sig) |
| **Social Exposure: Reviewer peers** | 1–10% | +14% (sig) | +11% (sig) |
| | 10–25% | +32% (sig) | +24% (sig) |
| | 25+% | **+54%** (sig) | **+48%** (sig) |
| **Prior IDE Copilot Use** | 1–14 active days | +49% (sig) | **−12%** (sig) |
| *(Ref: 0 days)* | 15–60 active days | +71% (sig) | **−14%** (sig) |
| | 60+ active days | **+83%** (sig) | **−15%** (sig) |
| **Baseline PR Activity** | <= 1 PR/week | +19% (sig) | +13% (sig) |
| *(Ref: 0 PRs/week)* | 1–2 PRs/week | +24% (sig) | +14% (sig) |
| | 2+ PRs/week | **+34%** (sig) | **+31%** (sig) |
| **Career Stage** | IC2 (Junior) | **−13%** (sig) | noisy / sig |
| *(Ref: IC4 Mid-level)* | IC3 | **−14%** (sig) | not sig |
| | IC5 (Senior) | **+22%** (sig) | not sig (~0%) |
| | IC6 (Staff/Principal) | +18% (sig) | not sig (~0%) |
| | M4–M6 (Managers) | not sig (~0%) | not sig (~0%) |
| **Tenure** | < 1 year | **+11%** (sig) | not sig |
| *(Ref: 5–15 years)* | 1–2y, 2–5y, 15+y | not sig (within ~2%) | not sig |

**Outcomes Study: Productivity Lift and Persistence (§5.1, §5.2)**:

- **CausalImpact headline lift (RQ3 Part 1)**: **+24.0%** in daily merged PRs per engineer [95% CI: +14.5%, +33.7%], posterior tail-area $p < 0.001$.
- **Lift persistence over time**:
  - February 2026: **+29.4%** [95% CI: +17.7%, +44.4%]
  - March 1 – April 29, 2026: **+20.0%** [95% CI: +7.4%, +35.9%]
  - Difference between months is within sampling noise (credible intervals substantially overlap and both exclude 0).
- **Placebo check**: Artificial intervention on 2025-10-06 yielded −1.1% [95% CI: −10.6%, +8.6%], confirming absence of pre-existing trajectory divergence.
- **Within-person dose-response (RQ3 Part 2, Figure 7)**:
  - 1 day/week: +4.2%
  - 2 days/week: +9.1%
  - 3 days/week: **+15.0%**
  - 4 days/week: +28.3%
  - 5+ days/week: **+50.1%** (relative to 0-day weeks of same engineer).
- **Tool comparison (RQ4, Figure 8, single-tool users)**:
  - Claude Code: **+11.4%** [95% CI: +9.4%, +13.6%]
  - Copilot CLI: **+24.9%** [95% CI: +23.0%, +26.8%]
  - Copilot CLI lift is **2.2x** that of Claude Code ($p < 0.0001$).
- **Subgroup moderators at 3 days/week (RQ5, Figures 9–10)**:
  - IC4 reference lift: **+21.3%** [95% CI: +19.6%, +23.0%]. Junior ICs (IC2–IC3) and senior managers experienced higher relative lifts.
  - 5–15y tenure reference lift: **+21.5%** [95% CI: +19.9%, +23.1%]. Shows a "C" shape: <1y tenure (caveat: onboarding confound) and 15+y tenure showed higher lifts.

### Separating the paper's claims from the recorder's inferences

**The paper's claims**:
- Initial adoption of CLI coding agents spreads primarily through organizational and peer social networks (skip-level peers and direct managers having the highest impact).
- Prior IDE Copilot use facilitates trial of Copilot CLI but actively hinders retention (−12% to −15%), suggesting developers with satisfactory IDE workflows revert to them.
- Sustained retention is driven by active code shipping (baseline PR volume) rather than role demographics.
- CLI AI coding agents generate an average +24.0% lift in merged PR throughput that does not exhibit early novelty decay over a 4-month window.
- Copilot CLI produced more than double the merged PR throughput lift of Claude Code within Microsoft's environment (+24.9% vs +11.4%).
- High tool usage scales non-linearly, reaching +50.1% for engineers using the tools 5+ days a week.

**The recorder's inferences (interpretation for CLI AI coding agent operations)**:
- *PR size and slicing bias*: A +24% increase in merged PRs may partly reflect developers splitting tasks into smaller chunks suited for CLI agent execution (e.g. decomposing a large feature into separate PRs) rather than a net 24% increase in delivered feature value.
- *Tool disparity context*: The 2.2x performance gap between Copilot CLI and Claude Code likely reflects internal enterprise friction: Copilot CLI was deeply integrated into Microsoft's internal dev fabric, corporate auth, and Azure DevOps repositories, whereas Claude Code had restricted licensing and less customized tooling integrations. It should not be generalized as a standalone model-intelligence comparison.
- *The IDE vs CLI agent tension*: The negative retention effect for IDE Copilot users highlights an operational hazard: engineers comfortable with inline completions may find terminal-based agent loops disruptive or duplicative unless given specific tasks (scaffolding, multi-file refactoring, end-to-end test generation) where CLI agents excel.
- *Token ROI considerations*: As noted in the paper's introduction, CLI agents consume millions of tokens ($5/M tokens on premium models). While merged PR throughput rises, total cost of ownership (TCO) must be weighed against whether the extra PRs provide business value or superficial code expansion.

### Text and table points to check (recorded unresolved)

1. **Exact sample counts**: The paper describes the sample as "tens of thousands of engineers" but conceals exact headcounts and division names for corporate confidentiality.
2. **Onboarding confound**: The large moderation effect observed for <1y tenure engineers may conflate normal developer onboarding trajectory with tool impact, despite excluding engineers with <6 months tenure.
3. **Task mix asymmetry**: The difference between Claude Code and Copilot CLI does not control for task selection (e.g., whether Claude Code was chosen for exploratory/complex architecture and Copilot CLI for routine PR throughput).
4. **Code quality and defects**: The study explicitly leaves code quality, security vulnerabilities, and review turnaround times for future work.

### Scope of verification

- **Checked**: Full text of arXiv:2607.01418v1 HTML (Sections 1–8, Acknowledgments, References [1]–[45]), figures 1–10, regression specifications (Equations 1–3), time horizons, statistical tests (BSTS CausalImpact, fixed-effects Poisson, Benjamini–Hochberg corrections), and validity threats.
- **Not checked**: Direct inspection of underlying telemetry notebooks, raw Azure DevOps pull request data, Microsoft HR records, or proprietary internal tool logs. No replication code was run.

### Scope of the repository duplicate check

We searched the full text and git history of the **main branch** of public repository `moruku36/independent-cs-research-2026` (as of commit `6b195205f6984acf7a6d66bababcf8d7d69c6c34`, 2026-10-17). No references to `2607.01418` were found. Open PRs were checked via `gh pr list` and none were present.

## Applying this to this repository's practice

These are **this record's operational proposals**, not measures evaluated in the paper. Implementation, adoption, and effect measurement remain unperformed.

1. **Rollout strategy via visible peer workflows**: When introducing CLI coding agents (e.g., Claude Code, Copilot CLI, Gemini CLI), leverage social proof and peer demonstrations (brownbags, shared command snippets) rather than top-down policy mandates.
2. **Targeting active coders**: Focus initial licenses on contributors who already ship pull requests regularly, as they have established workflows capable of integrating agentic output and show the highest retention.
3. **Differentiating CLI from IDE tools**: Provide explicit operational guidance distinguishing inline autocomplete (IDE) from multi-step agentic tasks (CLI test repair, repository exploration, batch refactoring) to prevent veteran IDE users from abandoning CLI tools.
4. **Measuring quality alongside throughput**: Pair any internal PR-volume tracking with code review smell metrics (e.g., review duration, defect escape rates, churn) to ensure higher PR velocity does not mask technical debt.

## 日本語

[コマンドラインAIコーディングエージェントの導入と影響](2026-cli-coding-agents-adoption-impact.ja.md)（arXiv:2607.01418v1、cs.SE、2026-07-01投稿、プレプリント・会場未確認）：Microsoftの2026年初頭におけるCopilot CLIおよびClaude Codeの社内展開（数万人規模、2026年1月〜4月）を調査。導入調査では、初期試用は上位マネージャーや同僚の利用といった社会的要因が強く牽引（スキップレベル同僚で最大+216%）。以前のIDE Copilotヘビー利用者は試用率が高いものの定着率が有意に低下（−12%〜−15%）。成果調査（CausalImpact）ではマージ済みPR数が日あたり+24.0%増加し、4ヶ月間持続（2月+29.4%、3〜4月+20.0%）。個人内用量反応では週5日以上利用で+50.1%に達した。Copilot CLI利用者はClaude Codeの2.2倍のPR増加を示した（+24.9% vs +11.4%）。PR数はスループットの代理指標でありコード品質や価値は未計測。一次HTML全文読了、テレメトリ非公開のため追試未実施。

Source sections: [§1](https://arxiv.org/html/2607.01418v1#S1) · [§2](https://arxiv.org/html/2607.01418v1#S2) · [§3](https://arxiv.org/html/2607.01418v1#S3) · [§4](https://arxiv.org/html/2607.01418v1#S4) · [§5](https://arxiv.org/html/2607.01418v1#S5) · [§6](https://arxiv.org/html/2607.01418v1#S6) · [§7](https://arxiv.org/html/2607.01418v1#S7) · [§8](https://arxiv.org/html/2607.01418v1#S8)

[Collection index](README.md) | [Reading list](../../docs/reading-list.md)
