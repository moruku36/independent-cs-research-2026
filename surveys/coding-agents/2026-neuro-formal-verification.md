**English** | [日本語](2026-neuro-formal-verification.ja.md)

# Neuro-Formal Verification: Agentic Language-Agnostic Formal Program Reasoning

## Overview

- **What it is**: A preprint on translating program reasoning into verifier-checkable artifacts.
- **What it says**: A staged pipeline combines neural translation with formal checking.
- **Caveat**: Checking the translated model does not establish source-program soundness.

## Bibliography and verification

Shuvendu K. Lahiri, Microsoft Research, 2026, arXiv:2608.21516v1, dated 2026-08-21. Preprint; peer-reviewed acceptance not checked. Checked 2026-10-25 JST: HTML introduction, method, evaluation, error analysis, and conclusion; appendices partially checked. No PDF cross-check, code execution, or reproduction. [N1, N2]

## Question, method, and evidence

Can mainstream code obtain useful checked reasoning without a complete symbolic frontend? The agent formalizes assumptions, translates code and properties, then searches for proofs. Dafny and CBMC instantiate the approach. The dataset has 206 Python program/specification pairs; the main evaluation uses gpt-5.6-sol, five attempts, and ten repair rounds. [N1, §§1–4]

| Reported result | Correct verdicts / issued | Denominator for recall |
|---|---|---|
| Dafny combined pipeline | 118 / 128 = 92.2% precision | 118 / 206 = 57.3% |
| CBMC refutation | 65 / 72 ≈ 90% precision | 65 / 103 buggy programs ≈ 63% |

These rows measure different populations. Precision excludes abstentions; 57.3% is correct-verdict recall, not the fraction receiving any verdict (128/206). Translation and assumption errors remain possible. [N1, Table 3, §§4.2–4.3]

## Critical interpretation and validity

This survey's assessment: evidence should carry two separate judgments: whether the checker accepted the target artifact, and whether that artifact faithfully represents the intended source behavior. A proof log can support the first without resolving the second.

For review, retain a correspondence record:

| Proposed review item | Question |
|---|---|
| Input domain | Were empty, negative, non-integer, and exceptional values excluded intentionally? |
| Environment | Does the library model come from an independent contract? |
| Artifact identity | Did the program or property change during proof repair? |
| Counterexample | Can the witness be replayed in the original language? |
| Inconclusive outcome | Is timeout or missing proof recorded without calling it correctness or a bug? |

These are proposed review questions, not additional experiments. A small function benchmark is insufficient to infer reliability for stateful services, distributed execution, or dependency-heavy applications. A verifier can make a bad abstraction look authoritative; preserve the abstraction for inspection.

## Related-work comparison

Conceptual comparison, not an experimental ranking:

- [Anthropic formal verification](2026-anthropic-formal-verification.md): compare the theorem, execution model, and artifact correspondence before comparing headline scale.
- [FlowAgent](2026-flowagent.md): compare proof-backed obligations with test-backed acceptance.
- [Reward hacking](../agent-safety/2025-reward-hacking-emergent-misalignment.md): investigate whether an acceptance mechanism can be satisfied while the user's requirement changes.

## Free-to-run check plan

Proposed, unexecuted: manually translate one tiny pure function, pin the specification and assumptions, and use a locally installed open-source checker. Include an intentional bug and replay its witness in Python. Try a second abstraction that excludes the failing input and document why its accepted proof answers a narrower question. Record versions, file hashes, runtime, and all outcomes.

This checks the trust boundary without paid inference. Reproducing agentic generation additionally requires the paper's prompts, artifact availability, model access, and compute budget; those are unresolved.

## Usage and next checks

**Proposed only; not trialed or adopted.** Next: locate and pin experiment artifacts, inspect assumption provenance, and audit abstentions and mislabeled cases before attempting an independent run.

## References

- N1: [Versioned primary HTML](https://arxiv.org/html/2608.21516v1), especially §§1, 3–4, Table 3.
- N2: [Versioned arXiv record](https://arxiv.org/abs/2608.21516v1).

[Theme index](README.md) | [Survey index](../README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
