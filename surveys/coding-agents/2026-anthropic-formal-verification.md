**English** | [日本語](2026-anthropic-formal-verification.ja.md)

# LLM-assisted formal software verification: a critical survey

## Overview

- **What it is**: An Anthropic and Theorem research article (2026-10-22) on using LLMs to make formal software verification feasible at larger scale; this note is a critical survey of it.
- **What it says**: Fuzz harnesses become specifications over compiled RISC-V binaries and Claude builds proofs checked by Rocq, reported as 239 entry points in 123 libraries and about 180 million accepted proof lines.
- **Caveat**: A proof covers particular compiled artifacts under stated assumptions, not whole-library correctness; nothing was independently proof-checked or replicated here.

## Bibliography and verification status

- Primary source [F1]: [LLMs are making formal software verification feasible at a much larger scale](https://www.anthropic.com/research/formal-verification), Anthropic / Theorem, 2026-10-22.
- Listed authors: Keane Lucas, Aengus Lynch, Luna Tong, Luke Champine, Zygi Straznickas, Dino Distefano, Harshikaa Agrawal, Evyatar Ben Asher, Ava Howell, Sami Jawhar, Chris Rohlf, Nickolai Zeldovich, Nicholas Carlini, Rajashree Agrawal, Jason Gross.
- Type: institutional research article with technical appendix and public artifacts. No peer-reviewed venue, DOI, or arXiv identifier confirmed for this article.
- Checked: 2026-10-24 JST; current HTML main sections and limitations read; [appendix F2](https://www-cdn.anthropic.com/files/4zrzovbb/website/6867eadf760258fa8b42a504600cd3c036d16358.pdf) text on proof statements and interpreter checked; public [proof repository F3](https://github.com/theorem-labs/oss-verify-proofs) README checked.
- Not done: independent proof checking, binary rebuilding, code audit, or replication. This is a focused survey note, not an original experiment or systematic literature review.

## Research question and approach

Can machine-checked evidence supplement the test-based acceptance of AI-written changes? F1 transforms fuzz harnesses into specifications over compiled RISC-V binaries; Claude constructs proofs, checked by Rocq. It reports 239 entry points across 123 libraries and approximately 180 million accepted proof lines. Its scope is restricted by the input bound (under 64 MB), single-threaded static binaries, and modeled execution environment. These are reported outcomes, not independently reproduced measurements. [F1, “Turning tests into proofs”]

## Evidence and interpretation

| Evidence source | What was checked | Reading implication |
|---|---|---|
| F2, “What our OSS-Fuzz proofs prove” | Crash freedom of plain and instrumented binaries plus agreement of observable behavior under the model | Review the theorem and its premises before interpreting “verified.” |
| F3, README | Public release lists 60 entry points in 25 libraries; it uses agreement statements and explicitly does not establish termination | Keep released artifacts separate from F1's larger project totals. |
| F3, “What a proof does not say” | Claims concern particular compiled artifacts and reachable harness code, not whole-library correctness | A source revision or deployment change requires a new applicability assessment. |

F2 also distinguishes an interpreter's proof against formal semantics from empirical agreement with CPython. The reference semantics itself therefore needs scrutiny; a high test agreement rate cannot establish semantic identity. [F2, “Building a Python interpreter in Rust”]

## Limitations and threats to validity

F1's assumptions do not establish safety for arbitrary x86/ARM deployments or all library entry points. [F1, “Limitations”]

Survey interpretation: acceptance should be attached to a tuple of source revision, binary, harness, theorem, execution model, and checker. A change to any component should invalidate automatic reuse until assessed. Counting proof lines is insufficient for deciding whether the property matters to users. A successful checker result also says little about proof-generation affordability without elapsed time, resource use, and failed-attempt costs.

The observed difference between project totals and public release totals is a scope difference to track, not evidence that either count is false. Current released statements also warrant more precise wording than a blanket claim that every execution exits normally. [F3]

## Comparison with related work

This is a conceptual comparison, not a head-to-head performance result.

| Existing repository note | Comparison proposed by this survey |
|---|---|
| [FlowAgent](2026-flowagent.md) | Test-based repair acceptance versus acceptance of an explicit theorem; both need checks that the repair preserves intent. |
| [SlopCodeBench](2026-slopcodebench.md) | Structural quality should remain a separate review axis even when a property is proved. |
| [Self-replicating AI](../agent-safety/2026-anthropic-self-replicating-ai.md) | Local software guarantees and environment-level agent containment answer different security questions. |

## Free-to-run reproduction plan

Proposed, unexecuted: select one public F3 target, pin its commit and binary hashes, inspect its premises, and recheck the existing proof using the documented open-source toolchain. Record checker version, assumptions, wall time, peak memory, result, and any omitted checks. This needs no paid inference API; it is artifact verification, not reproduction of AI proof generation. F3 warns that checking can require substantial memory, so assess one target before execution.

A later experiment could compare the same unchanged harness under fuzzing and proof checking, with a fixed budget and failures retained. Do not count resource exhaustion as disproof.

## Usage status and next checks

**Proposed only; not trialed or adopted.** Candidate use: attach theorem scope and artifact identity to a dependency review.

Next: pin the F3 release commit; reconcile each chosen target with F1/F2; inspect the [execution semantics](https://github.com/theorem-labs/rocq-linux-process-semantics); determine how patches preserve intended behavior; estimate proof-generation cost separately from checking cost.

## References

- F1: [Anthropic research article](https://www.anthropic.com/research/formal-verification).
- F2: [Technical appendix](https://www-cdn.anthropic.com/files/4zrzovbb/website/6867eadf760258fa8b42a504600cd3c036d16358.pdf).
- F3: [Theorem OSS Verify proofs and checking documentation](https://github.com/theorem-labs/oss-verify-proofs), mutable README checked 2026-10-24; not executed.

[Theme index](README.md) | [Survey index](../README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
