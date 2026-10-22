**English** | [日本語](README.ja.md)

# Independent CS Research 2026

Public notes for independent researchers and industry practitioners who do computer science research and want to turn it into papers and conference talks. This repository accumulates publication pathways, candidate research topics, AI paper reading logs, and practical application ideas, all based on publicly available information.

**2026-10-18 UTC update:** Research plans are in the initial phase. The survey collection holds 12 papers. Primary texts have been checked for Astra, SWE-Journey, FlowAgent, GitInject, the CAMM evaluation, Agentic Code Review Eras, Chat First Worry Later, CLI Coding Agents, AI-Native Co-Worker Qualities (BACI), and Meta RADAR; SWE-Journey is only partially read. Replication experiments and original-research validation have not been done. Eligibility for presentation, acceptance precedents, biographical details, and affiliation wording are still undecided.

## Repository architecture

![Repository architecture: root README leads to docs/ (pathways, plans, checklists) and surveys/ (paper reading records), where collection-v2 is the canonical thematic index](docs/diagrams/architecture.en.svg)

<sub>Rendered with [Pele](https://pele.run/) from the [Mermaid source](docs/diagrams/architecture.en.mmd). Japanese version: [README.ja.md](README.ja.md).</sub>

**2026-10-20 JST addition:** Added the [SlopCodeBench survey](surveys/collection-v2/2026-slopcodebench.md), covering primary PDF findings, execution conditions, related-work comparison, limitations, and an unexecuted pilot plan.

## Survey Collection v2

- **[Survey Collection v2: per-paper records and thematic index](surveys/collection-v2/README.md)**
  - [Unsanctioned supply-chain attacks by AI agents (UK AISI)](surveys/collection-v2/2026-unsanctioned-supply-chain-attacks.md)
  - [AgentLSD: guiding agent exploration with deceptive evidence](surveys/collection-v2/2026-agentlsd.md)
  - [HoneyRoute: routing malicious requests to honeypot models](surveys/collection-v2/2026-honeyroute.md)
  - [SWE-Journey: long-horizon interactive coding evaluation](surveys/collection-v2/2026-swe-journey.md)
  - [FlowAgent: low-latency pre-submit test repair at Google](surveys/collection-v2/2026-flowagent.md)
  - [GitInject: real-world prompt injection in AI-powered CI/CD](surveys/collection-v2/2026-gitinject.md)
  - [CAMM: practical evaluation of the crypto-agility maturity model](surveys/collection-v2/2026-camm-practical-evaluation.md)
  - [From Human-Centric to Agentic Code Review](surveys/collection-v2/2026-agentic-code-review-eras.md)
  - [Chat First, Worry Later: workplace ChatGPT privacy study](surveys/collection-v2/2026-chat-first-worry-later.md)
  - [Adoption and impact of command-line AI coding agents at Microsoft](surveys/collection-v2/2026-cli-coding-agents-adoption-impact.md)
  - [What Makes a Great Co-Worker in an AI-Native Workplace? (Microsoft BACI study)](surveys/collection-v2/2026-ai-native-coworker-qualities.md) ([arXiv:2609.13786](https://arxiv.org/abs/2609.13786))
  - [Automating Low-Risk Code Review at Meta: RADAR](surveys/collection-v2/2026-radar-low-risk-code-review.md)
  - [How employment is changing at Anthropic](surveys/collection-v2/d2026-anthropic-employment-changes.md) ([Source](https://www.anthropic.com/research/employment-at-anthropic))
   - [Anthropic Economic Index report: Cadences](surveys/collection-v2/d2026-anthropic-economic-index-cadences.md) ([Source](https://www.anthropic.com/research/economic-index-june-2026-report))
  - [SlopCodeBench: code degradation under iterative agent development](surveys/collection-v2/2026-slopcodebench.md)
  - [Too Long to Watch, Too Short to Leave: designing for agent micro-waits (Sidecar)](surveys/collection-v2/2026-agent-micro-waits-sidecar.md) ([arXiv:2610.27170](https://arxiv.org/abs/2610.27170)): primary HTML checked via extraction; no reproduction.
  - [Demystifying Cost-Efficiency in LLM Serving over Heterogeneous GPUs](surveys/collection-v2/2025-heterogeneous-gpu-llm-serving.md) ([arXiv:2502.00722](https://arxiv.org/abs/2502.00722)): partially read; no reproduction.

## Reference candidates (primary text not yet checked)

- [Quantum annealing and RSA integer factorization on D-Wave Advantage](docs/reference-candidates/2024-dwave-annealing-rsa.md): a 2024 news article, recorded as a lead toward the primary PDF. Full text unread, bibliography unconfirmed, no replication. Not counted among the surveys above.

## Contents

- [Publishing and presenting CS research as an individual (first survey done)](docs/publication-pathways-2026.md)
  - Updated 2026-10-11 JST: domestic Japanese venues, acceptance examples, and public research history checked against primary sources. Target venue, affiliation wording, and travel budget are still undecided.
- [Research candidates (unverified)](docs/research-agenda.md)
- [AI paper reading and application list (includes five papers checked against primary text)](docs/reading-list.md)
- [AgentLSD: guiding AI agent exploration with fake evidence](surveys/2026-agentlsd.md)
- [HoneyRoute: routing LLM requests to decoy models](surveys/2026-honeyroute.md)
- [AI decoy defenses: comparing two papers and sorting research themes](surveys/2026-ai-agent-honeypot-deception.md)
- [Survey record template](surveys/template.md)
- [Reproducibility, ethics, and pre-publication checklist](docs/reproducibility-ethics-checklist.md)

Published content is limited to publicly verifiable CS background, OSS contributions, research plans, and public paper information. Internal company information, private correspondence, confidential data, and non-public personal details are excluded. No biographical or degree claims are made until a public source is checked, and neither an employer nor a past university is treated as a current research affiliation.

## Languages

English is the primary language. Every page has a Japanese counterpart (`*.ja.md`), linked from the switcher at the top of each page. Where the two differ, the Japanese originals are authoritative for Japan-specific details (venues, deadlines, fees).

## Conference and technical article reviews

- [Black Hat USA 2026: NRI Secure article review](surveys/collection-v2/2026-black-hat-usa-nri-secure.md) (2026-10-20): Five-session synthesis, primary-source verification scope, and enterprise review proposals. Article checked; no reproduction or implementation. Excluded from academic paper counts.

- [Research acceleration: The view inside OpenAI](surveys/collection-v2/2026-10-21-openai-research-acceleration.md) (recorded 2026-10-21 JST): company research article; author reflection kept separate. Excluded from academic paper counts.
