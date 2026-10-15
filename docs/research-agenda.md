**English** | [日本語](research-agenda.ja.md)

# Research Candidates Built on Public Work, 2026

Checked 2026-10-11 JST (2026-10-10 UTC). **Everything below is a research plan. An exhaustive novelty check, the proposed comparison experiments, and an assessment of acceptance likelihood have not been done.** Existing tests and past run records in the repositories are not treated as results of new research experiments.

## Starting point

The 2023 report "DevSecOps スキームにおいて脆弱性逓減を可能にする OSS ベースの環境調査" (an OSS-based environment survey enabling vulnerability reduction in a DevSecOps scheme) is held in the [JAIST official repository](https://dspace.jaist.ac.jp/dspace/handle/10119/18754) as a project research report by Kentaro Mori. [The author's own slides](https://speakerdeck.com/moruku36/devsecops-sukimunioitecui-ruo-xing-di-jian-woke-neng-nisuruoss-besunohuan-jing-diao-cha) describe a DevSecOps environment built from OSS on Azure with multiple security checks. The aim is to connect this research history to evaluating today's public tools.

Owning a public repo is not taken to mean the author wrote all the code in it alone. When writing a paper, distinguish upstream OSS, the author's and collaborators' contributions, AI assistance, and licenses, and pin the commits that are cited.

## Proposed priority

1. **Evidence conditions that reduce misjudgment of scan diffs**: strongly connected to past research, and it can start small using existing code and synthetic fixtures. First candidate.
2. **Added effect and cost of independent multiple AI reviews**: strongly tied to practical interest, but there is a lot of close prior work, so comparison against existing methods and independence of data matter.
3. **Judging cloud cleanup completion without misreading it**: easy to turn cloud-operations experience into research. Start by fixing metrics and failure taxonomy in a simulated environment, and treat generality to real clouds as a later stage.

This order reflects ease of preparation and clarity of evaluation, not ranking of academic novelty.

## Idea 1: Evidence conditions that reduce misjudgment of scan diffs

### Research question

When comparing vulnerability scans before and after, if we check scanner version, DB, configuration, scope, and evidence of completed execution, how much can we reduce the error of "judging it improved when the runs are not comparable", compared with just diffing detection counts or identifiers? And in exchange, how many comparable pairs do we reject?

### Public work that can be used

The [README of trivy-remediation-evidence](https://github.com/moruku36/trivy-remediation-evidence/blob/2d29efa09f29869de68793231cc801765c98cf2b/README.md) shows a design that builds a deterministic comparison result from before/after Trivy JSON and an explicit manifest, and refuses comparison when evidence is lacking. The [fixture index](https://github.com/moruku36/trivy-remediation-evidence/blob/2d29efa09f29869de68793231cc801765c98cf2b/outputs/fixtures/index.json) has 20 cases covering DB changes, missing scope, execution failure, and ambiguous identity. The [reason codes](https://github.com/moruku36/trivy-remediation-evidence/blob/2d29efa09f29869de68793231cc801765c98cf2b/outputs/schemas/reason-catalog.json) are also public. What was confirmed here is the content of public files, not new execution results.

### Verify the difference from prior work

The official Trivy docs explain that false positives and false negatives vary with detection targets, advisory selection, and detection priority, and that exit code 0 does not mean no vulnerabilities. [Detection spec](https://trivy.dev/docs/latest/scanner/vulnerability/) · [Exit codes](https://www.trivy.dev/docs/dev/guide/configuration/others/)

"A Reality Check on SBOM-based Vulnerability Management" (2025) treats warnings caused by SBOM accuracy and unreachable code. [Abstract of the primary paper](https://arxiv.org/abs/2511.20313). This idea does not estimate whether an individual vulnerability is actually exploitable; its theme is **checking the conditions under which before/after observations are comparable**. Still, we need to compare full texts and public implementations to confirm it does not already solve the same problem as existing work on SBOM/VEX, scanner diffs, and measurement reproducibility. A new tool name alone is not a contribution.

### Required data and minimal experiment

- Use the existing 20 fixtures for design and sanity checks. For evaluation, prepare separately about 30 unused synthetic before/after pairs whose creation rules are fixed in advance.
- Condition changes include DB, configuration, scope, execution state, identity, and legitimate content changes. Include normal controls with no condition change.
- Compare three judges: detection count only, set difference over stable finding identity, and the proposed manifest-based judgment. Do not confuse simple baselines with the performance of real products.
- Ground truth is the change embedded at generation time and labels made without looking at judge output. If possible, have a third party recheck some labels.
- Metrics are false-accept rate on non-comparable pairs, false-reject rate on comparable pairs, agreement of reason classification, and processing time. Always show denominators and per-case errors.

The first round can run entirely on local synthetic data. If moving to real images, align license-checked pinned digests, scanner versions, DB snapshots, and effective configuration. Do not conclude remediation is complete, or the application is safe overall, from a new scan not detecting anything.

### Limitations and venue

Synthetic cases alone cannot estimate real-world frequency. An evaluation built only from the existing fixtures leaks in the design's favor. The first report should center on "conditions of comparability, taxonomy of false accepts, and a public benchmark" for CSEC, with real-data validation as the next stage.

## Idea 2: Added effect and cost of independent multiple AI reviews

### Research question

For the same code diff, does a review that does not see others' findings detect additional reproducible serious defects compared with the implementer's own re-review or sequential review? Can we separate the effect of model differences from the effect of simply adding more inference runs or budget?

### Public work that can be used

The [independent-review prompt in multi-ai-workflow](https://github.com/moruku36/multi-ai-workflow/blob/cbacf842a30ed1d485eb37ee8ce1fad555b7a444/configs/level4-claude/review_prompt.md) prioritizes important findings with evidence and reproduction steps and treats uncertain claims as unconfirmed. [ai-engineering-factory](https://github.com/moruku36/ai-governance-control/tree/2525cbbdaf17947dcdd20943afb9098b8cb30c5e) is a candidate base that distinguishes collected evidence from verification and completion. It is not treated as having implemented automatic code generation, automatic merge, or automatic deploy.

### Verify the difference from prior work

[CodeAgent](https://arxiv.org/abs/2402.02172v5) covers multi-agent review, [c-CRAB](https://arxiv.org/abs/2603.23448v3) covers review evaluation based on human review, and [Adversarial Review](https://arxiv.org/abs/2608.18167v1) covers structured disagreement between reviewer and critic. Proximity was checked only at the abstract level; comparing methods, data, and grading in the full texts is the next step.

So novelty cannot be claimed for "having several AIs review" alone. A candidate difference is **separating independence from model diversity at the same budget, and measuring reproducibility of serious findings and the cost of additional detection**. If existing work already applies the same controls, the question must narrow to a more specific class of defects, such as cloud/IaC.

### Required data and minimal experiment

- From the author's public projects and public benchmarks whose terms allow it, fix about 20 diffs with defects and 10 without. Remove public write-ups and fix answers from the input.
- Condition A is one review, B is two independent reviews by the same model, C is two independent reviews by different models, D uses the same two models but the second reads the first's findings (sequential).
- For the main comparison B–D, match total tokens, maximum time, diff, and tool permissions. Report A alongside as a low-cost baseline, without mixing it into the budget-matched comparison.
- Run each condition several times and record model/API ID, settings, run date, actual usage, and elapsed time. Separate threads do not guarantee statistical independence.
- Deduplicate findings and confirm them by reproduction tests or blinded human judgment. Measure additional true positives, false positives, recall of serious defects, actual cost per additional finding, and human verification time.

If using existing contract run quotas or local models, do not assert they are free; account for time, power, and usage separately. Comparisons using paid APIs or GPUs should happen after a budget is decided. This plan does not start anything or incur charges.

### Limitations and venue

Constraints are a small number of self-made repos, model updates, public-data contamination of training, and subjectivity of severity judgment. Early results are candidates for software-engineering study groups or workshops; the specific next call must be checked separately. Do not use a majority vote of reviews as the ground-truth label, which would be circular.

## Idea 3: Judging cloud cleanup completion without misreading it

### Research question

In AI-assisted cloud operations, if we verify command exit, Terraform state, and a provider query of the target resources separately, can we reduce how often cleanup completion is falsely reported under partial failure, delay, or missing evidence? How does this relate to the time to confirm correct completion and to API load?

### Public work that can be used

The [final report of cloud-validation-level2-multicloud](https://github.com/moruku36/cloud-validation-level2-multicloud/blob/c5d25b637c2a71ffb84b6a7dab6c5f0f994062a0/docs/final-report.md) is a post-hoc analysis from build to cleanup on AWS/Azure/GCP, distinguishing execution records, static review, and discussion. It also notes that the three clouds were tried in sequence with earlier knowledge carried into the next, and code-level issues on reproduction. It is not to be treated as a performance comparison from a controlled experiment.

The [JUnit check in ai-engineering-factory](https://github.com/moruku36/ai-governance-control/blob/2525cbbdaf17947dcdd20943afb9098b8cb30c5e/orchestrator/core/junit.py) is an example that rejects zero tests, all skipped, and malformed totals. However, a report that parses is not necessarily evidence that tests truly ran; trust in the producer and confirmation of external state are needed separately.

### Verify the difference from prior work

[IaC-Eval](https://papers.nips.cc/paper_files/paper/2024/hash/f26b29298ae8acd94bd7e839688e329b-Abstract-Datasets_and_Benchmarks_Track.html) evaluates AWS IaC generation and [SWE-InfraBench](https://arxiv.org/abs/2606.05249) evaluates modifying existing AWS CDK code. This idea narrows the target from generation accuracy and deals with **the operational claims of termination, deletion, and nothing remaining, and the observation evidence for them**.

We still need to investigate whether comparable methods already exist in failure detection for distributed systems, state consistency, and IaC drift/teardown verification. Adding "AI" to the name does not make it new research. If claiming improvement in model behavior, measure separately with and without AI execution under the same controller and tasks.

### Required data and minimal experiment

- Build about 30 scenarios with a local state machine. Include normal deletion, partial deletion, delayed reflection in listings, expired credentials, rate limits, mid-run interruption, targets that vanish from state but remain externally, and missing evidence.
- Compare A "exit code only", B "exit code and state", and C "B plus scoped external-state confirmation and time-bounded re-query". Do not treat failure of an external query as zero results.
- Ground truth is held only by the grader inside the simulated provider. The controller sees only responses.
- Metrics are false-completion rate, detection rate of non-completion, false stops in normal cases, time to determination, and additional API calls. Cases not determined within the trial limit are tallied separately as "unknown".
- Record "process stopped," "resource deleted," "stored data deleted," and "billing stopped" as separate items in the report. Do not infer actual billing from a simulated API's deletion success.

The first round involves no real cloud, billing, or deletion. If moving to real environments, decide approvals for targets, cost, preservation, and deletion separately, and do not touch environments used for other work.

### Limitations and venue

It can only evaluate failures assumed by the simulated model. Provider-specific propagation delays and enumeration gaps need empirical demonstration. A good starting point is an IOTS non-reviewed poster to discuss the validity of the failure taxonomy and judgment metrics.

## Common checks before starting research

- Narrow to one research question and hypothesis; fix baselines, primary metrics, and exclusion criteria before experiments.
- Read prior work's full text and public artifacts, and tabulate which questions are the same and which differ. The above is not an exhaustive survey.
- Separate design data from evaluation data, and keep failures and negative results.
- Use public materials and synthetic data as the baseline; do not use internal company information, private correspondence, or real credentials.
- Save commits, dependency versions, model IDs, settings, seeds, counts, and failure denominators at run time. A guessed model name is not a substitute for a run ID.
- Separate procedures that allow independent reruns from parts that could not be rerun.
- For rights, affiliation, and publication pathways, see the [publication pathways report](publication-pathways-2026.md).

## Deferred candidates

The existing "secret handoff lifecycle" and "on-demand GPU cleanup" are not withdrawn. For the former, first design the threat model and evaluation data that contain no secrets; for the latter, first fix the evidence conditions of Idea 3 above and confirmation in a real environment. Neither is treated as demonstrated effective or safe by the current public notes.
