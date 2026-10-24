**English** | [日本語](reading-list.ja.md)

# AI Paper Reading and Application List

## October 2026: Anthropic formal verification and self-replicating AI (research articles)

- [LLM-assisted formal software verification](../surveys/coding-agents/2026-anthropic-formal-verification.md)
- [Self-replicating AI outside datacenters](../surveys/agent-safety/2026-anthropic-self-replicating-ai.md)

Added 2026-10-24 JST. Research articles are distinct from academic papers. Each note records verification scope, limitations, related work, and unexecuted check plans.

## Added paper surveys, 2025–2026

- [Raw-RAG versus agentic memory](../surveys/llm-infrastructure/2026-raw-rag-agentic-memory.md) — [arXiv:2610.30755v1](https://arxiv.org/html/2610.30755v1); primary body and selected appendix material checked; partially read; code and reproduction unverified.
- [Cache Engineering for Agents](../surveys/llm-infrastructure/2026-cache-engineering-for-agents.md) — [arXiv:2610.28577v1](https://arxiv.org/html/2610.28577v1); partially read; not reproduced.
- [Generative AI and critical thinking in knowledge work](../surveys/articles/2025-ai-critical-thinking-knowledge-workers.md) — [CHI 2025](https://doi.org/10.1145/3706598.3713778); work/labor academic paper, partially read; not reproduced.
- [Adaptive Ephemeral Chaos Infrastructure](../surveys/cloud-resilience/2026-adaptive-ephemeral-chaos-infrastructure.md) — [publisher PDF](https://ijetcsit.org/index.php/ijetcsit/article/view/654/593); full text checked, Section 8 only future evaluation, no measured result; code and reproduction unverified.

Status: the existing secondary-article seeds are awaiting identification of primary papers. Reading status is recorded per paper. Astra, SWE-Journey, FlowAgent, and GitInject have primary text checked (FlowAgent via the primary PDF); SWE-Journey is partially read (no reproduction or implementation). Application ideas are not treated as completed results.

| Secondary-article seed | Interest / application idea | Primary paper / read / implemented |
|---|---|---|
| https://ai-data-base.com/timeline/read/125022 | Applying to effort-estimation simulation | Awaiting identification / unconfirmed / unconfirmed |
| https://ai-data-base.com/timeline/read/127145 | Independent review with Qwen; applying to A100 | Awaiting identification / unconfirmed / unconfirmed |
| https://ai-data-base.com/timeline/read/122219 | Subject for understanding and explanation | Awaiting identification / unconfirmed / unconfirmed |

## Survey Collection v2

- **[Survey collection (theme index)](../surveys/README.md)**
- [Evaluation of unsanctioned OSS supply-chain attacks (GPT-6 Astra)](../surveys/agent-safety/2026-unsanctioned-supply-chain-attacks.md): arXiv:2609.38415. Primary text checked; no replication.

## Sept–Oct 2026: AI agent attacks and decoys

- [Exploration steering with decoys and false evidence, and protecting production LLMs (detailed note)](../surveys/deception-defense/legacy/2026-ai-agent-honeypot-deception.md)
- **[AgentLSD: template-conformant individual note](../surveys/deception-defense/2026-agentlsd.md)** (2026-09-16): evaluates whether false leads increase an AI's exploration turns and reasoning tokens. Primary abstract checked; not reproduced. [Primary paper](https://arxiv.org/abs/2609.19140).
- **[HoneyRoute: template-conformant individual note](../surveys/deception-defense/2026-honeyroute.md)** (2026-09-08): routes malicious LLM requests to a decoy model to protect production. Primary abstract checked; not reproduced. [Primary paper](https://arxiv.org/abs/2609.08306).
- **Source article**: [AIDB 134139](https://ai-data-base.com/timeline/read/134139)

When adding an entry, record the primary URL, bibliographic information, reading status, question, method, limitations, comparison, reproduction plan, usage status, and public evidence separately.

## October 2026: Coding assistance and collaboration

- [SWE-Journey: evaluating long-horizon, interactive coding assistance](../surveys/coding-agents/2026-swe-journey.md): [arXiv:2610.11559v1](https://arxiv.org/abs/2610.11559v1). Primary text checked / partially read / no reproduction or implementation. Use for acceptance conditions and verification records is a proposal. The introducing article [AIDB 134413](https://ai-data-base.com/timeline/read/134413) could not be retrieved; the record rests on the paper's text.
- [FlowAgent: low-latency agentic repair of pre-submit test failures](../surveys/coding-agents/2026-flowagent.md): [arXiv:2610.07289v1](https://arxiv.org/abs/2610.07289v1). Primary PDF checked / not reproduced (data non-public). Four operating practices for delegating work are adopted but their effect is unverified. The introducing article [AIDB 133569](https://ai-data-base.com/timeline/read/133569) was not read in full; the paper alone is the basis.

## June 2026: Defending AI agents in CI/CD

- [GitInject: real-world prompt injection against AI-powered CI/CD](../surveys/agent-safety/2026-gitinject.md): [arXiv:2606.09935v1](https://arxiv.org/abs/2606.09935v1). Primary HTML read in full; no reproduction, PDF cross-check, or code check. Results are for the configurations tried and do not generalize to all models. Table/text mismatches are recorded unresolved. Application ideas are proposals only.

## April 2026: Evaluating crypto-agility and PQC migration

- [Practical evaluation of CAMM](../surveys/security-governance/2026-camm-practical-evaluation.md): [arXiv:2604.12428v1](https://arxiv.org/abs/2604.12428v1), 2026-04-14. Primary PDF text checked / not reproduced. Application to a PQC lab is an improvement proposal only.

## Reference candidate: quantum annealing cryptanalysis

- [D-Wave Advantage and RSA integer factorization](reference-candidates/2024-dwave-annealing-rsa.md): the [introducing article](https://gigazine.net/news/20241015-rsa-encryption-quantum-computer/) points to a [primary PDF](http://cjc.ict.ac.cn/online/onlinepaper/wc-202458160402.pdf) that could not be retrieved. Text unread, bibliography unconfirmed, no replication. Not treated as a practical RSA break or as proof of quantum advantage, and managed separately from the seven existing surveys.

## March–May 2026: iterative development and code quality

- [SlopCodeBench: code degradation under iterative agent development](../surveys/coding-agents/2026-slopcodebench.md): [arXiv:2603.24755v2](https://arxiv.org/abs/2603.24755v2). Primary PDF body, main tables, and execution conditions checked. Includes unresolved reporting inconsistencies, comparison with SWE-Journey, and an unexecuted pilot plan. No reproduction or implementation.

## October 2026: Black Hat conference article

- [Black Hat USA 2026: NRI Secure article review](../surveys/articles/2026-black-hat-usa-nri-secure.md): Five-session synthesis, primary-source verification scope, and enterprise review proposals. Article checked; no reproduction or implementation. Excluded from academic paper counts. [Source article](https://www.nri-secure.co.jp/blog/black-hat-usa-2026)

## October 2026: OpenAI company research article

- [Research acceleration: The view inside OpenAI](../surveys/articles/2026-10-21-openai-research-acceleration.md) (recorded 2026-10-21 JST): article reading record with a separate author reflection; outside academic paper counts.
