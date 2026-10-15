**English** | [日本語](2026-honeyroute.ja.md)

# HoneyRoute: Routing Malicious LLM Requests to Decoy Models

- **Status**: primary bibliographic information and abstract checked / full text not closely read / not reproduced
- **Title, authors, year, venue, ID, primary URL**: *HoneyRoute: Honeypot-Model Routing for Adversarial LLM Serving* / Han Jin / 2026 / arXiv preprint (peer-reviewed venue not confirmed) / arXiv:2609.08306 / [primary paper](https://arxiv.org/abs/2609.08306)
- **Date checked and version**: 2026-10-10 / public abstract (arXiv lists several versions; pin one before reproducing)
- **Research question**: can malicious LLM requests be separated from the production model while still improving attack observation and the classifier?
- **Method, data, comparison conditions**: a router with a 0.8B embedding backbone plus per-domain classification heads makes the call. Flagged requests go to a rule/prompt-based honeypot or a replica-style honeypot of a similar model, and the router is retrained on the observed attack features. Uses operational traces and attack data from 7 domains.
- **Claims and evidence**: the abstract reports detection F1 = 0.911, median added latency of +38 ms, a 97.8% reduction in **production-model** token consumption in a concurrent load test where malicious traffic is diverted, and F1 = 0.933 after retraining.
- **Limitations and threats to validity**: the production-side reduction is not the reduction in total cost including the honeypot. Watch false positives, the operational burden of replicas, distribution shift, and attacker adaptation. The evaluation population and confidence intervals behind the numbers need checking in the full text.
- **Comparison with related work**: [AgentLSD](2026-agentlsd.md) measures the exploration resources a security AI wastes when misled by false evidence. This paper centers on protecting LLM-serving infrastructure and routing requests.
- **Free-to-run reproduction plan**: with a local mock LLM endpoint and synthetic requests, compare with and without the router, measuring F1, false positives, p50/p95 latency, production vs. decoy tokens, and total compute cost. **Not done.**
- **Usage status**: proposed (for considering LLM gateway designs). Not trialed or adopted.
- **Unconfirmed points and next checks**: examine the full text, version number, data availability, classifier training conditions, handling of false positives, and operating cost.

Related: [thematic comparison](../2026-ai-agent-honeypot-deception.md) / [reading list](../../docs/reading-list.md)
