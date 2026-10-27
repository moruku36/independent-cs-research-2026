**English** | [日本語](README.ja.md)

# Survey notes

Reading records for computer science and AI-security papers and research articles. Each note follows the [survey record template](template.md) and keeps **primary source checked / text read closely / reproduced** apart. Pick a theme:

- [AI agent safety and out-of-scope behavior](agent-safety/README.md) (4 papers + 1 research article): Whether AI agents act outside their authorization, and how they can be attacked in real workflows. [Agentic Uncertainty Reveals Agentic Overconfidence](agent-safety/2026-agentic-overconfidence.md)。
- [Decoys, deception, and LLM system defense](deception-defense/README.md) (2): Using fake evidence and decoy models to steer or isolate malicious agents and requests.
- [Coding agents, code review, and software engineering](coding-agents/README.md) (7 papers + 1 research article + 4 technical articles): Benchmarks and industrial studies of AI coding assistants, automated repair, and automated review. [Redesigning source control at Anthropic](coding-agents/2026-anthropic-scion-source-control.md) (report/article).
- [Human-AI collaboration at work](human-ai-collaboration/README.md) (5): What people expect from AI co-workers, how tools treat waiting time and attention, and how AI use changes work activity and learning opportunities. [Goals as First-Class Abstractions in Human-AI Collaboration](human-ai-collaboration/2026-goals-first-class-abstractions.md)。
- [Security governance: privacy, policy, crypto-agility, and cloud controls](security-governance/README.md) (4 papers + 1 article review): Organizational security questions around GenAI, cryptographic migration, and multi-cloud control consistency. [Agentic Inequality](security-governance/2025-agentic-inequality.md)。 [Shadow AI and PII article review](security-governance/2026-shadow-ai-ban-pii-governance.md).
- [LLM serving infrastructure and cost-efficiency](llm-infrastructure/README.md) (3): Hardware choices, scheduling, KV cache control, and long-term memory retrieval.
- [Cloud resilience and SRE](cloud-resilience/README.md) (2): AWS cross-account fault experiments and recovery decisions; measured results and reproduction unverified. [SequenceFI: Non-intrusive Temporal Fault Injection for Microservice Systems](cloud-resilience/2026-sequencefi.md)。 [Cloud Computing & DevOps: Research Insights 2025–2026](cloud-resilience/2026-cloud-devops-research-insights.md) (report/article).
- [Events, technical articles, and work/labor research](articles/README.md) (5 articles/reports + 1 academic paper): A CHI paper is kept distinct from the articles. [Recursive self-improvement: evidence review](articles/2026-rsi-evidence-review.md)。


Research articles follow the same record fields but are counted separately from academic papers and preprints.

## Principles for research notes

- Do not write "reproduced" when no experiment was run.
- Do not confuse a paper's simulation results with attacks that succeed in real operation.
- Always keep the primary URL and verification status of cited works.
- Every note has a Japanese counterpart (`*.ja.md`).
- Every note opens with a three-line **Overview** (what it is / what it says / caveat), placed right after the title.

## Where files live

`surveys/<theme>/<year>-<slug>.md` for papers, plus `<slug>.ja.md` for the Japanese version. Each theme folder has its own README listing its notes. Plans, checklists, and the full reading list are in [docs/](../docs/reading-list.md).

[Repository README](../README.md) | [Reading list](../docs/reading-list.md)
