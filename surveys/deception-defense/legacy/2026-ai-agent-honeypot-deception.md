**English** | [日本語](2026-ai-agent-honeypot-deception.ja.md)

# AI Agent Attacks, Decoys, and Resource Consumption (Sept–Oct 2026)

- Recorded: 2026-10-10
- Status: **abstracts of the primary sources checked / no close reading of full text, no experiment replication**
- Related secondary article: [AIDB 134139](https://ai-data-base.com/timeline/read/134139)
- Keywords: AI Agent Security / Deception / Honeypot / Task Contamination / Token Consumption

## In one paragraph

A research area where attacking or exploring AI agents are shown false leads or decoy environments in order to **increase their unnecessary tool runs, exploration turns, and reasoning tokens**. On top of the observation and isolation of ordinary honeypots, it evaluates the effect on the AI's limited budget and time. Defenders also pay costs, so both attacker-side and defender-side cost and damage have to be compared.

## Primary papers recorded

### 1. AgentLSD: false evidence sends AI agents on detours

- **Paper**: [AgentLSD: Evaluating AI Security Agents Under Adversarial Task Contamination](https://arxiv.org/abs/2609.19140)
- **Authors**: Matteo Golinelli, Idilio Drago, Matteo Boffa, Francesco Bergadano, Bruno Crispo
- **Published**: 2026-09-16 (first arXiv version)
- **Status**: abstract checked / full text not closely read
- **Question**: in security tasks such as CTFs, how do false evidence, hints, and endpoints affect an AI agent's decisions and exploration budget?
- **Method**: inserts fake flags, misleading hints, decoy endpoints, and similar into 11 web CTF challenges, and compares with the clean condition across 6 models. The legitimate solution is kept.
- **Main results (as stated in the abstract)**: 41% flag-capture in the clean condition. With decoys present, even successful cases take **+20** exploration turns and **about +2,000** reasoning tokens. The effect on success rate varies by model and challenge.
- **Why it's worth reading**: plausible "evidence" contamination alone, not simple prompt injection (commands), raises an agent's resource consumption.
- **Limitations and cautions**: results come from a controlled CTF setting. They do not directly guarantee anything about real-world attacks or monetary cost increases. The statistics behind the increases and the budget conditions need checking in the full text.
- **Reproduction plan (not done)**: in a CTF you own or are authorized to use, fix clean/trap conditions and measure success rate, turns, tool calls, tokens, total time, and both sides' costs.

### 2. HoneyRoute: forwarding malicious LLM requests to decoy models

- **Paper**: [HoneyRoute: Honeypot-Model Routing for Adversarial LLM Serving](https://arxiv.org/abs/2609.08306)
- **Author**: Han Jin
- **Published**: 2026-09-08 (first arXiv version)
- **Status**: abstract checked / full text not closely read
- **Question**: can malicious requests be isolated from the production LLM while the observed attack data improves detection?
- **Method**: a streaming classification router, a rule/prompt-based or dedicated replica-style decoy model, and a retraining loop that uses the observations.
- **Main results (as stated in the abstract)**: detection F1 **0.911**, median added latency **38 ms**. Under the test conditions, diverting malicious traffic **cut production-model token consumption by 97.8%**. F1 **0.933** after retraining.
- **Why it's worth reading**: an approach that **protects the defender's production model load**. It measures something different from AgentLSD's "extra consumption on the attacker/explorer side".
- **Limitations and cautions**: running a separate model and handling false positives have costs. The 97.8% is the production-model reduction under the stated load-test conditions, not the cost reduction of the whole system.
- **Reproduction plan (not done)**: compare with and without the router on synthetic or authorized requests, measuring false-positive rate, p95 latency, and combined production and decoy tokens/cost.

## How the two differ

| Aspect | AgentLSD | HoneyRoute |
|---|---|---|
| Target | Security AI that performs tasks and explores | Malicious requests sent to an LLM service |
| Decoy | Fake flags, hints, endpoints | A separate honeypot model |
| Main goal | Measure the effect of misleading and the AI's weakness | Isolate and observe on the production side, cut load |
| Metrics | Solve success, turns, reasoning tokens | Detection F1, latency, production token consumption |
| Caution | Extrapolating from CTFs to general attacks | Lower production consumption ≠ higher attacker cost |

## Checkpoints for the next read

1. Keep "higher attacker cost" and "lower defender cost" apart.
2. Check robustness against agents that see through decoys, effects over long attempts, and false positives.
3. Check the full text, appendix, and code, and record experimental conditions, confidence intervals, and reproducibility.
4. Limit experiments to your own CTFs or explicitly authorized test environments.

## Further candidates (unverified)

Two papers raised in an earlier conversation, "AgentTrap: Stateful Feedback Deception against Autonomous Penetration Testing Agents" (arXiv:2610.02869) and "LLM-Based Penetration Testing in the Presence of Honeypots" (arXiv:2609.08093), could not be confirmed to exist with matching bibliographic information from primary sources this time, so they are **excluded from the formal entries**. Recheck titles, IDs, and experimental numbers before adding them.

> This note is a reading memo based on abstracts as of 2026-10-10. It is neither a review paper nor a replication result.
