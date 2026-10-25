**English** | [日本語](README.ja.md)

# Independent CS Research 2026

Public notes for independent researchers and industry practitioners who do computer science research and want to turn it into papers and conference talks. This repository accumulates publication pathways, candidate research topics, AI paper reading logs, and practical application ideas, all based on publicly available information.

**Status (2026-10-25 JST):** Research plans are in the initial phase. Each paper note states what was actually checked (primary text, partial read, or abstract only). Replication experiments and original-research validation have not been done. Eligibility for presentation, acceptance precedents, biographical details, and affiliation wording are still undecided.

## Paper notes by theme

Start from a theme; each folder README lists its papers with their verification status. [All themes and conventions](surveys/README.md).

- [AI agent safety and out-of-scope behavior](surveys/agent-safety/README.md) (3 papers + 1 research article): Whether AI agents act outside their authorization, and how they can be attacked in real workflows. Includes [self-replicating AI](surveys/agent-safety/2026-anthropic-self-replicating-ai.md) and [reward hacking](surveys/agent-safety/2025-reward-hacking-emergent-misalignment.md).
- [Decoys, deception, and LLM system defense](surveys/deception-defense/README.md) (2): Using fake evidence and decoy models to steer or isolate malicious agents and requests.
- [Coding agents, code review, and software engineering](surveys/coding-agents/README.md) (7 papers + 1 research article + 1 technical article): Benchmarks and industrial studies of AI coding assistants, automated repair, and automated review. Includes [formal verification](surveys/coding-agents/2026-anthropic-formal-verification.md), [NFV](surveys/coding-agents/2026-neuro-formal-verification.md), and [subagent consolidation](surveys/coding-agents/2026-fold-subagents-main-loop.md).
- [Human-AI collaboration at work](surveys/human-ai-collaboration/README.md) (4): What people expect from AI co-workers, how tools treat waiting time and attention, and how AI use changes work activity and learning opportunities. Includes [workplace adoption](surveys/human-ai-collaboration/2026-genai-workplace-productivity-communication.md) and [informal learning](surveys/human-ai-collaboration/2026-informal-learning-human-llm.md).
- [Security governance: privacy, policy, crypto-agility, and cloud controls](surveys/security-governance/README.md) (3): Organizational security questions around GenAI, cryptographic migration, and multi-cloud control consistency. Includes the [multi-cloud security architecture survey](surveys/security-governance/2026-multi-cloud-security-architecture.md).
- [LLM serving infrastructure and cost-efficiency](surveys/llm-infrastructure/README.md) (3): Hardware choices, scheduling, KV cache control, and long-term memory retrieval. Includes the [Raw-RAG survey](surveys/llm-infrastructure/2026-raw-rag-agentic-memory.md).
- [Cloud resilience and SRE](surveys/cloud-resilience/README.md) (1): AWS cross-account fault experiments and recovery decisions; measured results and reproduction unverified.
- [Events, technical articles, and work/labor research](surveys/articles/README.md) (4 articles + 1 academic paper): A CHI paper is kept distinct from the articles.

## Plans and guides

- [Publishing and presenting CS research as an individual](docs/publication-pathways-2026.md): updated 2026-10-11 JST; domestic Japanese venues, acceptance examples, and public research history checked against primary sources. Target venue, affiliation wording, and travel budget are still undecided.
- [Research candidates (unverified)](docs/research-agenda.md)
- [AI paper reading and application list](docs/reading-list.md)
- [Reproducibility, ethics, and pre-publication checklist](docs/reproducibility-ethics-checklist.md)
- [Survey record template](surveys/template.md)
- [Reference candidates (primary text not yet checked)](docs/reference-candidates/2024-dwave-annealing-rsa.md): a 2024 news article on quantum annealing and RSA factorization, recorded as a lead toward the primary PDF. Not counted among the paper notes.

## About this repository

Published content is limited to publicly verifiable CS background, OSS contributions, research plans, and public paper information. Internal company information, private correspondence, confidential data, and non-public personal details are excluded. No biographical or degree claims are made until a public source is checked, and neither an employer nor a past university is treated as a current research affiliation.

English is the primary language. Every page has a Japanese counterpart (`*.ja.md`), linked from the switcher at the top of each page. Where the two differ, the Japanese originals are authoritative for Japan-specific details (venues, deadlines, fees).
