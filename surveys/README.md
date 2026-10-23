**English** | [日本語](README.ja.md)

# Survey notes

Reading records for computer science and AI-security papers. Each note follows the [survey record template](template.md) and keeps **primary source checked / text read closely / reproduced** apart. Pick a theme:

- [AI agent safety and out-of-scope behavior](agent-safety/README.md) (2): Whether AI agents act outside their authorization, and how they can be attacked in real workflows.
- [Decoys, deception, and LLM system defense](deception-defense/README.md) (2): Using fake evidence and decoy models to steer or isolate malicious agents and requests.
- [Coding agents, code review, and software engineering](coding-agents/README.md) (6): Benchmarks and industrial studies of AI coding assistants, automated repair, and automated review.
- [Human-AI collaboration at work](human-ai-collaboration/README.md) (2): What people expect from AI co-workers, and how agent tools should treat the user's waiting time and attention.
- [Security governance: privacy, policy, and crypto-agility](security-governance/README.md) (2): Organizational and policy-level security questions around GenAI use and cryptographic migration.
- [LLM serving infrastructure and cost-efficiency](llm-infrastructure/README.md) (2): Hardware choices, scheduling, and agent KV cache control.
- [Cloud resilience and SRE](cloud-resilience/README.md) (1): AWS cross-account fault experiments and recovery decisions; measured results and reproduction unverified.
- [Events, technical articles, and work/labor research](articles/README.md) (4 articles + 1 academic paper): A CHI paper is kept distinct from the articles.

## Principles for research notes

- Do not write "reproduced" when no experiment was run.
- Do not confuse a paper's simulation results with attacks that succeed in real operation.
- Always keep the primary URL and verification status of cited works.
- Every note has a Japanese counterpart (`*.ja.md`).

## Where files live

`surveys/<theme>/<year>-<slug>.md` for papers, plus `<slug>.ja.md` for the Japanese version. Each theme folder has its own README listing its notes. Plans, checklists, and the full reading list are in [docs/](../docs/reading-list.md).

[Repository README](../README.md) | [Reading list](../docs/reading-list.md)
