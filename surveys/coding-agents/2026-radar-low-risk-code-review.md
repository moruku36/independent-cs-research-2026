**English** | [日本語](2026-radar-low-risk-code-review.ja.md)

# Automating Low-Risk Code Review at Meta: RADAR, Risk Calibration, and Review Efficiency

## Key points for people and PMOs

- **What we learned**: As agentic AI coding tools accelerated code production at Meta—driving a **+105.9% YoY** increase in significant lines of code per human-landed diff and a **+51% YoY** increase in diffs per developer per month (with **80%+** of growth driven by agentic AI)—human review capacity became a bottleneck. Meta deployed **RADAR (Risk Aware Diff Auto Review)**, a multi-stage automated review and landing funnel combining source-specific eligibility gates, static heuristics, a machine-learned **Diff Risk Score (DRS)**, an LLM-based **Automated Code Review (ACR)** agent (requiring confidence $\ge 8/10$ and zero risk signals), and deterministic CI validation. Across production rollout, RADAR reviewed **535,290 diffs** (peaking at **25,000+ diffs/day**) and automatically landed **331,720 diffs**. Relaxing the DRS threshold from **P25 to P50** increased the 7-day RADAR approve rate to **60.31%** (and human RADAR Verification pass rate to **26.31%**). Safety outcomes remained substantially better than baseline: RADAR-reviewed diffs had **1/3 the revert rate** ($p < 10^{-16}$) and **1/50 the Production Incident (PI) rate** ($p < 10^{-6}$) of non-RADAR diffs. Compared to human-reviewed diffs, RADAR reduced **median time to close by over 330%** and **median diff review wall time by 35%**.
- **What it is useful for**: Scaling code review pipelines under heavy AI/agent diff volume: instead of applying a uniform review policy to all diffs, stratify eligibility by authorship and automation source (blanket approval for vetted deterministic codemods, per-runbook 60-day safety track records and daily volume caps for AI agents, and conservative P5 risk gating with deferred or waived review for human diffs).
- **Caution**: Observational production evaluation inside Meta's monorepo environment (Phabricator, mature CI, canary deployment, and an established ML Diff Risk Score platform). Diffs are not randomly assigned to RADAR; lower revert and PI rates reflect strict selection of low-risk diffs rather than causal superiority of LLM review over human review on equivalent-risk changes. Underlying diff-level datasets and full difference-in-differences specifications are proprietary and not publicly released.
- **Next step**: Primary source (arXiv PDF v2 / HTML v2) read in full. No reproduction performed due to proprietary internal infrastructure and telemetry.

## Survey record

- **Status**: fully read (arXiv PDF v2: body, figures, tables, and bibliography). No reproduction (proprietary Meta monorepo infrastructure and telemetry).
- **Title, authors, year, venue, DOI / arXiv ID, primary URL**: *Automating Low-Risk Code Review at Meta: RADAR, Risk Calibration, and Review Efficiency* / Chris Adams, Arjun Singh Banga, Parveen Bansal, Souvik Bhattacharya, Payal Bhuptani, Rujin Cao, Pedro Canahuati, Nate Cook, Brian Ellis, Prabhakar Goyal, Gurinder Grewal, Tianyu He, Matt Labunka, Alex Manners, David Molnar, Ging Cee Ng, Vishal Parekh, Jiefu Pei, Frederic Sagnes, James Saindon, Will Shackleton, Sid Sidhu, Gursharan Singh, Karthik Chengayan Sridhar, Matt Steiner, Pratibha Udmalpet, Sean Xia, Stacey Yan, Audris Mockus, Peter Rigby, Nachiappan Nagappan (Meta) / 2026 / DOI: `10.1145/3643774` (arXiv preprint, cs.SE). [arXiv:2605.30208v2](https://arxiv.org/abs/2605.30208) (v1 submitted 2026-05-28, v2 revised 2026-06-12), [HTML v2](https://arxiv.org/html/2605.30208v2), [PDF](https://arxiv.org/pdf/2605.30208).
- **Date checked and version examined**: 2026-10-18 (PDF v2 checked) / v2.
- **Research questions** (§1, §3, Table 2):
  - RQ1 (Feasibility): Can risk-stratified automation operate at production scale, absorbing a meaningful share of review volume across diverse organizational contexts?
  - RQ2 (Calibration): How does adjusting the risk threshold governing automation eligibility affect the trade-off between automation yield and safety outcomes?
  - RQ3 (Impact): To what extent does automated review reduce end-to-end review latency for AI-generated code changes?
- **Method, data, and comparison conditions** (§2, §3):
  - **Motivation and background systems** (§2.1–§2.5):
    - *RACER (Risk-Aware Code Editing and Refactoring)*: Meta's GenAI agent for bulk code maintenance via pre-configured prompt "runbooks" (dead code removal, cyclomatic complexity reduction, lint/test fixes, migrations), landing ~3,000 diffs/week (59% without human revisions).
    - *Diff Risk Score (DRS)*: ML model predicting Production Incident (PI) likelihood (e.g., flagging 10% of diffs catches 60% of PI-causing changes), expressed as percentile $P_X$ (only safest $X\%$ qualify).
    - *Automated Code Review (ACR / DCR)*: LLM review agent classifying diff changes against *safe signals* (non-behavioral refactoring, dead code removal, defensive checks, logging, formatting, docs, import hygiene, tests, static resources) and *risk signals* (complexity score $\ge 4$, structural changes, logic bugs, performance/security risks). Auto-acceptance requires confidence $\ge 8/10$ and zero risk signals.
  - **Differentiated Diff Eligibility Model** (§2.7–§2.9, Table 1, Figures 2–4):
    - *Deterministic Codemods (CodemodService)*: **Blanket AutoAccept**—vetted at the codemod level; bypasses per-diff ACR and DRS gating.
    - *AI-Generated Codemods*: **Conditional AutoAccept** via **ACE (AI Commit Eligibility)** pipeline—requires static safety checks, DRS gating, and per-diff ACR evaluation.
    - *RACER Runbooks*: Per-runbook eligibility checks (60-day clean risk history with 0 PIs and low revert/rejection rates; daily landing caps of 10–2,000 diffs/day; DRS threshold P50 for allowlisted runbooks vs. P20 default for non-allowlisted; keyword/incident denylist) $\rightarrow$ ACE pipeline $\rightarrow$ configurable auto-land delay (e.g., 24h queue where humans can still reject).
    - *Human-Authored Diffs*: Two-step pipeline: (1) **RADAR Verification** checks author eligibility (SWE/DE/DS or $>10$ diffs/yr, $\ge 60$ days tenure for interns, active oncall rotation), scope exclusions (no OSS, SOX, code freeze, or blocklisted files/phrases), allowed CI state, ACR review, and default **P5 DRS threshold** to allow immediate shipping with *deferred post-land human review*; (2) **RADAR Approval** applies stricter criteria to waive deferred review entirely.
    - *Organizational configurability*: Controlled per org via `OrgRADARPolicyConfig`.
  - **Evaluation design** (§3, Tables 2–3):
    - *RQ1*: Descriptive operational telemetry across 535,290 RADAR-reviewed diffs and 331,720 RADAR-landed diffs; Fisher's exact tests comparing revert and PI rates against non-RADAR diffs.
    - *RQ2*: Observational before–after comparison when relaxing the DRS threshold from P25 to P50, tracking L7 (7-day) RADAR approve rate, RADAR Verification pass rate, reverts, and PIs.
    - *RQ3*: Large-scale difference-in-differences style observational comparison estimating median time to close and median diff review wall time reductions across 535K+ RADAR-reviewed diffs.
- **Claims and evidence**: Supported by production telemetry across 535,290 reviewed diffs (§4, Tables 4–6).
- **Limitations and threats to validity** (§6):
  - *Generalizability*: Relies on Meta's unified monorepo, Phabricator workflow, mature CI/canary infrastructure, and pre-existing DRS ML platform; exact dates and diff-level datasets are withheld for confidentiality.
  - *Construct validity*: Time to close and review wall time measure queueing latency rather than defect prevention or long-term code maintainability. Revert and PI rates do not capture non-incident regressions or precautionary reverts, and human-authored diffs may themselves include AI assistance.
  - *Internal validity*: Non-random assignment to RADAR (eligible diffs are intentionally lower risk); threshold relaxation from P25 to P50 occurred alongside evolving onboarding and validation rules; full econometric specification for the difference-in-differences model is not disclosed.
- **Comparison with related work** (§5):
  - Inverts traditional risk-aware review tooling (e.g., Mockus & Weiss 2000; Kamei et al. 2016; Rigby et al. 2025 reviewer recommendation; Shan et al. 2022 review nudges): instead of alerting human reviewers to high-risk changes, RADAR uses risk prediction and LLM semantic classification to *remove* human reviewers from low-risk changes.
  - Complements [From Human-Centric to Agentic Code Review](2026-agentic-code-review-eras.md) and [FlowAgent](2026-flowagent.md) by documenting how enterprise review pipelines absorb the 51% YoY surge in developer diff volume caused by coding agents ([CLI Coding Agents at Microsoft](2026-cli-coding-agents-adoption-impact.md)).
- **Free-to-run reproduction plan**: In a GitHub Actions workflow on a personal repository, prototype a lightweight two-stage gate combining deterministic path/size filters with an LLM diff classifier (requiring zero risk signals across security/logic categories) to label low-risk PRs (`docs`, `tests`, dead-code cleanup) for fast-track merge.
- **Usage status**: Deployed in production at Meta across multiple organizations; architectural pattern proposed for CI/CD review gating.
- **Unconfirmed points and next checks**: Exact observation calendar dates, baseline raw revert/PI percentages for non-RADAR diffs, and the full regression specification for RQ3's difference-in-differences model.

### Numbers and evaluation unit

**RADAR Diff Eligibility Criteria by Source Type (§2.7–§2.9, Table 1)**:

| Criterion | Deterministic Codemod | AI Codemod | RACER Runbook | Human Author |
|---|---|---|---|---|
| **Pipeline** | Blanket AutoAccept | ACE | ACE | RADAR Verification + Approval |
| **Per-diff AI review (ACR)** | No | Yes (ACR, conf $\ge 8/10$) | Yes (ACR, conf $\ge 8/10$) | Yes (ACR, conf $\ge 8/10$) |
| **DRS ML risk gating** | No | Yes (P20 default) | Yes (P50 allowlisted / P20 default) | Yes (P5 default, per-org configurable) |
| **Risk history required** | No (codemod-level review) | No | Yes (60-day lookback: 0 PIs, low reverts) | No |
| **Daily volume limits** | No | No | Yes (10 to 2,000 diffs/day per runbook) | No |
| **Author / source vetting** | Codemod approval | Codemod config review | Runbook onboarding | Eligible role/tenure ($>10$ diffs/yr or $\ge 60$d intern) + oncall |
| **Scope exclusions** | Standard (no OSS/SOX) | Standard (no OSS/SOX) | Standard + keyword/incident denylist | Standard + file/phrase blocklists |

**Production Scale, Calibration, and Efficiency Outcomes (§1, §2.2, §4, Tables 4–6)**:
```
- Scale Pressure Context at Meta (YoY):
  - Significant LoC per human-landed diff: +105.9% YoY
  - Diffs per developer per month: +51% YoY (80%+ attributed to agentic AI assistance)
  - RACER agent baseline volume: ~3,000 landed diffs/week (59% landing without human revisions)

- RQ1 (Feasibility & Production Scale, Table 4):
  - Total RADAR-reviewed diffs: 535,290 (535K+)
  - Total RADAR-landed diffs: 331,720 (331K+)
  - Peak daily throughput: 25,000+ diffs/day RADAR-reviewed
  - Revert rate (RADAR vs. non-RADAR): 1/3 the rate of non-RADAR diffs (Fisher's exact test p < 1e-16)
  - Production Incident (PI) rate: 1/50 the rate of non-RADAR diffs (Fisher's exact test p < 1e-6; 0 PIs deemed catchable by human review)

- RQ2 (Risk Calibration: Relaxing DRS Threshold from P25 to P50, Table 5):
  - Current RADAR approve rate (L7): 60.31%
  - Current RADAR Verification pass rate (L7): 26.31%
  - Post-calibration safety across 535K+ diffs: maintained at 1/3 revert rate and 1/50 PI rate

- RQ3 (Review Efficiency Impact vs. Human-Reviewed Diffs, Table 6):
  - Median time to close: >330% reduction
  - Median diff review wall time: 35% reduction
```

[Survey Collection v2 Index](README.md) | [Repository README](../../README.md)
