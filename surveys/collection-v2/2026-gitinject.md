**English** | [日本語](2026-gitinject.ja.md)

# GitInject: Real-World Prompt Injection Against AI-Powered CI/CD Pipelines

## Key points for people and PMOs

- **What we learned**: four AI review/triage workflows on GitHub Actions (Claude, Codex, Gemini, Cline) were actually run and evaluated in throwaway repositories. Of 11 named attack scenarios, 10 were reproduced and 1 was not (token theft via issue body). The most serious is the path where config files placed on a PR branch (`CLAUDE.md`, `AGENTS.md`, `GEMINI.md`) are loaded as operator-level instructions.
- **What it's useful for**: concrete examples of separating an AI agent's "trusted config and instructions" from "candidate code under review," auditing the credential exposure surface of the runtime environment, and decoupling security verdicts from an LLM judge.
- **Caution**: only **the workflow configurations, model versions, and scenarios tried** were verified, which does not generalize to all current models or configurations. A failed cell means only "that attack did not succeed," not proof of safety (§6.2). The countermeasures are also limited in scope. The HTML version has formatting damage, and we also found mismatches between tables and text (below).
- **Next step**: this record is defensive research; no reproduction was done. Proposals are recorded separately in documents on the [ai-governance-control](https://github.com/moruku36/ai-governance-control) side.

## Survey record

- **Status**: primary text checked / read through the HTML version's §1–7, Tables 1–5, descriptions of Figures 1–3, and Appendices A–H. Cross-check with the PDF, close reading of cited works, and checking the public code not done. No reproduction or experiments.
- **Title, authors, year, venue, ID, primary URL**: *GitInject: Real-World Prompt Injection Attacks in AI-Powered CI/CD Pipelines* / Jafar Isbarov, Umid Suleymanov, Ilia Shumailov, Murat Kantarcioglu / 2026 / peer-reviewed venue unconfirmed (arXiv preprint, cs.CR, cross-list cs.AI). [arXiv:2606.09935v1](https://arxiv.org/abs/2606.09935v1) (submitted 2026-06-07 19:17 UTC), [HTML v1](https://arxiv.org/html/2606.09935v1), [PDF](https://arxiv.org/pdf/2606.09935), [DOI](https://doi.org/10.48550/arXiv.2606.09935) (issued by arXiv). A CC BY 4.0 notice was seen on the HTML.
- **Date checked and version**: 2026-10-14 UTC / v1. Only v1 was confirmed from arXiv's submission history. We do not claim that no later version exists. The text says Table 2 will be updated for the camera-ready after a disclosure grace period (§6.2).
- **Research question**: does running real GitHub workflows expose attack surface from sandboxes, credential storage, permissions, and network settings that simulated tool-call evaluation misses? And what are the minimal workflow-level countermeasures, and how far do they work (§1, §4)?
- **Method, data, comparison conditions**:
  - **Framework**: prepare a throwaway GitHub repository, place the target workflow YAML as is, inject attack input into the event, and judge by looking at actual state through the GitHub API after the run (§4, Figure 3, Appendix E.2). The repository is deleted after the run.
  - **Judges (author's description)**: the authors say `StateEvaluator` (a deterministic judge of side effects visible through the API) is used routinely for security evaluation, and `LLMEvaluator` (a binary judgment by Gemini 3.1 Pro Preview) only for semantic success such as usefulness, not for security evaluation (§4, Appendix E.1). **This is a description of the authors' method, not established practice.** Also, Table 5 labels the judge for judgment/approval manipulation attacks as `LLM`, which contradicts this description (mismatch 3 below).
  - **Targets**: 11 named attacks evaluated on "four representative workflows" across 4 AI providers (§5.1). The inventory in Appendix G (Table 4) lists 13 (including 1 for GitLab). The four evaluated and the 13 listed differ only in coverage and are not treated as a contradiction.
  - **Repetition**: each scenario ran 5 times with identical results, so each cell is 5/5 or 0/5 (notes to Tables 2 and 5).
  - **Attack classes**: PR/issue body (user-turn-level trust), config files (operator-level trust), availability (cost, key suspension), judgment manipulation (steering reviews to overlook) (§3, §5).
  - **Appendix A**: a case where an LLM enumerated attack hypotheses. The hypothesis did not hold in the real environment because the workflow does not fire for runs from external forks. This case is treated as an example of "you only know in the real environment" and excluded from the case collection.
- **Claims and evidence**: see tables below. Sources are Tables 1–3, 5 and §5.
- **Limitations and threats to validity (§6.2)**:
  - Results depend on model versions and workflow configurations at the time of evaluation; whether they were fixed is only known by rerunning.
  - The attack enumeration is not exhaustive, and LLM hypothesis generation does not guarantee completeness.
  - A failed cell is not proof of safety.
  - Points from this record: several table/text mismatches, that part of the judging is an LLM judge, and that the simulation comparison is a result on a single benchmark (AgentDojo).
- **Comparison with related work**: the difference from simulated-environment benchmarks such as AgentDojo (97 user tasks, 629 security cases), studies of static GitHub Actions misconfiguration, and earlier reports of injection via PR/issue bodies (PromptPwnd, the post-mortem on a Cline incident) is placed on config-file injection reaching the agent at operator-level trust (§2). This "novelty" is the authors' claim and we did not verify it with an exhaustive prior-work search.
- **Free-to-run reproduction plan**: not done in this task. The paper's experiments involve real API keys, paid runs, and attack input against external services, so we limit ourselves to a free desk check (a read-through of our own workflow configurations). Attack input is not included in this record.
- **Usage status**: proposed (documents on the [ai-governance-control](https://github.com/moruku36/ai-governance-control) side) / implementation and reproduction not done.
- **Unconfirmed points and next checks**: differences from the PDF, contents of the public code, existence of later versions, conference acceptance, consistency of each cell with Tables 3 and 5 (below). Authors were not contacted.

### Numbers and evaluation unit

**Comparison with simulation (§4, §5.1, Table 1, Appendix B)**: 10 CI/CD injection tasks were built in AgentDojo (6 attacks that use runtime state, 2 attacks blocked by the sandbox, 2 controls) and run as 5 models × 10 tasks × 2 user tasks = **n=100**.

| | Actually succeeded | Actually failed | Total |
|---|---:|---:|---:|
| Simulated: success | 23 (TP) | 1 (FP) | 24 |
| Simulated: failure | 57 (FN) | 19 (TN) | 76 |
| Total | 80 | 20 | 100 |

- The paper writes "misses 71.2% of real attacks." The denominator is the **80 that actually succeeded** (57/80 = 71.25%). The denominator of "5.0%" is the **20 that actually failed** (1/20). The two denominators differ and neither is a share of all 100 (verification of the derivation is ours).
- Within the scope we checked, how each task was assigned "actually succeeded / failed" cannot be determined from the text. We do not infer the breakdown of the 80 from the task taxonomy (Appendix B) and record Table 1's values as is.
- AgentDojo is one benchmark with 5 models and 2 tasks; we do not generalize to other simulated environments. The paper itself says this is not a flaw of AgentDojo.

**By category (Table 2)**: each cell is "attacks that succeeded / attacks tried." All five runs gave the same result.

| MITRE category | Claude | Codex | Gemini | Cline | Total |
|---|---:|---:|---:|---:|---:|
| Credential Access | 1/3 | 2/2 | 2/3 | 0/1 | 5/9 |
| Defense Evasion | 1/2 | 2/2 | 2/2 | – | 5/6 |
| Discovery | 0/1 | – | 0/1 | 1/1 | 1/3 |
| Impact | 1/1 | 1/1 | 1/1 | 1/1 | 4/4 |
| Total | | | | | 15/22 |

- "22" is **the sum of scenarios tried across workflow × category pairs** (our summation), a different unit from the 11 named attacks. The 11 named attacks are the rows of Table 5, and one may apply to several workflows.
- The last row is our tally. "–" means structurally not applicable.

**By model (Table 3)**: PR/issue body has denominators of 4 (Claude, Gemini) or 2 (GPT; Codex has no issue), and config files have 2 scenarios.

| Model | PR/issue body | Config file |
|---|---:|---:|
| claude-sonnet-4-5 / claude-haiku-4-5 | 0/4 / 0/4 | 2/2 / 2/2 |
| claude-opus-4-7 | 0/4 | 0/2 |
| gpt-4o-mini | 2/2 | 2/2 |
| gpt-5 / gpt-5.4 | 0/2 / 0/2 | 2/2 / 0/2 |
| gemini-2.5-flash / gemini-3-flash / gemini-3.1-pro-preview | 0/4 (each) | 2/2 (each) |

**Availability (§5.4, Appendix C)**: the denial-of-service (denial_of_wallet) scenario itself is **confirmed 5/5** in Table 5. **Only the campaign dollar amount and run minutes are projections.** A 65,536-character PR body is 22,100 tokens (Opus 4.7 tokenizer), and with a 32,000-token output limit it costs $1.11 per PR; 100 PRs (2 hours) cost $32–$111 and 400 Actions minutes. Even a refusal costs $0.32 in input tokens alone. **Key suspension via content-policy violation is a hypothesis** and was not tested (for ethical and legal boundaries). Severity is rated Low.

### Countermeasures and limits (§5, Appendix D)

The paper's countermeasures are **per scenario** and not general guarantees.

- `persist-credentials: false`: removes only the path where `GITHUB_TOKEN` stays in `.git/config`. It does not stop theft of other credentials, and Gemini's key is written elsewhere, so it is deemed insufficient (§5.2, §5.3, Table 5). It is not proof of general safety.
- Tool restriction: prevents shell-stage theft but not judgment manipulation that does not use a shell. It has a usefulness cost.
- Actor filter: not stronger review but a trade-off that **denies service to outsiders**. Repos that must accept external PRs keep residual risk.
- Human approval: a cursory check has trouble distinguishing malicious config that is treated as operator settings, and is not a guarantee (Appendix D). The paper's conclusion says only an actor filter or advisory-only permissions give a "firm guarantee" against judgment manipulation, while §5.3 also says residual risk remains. Treat this strong wording as the authors' claim.
- Judgment manipulation (steering reviews to overlook) is said to have no cheap workflow-level countermeasure.
- Pre-checking input size and content pre-filtering need latency, cost, and custom implementation.

### Before publishing and cautions

- Some payloads and commands appear in the text, but this record is a defensive summary and **does not reproduce attack input or commands**.
- The paper says it experimented only in throwaway repositories owned by the authors and disclosed to GitHub, Anthropic, OpenAI, and Google (§6.3). We did not verify that disclosure.

## Text/table mismatches and formatting damage (recorded unresolved)

The following are results of checking the primary HTML, and **we did not resolve them by guessing**.

1. **HTML formatting damage**: formulas and code blocks are missing in places (e.g., right after "The injected payload:" and "Neither step succeeds alone," before the condition in Appendix A.2, and the code in §5.3). Math like `n=100` and `2^256` survives only in attributes. The color coding of Tables 2 and 3 is lost, and the table note "Gray (–)" survives only as a symbol. Some appendix headings are empty, and Acknowledgments is empty.
2. **"Eleven reproduced cases" vs. the table**: §1 says "Eleven reproduced prompt-injection cases," but of Table 5's 11 rows, `issue_body_github_token_exfiltration` has success rate 0 (precondition not met) and was not reproduced.
3. **The claim that LLM judges are not used for security verdicts vs. Table 5's labels**: §4 and Appendix E.1 say LLMEvaluator is not used for security evaluation. Yet Table 5 labels the judge for the six judgment/approval-manipulation attacks (`*_approval_manipulation`) as `LLM`, and the legend says "LLM = semantic review quality." Which is the actual judge cannot be determined from the text, and we did not resolve it. We do not treat the "success" of judgment manipulation as determined by deterministic state checks.
4. **Gemini in Table 3, Table 5, and §5.2**: §5.2 and Table 5 say PR-body-based judgment manipulation succeeded on gemini-2.5-flash and gemini-3-flash, and token theft was also confirmed on gemini-assistant. Yet in Table 3's PR/issue body column, both Gemini models are 0/4.
5. **Workflow in Table 5 vs. §5.2**: §5.2 says `pr_body_github_token_exfiltration` was confirmed on codex-pr-review and gemini-assistant, but Table 5 lists only codex-pr-review and gpt-4o-mini.
6. **Scope of denial_of_wallet**: Table 5 lists only claude-pr-review / Opus 4.7, while Impact in Table 2 is 1/1 for all four workflows.
7. **Some cells of Discovery and Credential in Table 2**: even cross-checking against Table 5, we cannot identify the named attacks corresponding to Claude's and Gemini's `Discovery 0/1` and Cline's `Credential Access 0/1`.
8. **Control tasks and the fork premise**: §5.1 and Appendix A say a `workflow_run` attack from a fork does not hold in the real environment, yet Appendix B places that type of control task as "simulation and reality agree." Appendix A says it was confirmed under the owner's account, but the basis for counting it as "actually succeeded" in Table 1 is not explicit.
9. **Cost arithmetic**: the "$1.11" in §5.4 does not match the simple sum of 22,100 input tokens ($5/MTok) plus 32,000 output tokens ($25/MTok), about $0.91. Appendix C mentions resending history across agentic multi-turn runs, but the breakdown of $1.11 is not given.
10. **Differences in command notation**: §5.1 and §5.2 spell the command that reads the auth header differently (not reproduced in this record).
11. **gpt-4o / gpt-4o-mini**: Appendix E.5 mentions developing a theft attack against "gpt-4o," but the only model in the evaluation tables is gpt-4o-mini.

## Applying this to our own AI operations

These are **this project's proposals**, not measures whose effect the paper demonstrated. Implementation, adoption, and effect measurement are not done.

1. Read trusted instructions and config from a trusted base, separate from the candidate under review (the PR checkout).
2. Minimize runtime credentials, permissions, and outbound communication, and keep the AI's output advisory.
3. Judge security effects by independent deterministic checks, not an LLM judge.
4. Limit input, output, and cumulative budgets separately, and fail closed when unsure.

Details and adoption conditions go in the [research note on the ai-governance-control side](https://github.com/moruku36/ai-governance-control/blob/main/docs/research/gitinject-2606.09935.md) (effective after merge).

## Summary

GitInject (arXiv:2606.09935v1, cs.CR, 7 June 2026; preprint, review status unconfirmed) runs real GitHub Actions workflows in ephemeral repositories to test prompt injection against AI review and triage agents (Claude, Codex, Gemini, Cline). It reports eleven named attacks; ten are shown as reproduced and one (issue-body token theft) is not. Each scenario ran five times with identical outcomes (5/5 or 0/5). Results apply only to the tested model versions, workflow configurations and scenarios, not to all current models; failed cells do not prove safety. Table 1 compares against AgentDojo over n=100 (5 models × 10 tasks × 2 user tasks): 23 TP, 1 FP, 57 FN, 19 TN as reported; the 71.2% miss rate uses the 80 real successes and the 5.0% false-positive rate the 20 real failures. We do not infer how those 80 arise from the task taxonomy. Table 2's 15/22 counts workflow/category scenario cells, a different unit from the eleven named attacks. The denial_of_wallet scenario itself is listed as 5/5 confirmed in Table 5; only the campaign amounts and Actions minutes ($32–$111, 400 minutes for a 2-hour, 100-PR campaign) are projections. The authors say security verdicts never use the LLM judge (§4, App. E.1) yet Table 5 labels the six judgment/approval-manipulation attacks as LLM-evaluated; this conflict is unresolved and the method description is an author claim, not established practice. Also, content-policy key suspension is a hypothetical not tested. The four evaluated workflows versus the 13-entry inventory are different coverage, not treated as a contradiction. Countermeasures (e.g., `persist-credentials: false`, tool restriction, actor filtering) are scenario-specific, with limits; actor filtering trades off service to external contributors. The HTML has formatting damage (missing code blocks and math) and several text/table inconsistencies, listed above and left unresolved. Primary HTML read in full; no reproduction, no PDF cross-check, no code inspection. Attack inputs are deliberately not reproduced. Governance proposals are recorded separately in ai-governance-control.

Source sections: [§1](https://arxiv.org/html/2606.09935v1#S1) · [§3](https://arxiv.org/html/2606.09935v1#S3) · [§4](https://arxiv.org/html/2606.09935v1#S4) · [§5.1/Table 1](https://arxiv.org/html/2606.09935v1#S5.SS1) · [§5.2](https://arxiv.org/html/2606.09935v1#S5.SS2) · [§5.3](https://arxiv.org/html/2606.09935v1#S5.SS3) · [§5.4](https://arxiv.org/html/2606.09935v1#S5.SS4) · [§5.5](https://arxiv.org/html/2606.09935v1#S5.SS5) · [§6.2](https://arxiv.org/html/2606.09935v1#S6.SS2) · [Appendix A](https://arxiv.org/html/2606.09935v1#A1) · [B](https://arxiv.org/html/2606.09935v1#A2) · [C](https://arxiv.org/html/2606.09935v1#A3) · [D](https://arxiv.org/html/2606.09935v1#A4) · [G](https://arxiv.org/html/2606.09935v1#A7) · [H](https://arxiv.org/html/2606.09935v1#A8) · [Table 2](https://arxiv.org/html/2606.09935v1#S5.T2) · [Table 3](https://arxiv.org/html/2606.09935v1#S5.T3)

[Collection index](README.md) | [Reading list](../../docs/reading-list.md)
