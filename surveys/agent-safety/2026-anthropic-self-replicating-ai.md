**English** | [日本語](2026-anthropic-self-replicating-ai.ja.md)

# Self-replicating AI outside datacenters: a critical survey

## Bibliography and verification status

- Primary source [S1]: William Zhou and Daniel Freeman, [AI models may be capable of self-replicating without access to a datacenter](https://www.anthropic.com/research/self-replicating-ai), Anthropic, 2026-10-12.
- Type: institutional research article; no peer-reviewed venue, DOI, or arXiv identifier confirmed for this article.
- Checked: 2026-10-24 JST; main HTML sections, experimental qualifications, mitigations, and Appendix A read. Interactive plots, underlying datasets, remaining appendices, and implementation were not independently checked.
- Related sources: abstracts and bibliographic records checked for [Petals S2](https://arxiv.org/abs/2209.01188v2) and [AI Agents Enable Adaptive Computer Worms S3](https://arxiv.org/abs/2606.03811v1). Neither related paper was read in full or reproduced.
- No propagation, exploitation, model deployment, or replication experiment performed. Focused survey note, not a systematic review.

## Research question, method, and evidence

Can small models establish inference and compose replication steps on modest hardware? S1 reports a 9B model setting up inference on 8/9 hardware types and distributed 26B inference on 15 TV boxes at 0.39 tokens/s. Its contained eight-node experiment simplifies access and uses external inference for the acting model while deploying Llama3.1-8B. GLM-5.2 reaches 8/8 nodes in four of five trials and 7/8 in one. This is not an observed autonomous Internet outbreak. The year-end capability projection is extrapolation, not demonstration. [S1, introduction and §§A–B]

## Critical interpretation

Survey analysis: evaluate the hardware demonstration, orchestration evaluation, and future prediction as separate claims. A result about running a model cannot establish that the same model can reliably execute a long sequence of tasks. Likewise, successful task orchestration with an external service is not a demonstration of an entirely self-contained replica.

| Question for an evaluation | Why record it? |
|---|---|
| Where does the acting model run? | Separates local autonomy from dependence on external inference. |
| Which steps are automated by the evaluator? | Avoids attributing harness behavior to the model. |
| What access is already provided? | Prevents a setup test from being described as a general intrusion result. |
| What counts as an independent trial? | Needed to distinguish repeated success from one favorable trajectory. |
| Does a new instance act without evaluator assistance? | Distinguishes inference setup from autonomous continuation. |

These are proposed assessment criteria, not newly measured findings.

## Limitations and threats to validity

The central external-validity issue is the gap between a constrained evaluation and heterogeneous deployed networks. A useful follow-up should vary connectivity, available memory, failure recovery, and the division of work between the harness and model. Estimate uncertainty separately for each stage; multiplying optimistic stage estimates would not establish reliable end-to-end behavior.

Defensive implications proposed here: maintain an inventory of inference-capable devices, separate device networks, and baseline unusual sustained transfers or peer traffic. Measure false positives and time to isolation using benign traffic. These are assessment proposals, not proven controls against every adaptive agent.

## Comparison with related research

| Source and checked scope | Contribution | Difference from S1 |
|---|---|---|
| S2: Borzunov et al., Petals, arXiv:2209.01188v2; abstract only | Cooperative inference and fine-tuning across participants | Distributed execution by itself is not evidence of malicious autonomous replication. |
| S3: Guan et al., AI Agents Enable Adaptive Computer Worms, arXiv:2606.03811v1; abstract only | Reports adaptive propagation in a test network across heterogeneous systems | A complementary research direction; no quantitative cross-study comparison is justified from abstracts. |
| [Formal verification](../coding-agents/2026-anthropic-formal-verification.md) | Survey of bounded software guarantees | Verifying a component does not settle an agent's authority or network reach. |

S2 is a legitimate distributed-computing system, not presented here as malware. S3's authors' conclusions remain author claims; this note has not verified their full methods.

## Free-to-run reproduction plan

Proposed, unexecuted: build a local mock state machine with fictional devices and inert payload identifiers. Use deterministic scripted actions to test the measurement pipeline: provided access, setup success, continuation, evaluator intervention, time, and cost. Add simulated resource and network failures, and keep every trial's log.

This can validate definitions and defensive instrumentation without downloading model weights, calling a paid API, or implementing a worm. It does **not** reproduce S1's capability results. A separate manual review can map already-collected benign flow logs to detection hypotheses and record false positives.

## Usage status and next checks

**Proposed only; not trialed or adopted.** Candidate use: a threat-model checklist for local inference and agent execution environments.

Next: inspect plot data and full appendices; identify released harness artifacts and exact model revisions; read S2/S3 in full; examine how success grading separates setup from autonomous execution. The unresolved question is how the result changes when the acting model must run within the same resource limits as the proposed replica.

## References

- S1: [Anthropic research article](https://www.anthropic.com/research/self-replicating-ai), especially §§A–B and Appendix A.
- S2: Alexander Borzunov et al., [Petals: Collaborative Inference and Fine-tuning of Large Models](https://arxiv.org/abs/2209.01188v2), 2023 revision of 2022 preprint; abstract only.
- S3: Jonas Guan et al., [AI Agents Enable Adaptive Computer Worms](https://arxiv.org/abs/2606.03811v1), 2026-06-02; abstract only.

[Theme index](README.md) | [Survey index](../README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
