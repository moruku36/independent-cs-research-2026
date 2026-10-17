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

- [SWE-Journey](2026-swe-journey.md) (2026-10-08): long-horizon development with simulated user dialogue. Primary text checked; partially read; no experiments.
- [FlowAgent](2026-flowagent.md) (2026-10-05): low-latency automatic repair of pre-submit test failures at Google. Primary PDF checked; no reproduction (proprietary data); team practices adopted, effect unverified.

- [From Human-Centric to Agentic Code Review](2026-agentic-code-review-eras.md) (v1, 2026-07-14): 1.02M reviewed PRs from 207 GitHub projects across pre-LLM, LLM, and agent eras. Primary HTML read in full; no PDF cross-check, replication-package check, or reproduction; regression results are explanatory, not causal.
- [Adoption and Impact of Command-Line AI Coding Agents](2026-cli-coding-agents-adoption-impact.md) (v1, 2026-07-01): tens of thousands of Microsoft engineers over an early-2026 rollout of Copilot CLI and Claude Code. Primary HTML read in full; no reproduction (proprietary telemetry); PR throughput increased +24% and persisted over 4 months; adoption driven by social exposure while prior IDE use reduced retention.

## Privacy and organizational policy in GenAI use

- [Chat First, Worry Later](2026-chat-first-worry-later.md) (v1, 2026-08-21): questionnaire study of 224 European ChatGPT users at work on policies, privacy concerns, and knowledge. Primary HTML read in full and PDF figures checked; no reproduction; text/table mismatches recorded as unresolved.

## Crypto-agility and PQC migration assessment

- [Practical evaluation of CAMM](2026-camm-practical-evaluation.md) (v1, 2026-04-14): primary PDF text checked; no reproduction. Records evaluation conditions, limitations, and an unperformed exercise for a PQC lab.

## Related reference candidates (outside the survey count)

- [2024 reports on D-Wave quantum annealing and RSA integer factorization](../../docs/reference-candidates/2024-dwave-annealing-rsa.md): records the path from the article to the official PDF. Primary text unread, bibliography unconfirmed, no replication.

## Principles for research notes

- Do not write "reproduced" when no experiment was run.
- Do not confuse a paper's simulation results with attacks that succeed in real operation.
- Always keep the primary URL and verification status of cited works.
- Existing per-paper notes are kept so external links keep working; this directory is the **canonical index from now on**.

[Repository README](../../README.md) | [Full reading list](../../docs/reading-list.md)
