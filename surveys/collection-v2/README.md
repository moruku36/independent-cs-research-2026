**English** | [日本語](README.ja.md)

# Survey Collection v2

Reading records for 2026 computer science and AI-security papers. Each file follows the items in the [survey record template](../template.md) and keeps **primary source checked / text read closely / reproduced** apart.

## AI agent safety and out-of-scope behavior

- [Evaluating Whether GPT-6 Astra Performs Unsanctioned Supply-Chain Attacks](2026-unsanctioned-supply-chain-attacks.md) (2026-09-29): does the AI attempt out-of-scope OSS supply-chain attacks? Primary text checked; no experiments.
- [GitInject](2026-gitinject.md) (2026-06-07): real-world prompt injection against AI-powered CI/CD workflows. Primary HTML read in full; no reproduction, PDF cross-check, or code check. Mismatches between tables and text recorded as unresolved.

## Decoys, deception, and LLM system defense

- [AgentLSD](2026-agentlsd.md) (2026-09): how fake evidence changes an agent's exploration and reasoning budget. Abstract checked; no replication.
- [HoneyRoute](2026-honeyroute.md) (2026-09): routes malicious requests to a decoy LLM and isolates production load. Abstract checked; no replication.
- [Cross-paper comparison of the two (older thematic note)](../2026-ai-agent-honeypot-deception.md)

## Coding assistants and human-AI collaboration

- [SlopCodeBench: code degradation under iterative agent development](2026-slopcodebench.md) (v2, 2026-05-07): 36 problems and 196 checkpoints measuring correctness, structural erosion, and verbosity. Primary PDF body, main tables, and execution conditions checked; no reproduction.

- [SWE-Journey](2026-swe-journey.md) (2026-10-08): long-horizon development with simulated user dialogue. Primary text checked; partially read.
- [FlowAgent](2026-flowagent.md) (2026-10-05): low-latency automatic repair of pre-submit test failures at Google. Primary HTML read in full; no reproduction.
- [From Human-Centric to Agentic Code Review](2026-agentic-code-review-eras.md) (v1, 2026-07-14): 1.02M reviewed PRs across human-centric, assistant-augmented, and agentic review eras. Primary PDF text checked.
- [Adoption and Impact of Command-Line AI Coding Agents](2026-cli-coding-agents-adoption-impact.md) (v1, 2026-07-01): telemetry and survey (n=3,812) on terminal coding agents at Microsoft. Primary PDF text checked.
- [What Makes a Great Co-Worker in an AI-Native Workplace?](2026-ai-native-coworker-qualities.md) (v1, 2026-09-12): 22 interviews and two-referent survey (N=1,534) at Microsoft producing the 75-quality BACI framework, 11 co-worker archetypes, and AI work etiquette taxonomy. Primary PDF text checked.
- [Automating Low-Risk Code Review at Meta: RADAR](2026-radar-low-risk-code-review.md) (v2, 2026-06-12): risk-stratified automated review and landing across 535K+ diffs at Meta (DRS + LLM ACR). Primary PDF text checked.

- [Too Long to Watch, Too Short to Leave: Designing for Agent Micro-Waits](2026-agent-micro-waits-sidecar.md) ([arXiv:2610.27170](https://arxiv.org/abs/2610.27170), v1, 2026-10-19): Sidecar, a same-tab side assistant for the 1-2 minute waits while an agent works; formative interviews (n=12) and a within-subjects study (N=16). Primary HTML checked through an extraction tool (last ~4,000 characters unread); venue unconfirmed; no reproduction.

## LLM serving infrastructure and cost-efficiency

- [Demystifying Cost-Efficiency in LLM Serving over Heterogeneous GPUs](2025-heterogeneous-gpu-llm-serving.md) ([arXiv:2502.00722](https://arxiv.org/abs/2502.00722), v2, 2025): benchmark of six GPU types and a MILP scheduler for GPU composition, deployment, and workload assignment under a price budget. Partially read (stops mid-§4.2); venue unconfirmed; no reproduction.

## Privacy and organizational policy in GenAI use

- [Chat First, Worry Later](2026-chat-first-worry-later.md) (v1, 2026-08-21): questionnaire study of 224 European enterprise employees on ChatGPT privacy habits and shadow GenAI. Primary PDF text checked.

## Crypto-agility and PQC migration assessment

- [Practical evaluation of CAMM](2026-camm-practical-evaluation.md) (v1, 2026-04-14): primary PDF text checked; no experimental verification.

## Related reference candidates (outside the survey count)

- [2024 reports on D-Wave quantum annealing and RSA integer factorization](../../docs/reference-candidates/2024-dwave-annealing-rsa.md)

## Principles for research notes

- Do not write "reproduced" when no experiment was run.
- Do not confuse a paper's simulation results with attacks that succeed in real operation.
- Always keep the primary URL and verification status of cited works.
- Existing per-paper notes are kept so external links keep working; this directory is the **canonical index from now on**.

[Repository README](../../README.md) | [Full reading list](../../docs/reading-list.md)

## Conference and technical articles (outside academic paper counts)

- [Black Hat USA 2026: NRI Secure article review](2026-black-hat-usa-nri-secure.md) (2026-10-20): Five-session synthesis, primary-source verification scope, and enterprise review proposals. Article checked; no reproduction or implementation. Excluded from academic paper counts.

- [Research acceleration: The view inside OpenAI](2026-10-21-openai-research-acceleration.md) (recorded 2026-10-21 JST): company research article; author reflection kept separate. Excluded from academic paper counts.
