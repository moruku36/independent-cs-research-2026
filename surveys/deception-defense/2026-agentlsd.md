**English** | [日本語](2026-agentlsd.ja.md)

# AgentLSD: Injecting False Information into AI Security Agents

## Overview

- **What it is**: AgentLSD (arXiv 2609.19140), a study of how false evidence planted in a task environment affects AI security agents; only the abstract was checked.
- **What it says**: Using 11 web CTF challenges and 6 models, it reports a 41% flag-capture rate in the clean condition, and traps added about 20 turns and 2,000 reasoning tokens even when the agent still solved the challenge.
- **Caveat**: CTFs differ from real networks and the full text was not closely read, so aggregation, variance and per-model detail are unconfirmed; nothing was reproduced.

- **Status**: primary source (arXiv abstract) checked / full text not closely read / not reproduced
- **Title, authors, year, venue, ID, primary URL**: *AgentLSD: Evaluating AI Security Agents Under Adversarial Task Contamination* / Matteo Golinelli, Idilio Drago, Matteo Boffa, Francesco Bergadano, Bruno Crispo / 2026 / AISec 2026 (announced; to be confirmed) / arXiv:2609.19140 / [primary paper](https://arxiv.org/abs/2609.19140)
- **Date checked and version**: 2026-10-10 / arXiv abstract (version not pinned; full text not cross-checked)
- **Research question**: how does false evidence planted in a task environment change a security AI's success rate and exploration resources?
- **Method, data, comparison conditions**: 11 web CTF challenges, 6 models. A clean environment is compared in pairs with conditions that inject fake flags, misleading hints, decoy endpoints, and similar. The legitimate solution path is kept intact.
- **Claims and evidence**: the abstract reports a 41% flag-capture rate in the clean condition. Even when the agent still solves the challenge, traps added about 20 turns and about 2,000 reasoning tokens. The effect differs by model and challenge.
- **Limitations and threats to validity**: CTF settings differ from real networks. How the increments were aggregated, their variance, the reproduction procedure, and per-model differences need the full text. This is not proof that an attacker's API cost always rises.
- **Comparison with related work**: [HoneyRoute](2026-honeyroute.md) is an operational scheme that routes malicious requests to a production LLM into a decoy model. This paper measures the robustness and resource use of security agents against false evidence.
- **Free-to-run reproduction plan**: keep the legitimate solution in a CTF you own, then compare clean vs. trap conditions with the same model and budget. Record success rate, turns, tool calls, reasoning tokens, and time. **Not done.**
- **Usage status**: proposed (an item for evaluating AI security agent robustness). Not trialed or adopted.
- **Unconfirmed points and next checks**: check the full text, appendix, public code and license; settle mean vs. median, statistical significance, reproducibility, and venue.

Related: [thematic comparison](legacy/2026-ai-agent-honeypot-deception.md) / [reading list](../../docs/reading-list.md)
