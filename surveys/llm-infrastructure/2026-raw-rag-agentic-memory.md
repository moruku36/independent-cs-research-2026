**English** | [日本語](2026-raw-rag-agentic-memory.ja.md)

# Is Complex Agentic Memory Always Needed? — Raw-RAG versus agentic memory

## Overview

- **What it is**: A preprint examining whether long-term conversation memory needs extraction, mutation, summarization, or graph construction.
- **What it says**: Raw-history retrieval plus reranking leads the compared memory systems in six of seven settings, excluding Full-context.
- **Caveat**: Offline public benchmarks do not establish superiority for every agent, production workflow, or deletion requirement. No code validation or reproduction was performed.

## Takeaways for people and PMOs

Before adopting complex memory management, establish a sufficiently tuned raw-history retrieval baseline. The useful evaluation distinction is between supplying necessary evidence and answering correctly once it is supplied. Neither “any RAG is enough” nor “memory management is unnecessary” follows from this work.

## Survey record

- **Status**: Primary HTML checked; partially read: main §§1–6, principal tables, selected Appendix A material, Appendix B, and parts of C. Remaining appendices, PDF cross-checking, code validation, and reproduction are unperformed.
- **Bibliography**: Zhengye Bao, Shengtao Zhang, Haokai Zhang, Shiqi Lou, Muning Wen, Minnan Luo. *Is Complex Agentic Memory Always Needed? Naive RAG Is Stronger Than We Thought*. October 22, 2026. arXiv:2610.30755v1 [cs.AI]. Preprint; peer review and acceptance venue unverified.
- **Primary URLs**: [HTML v1](https://arxiv.org/html/2610.30755v1) / [bibliography and version history](https://arxiv.org/abs/2610.30755) / [PDF v1](https://arxiv.org/pdf/2610.30755v1).
- **Checked on / version**: 2026-10-24 JST / v1. Numerical results below are author-reported, not independently recalculated.
- **Research question**: What additional value do explicit state mutation and structured memory provide over a well-configured raw-history RAG baseline for conversational QA?
- **Method, data, comparison**: A fixed source-preserving retrieval pipeline is compared with memory systems and Full-context on LoCoMo, LongMemEval, MEME, and MemoryAgentBench. Readers, retrieval configurations, and averaging schemes vary across benchmarks.
- **Claims and evidence**: Main §§3–5, Tables 3–9, and Appendices A–B; key findings and boundaries appear below.
- **Limitations / validity threats**: Results depend on readers, evidence length, timestamps, retrieval settings, judges, and the distinction between published and rerun results. LLM sufficiency judgments can err. Conditional utilization uses different question subsets for different systems, so it is not a controlled comparison of reader ability alone.
- **Related work**: See the comparison below. Comparator papers were not independently read closely in this task; descriptions are restricted to this paper's treatment.
- **Free reproduction idea**: Test retrieval, support recovery, and temporal preservation on a small public or synthetic sample using existing local resources. The plan below is unexecuted.
- **Usage status**: Design proposal only; no implementation adoption or demonstrated accuracy gain.
- **Open checks**: Implementation and experiment-log availability, dependency versions, complete reader settings, grading prompts, cost accounting, statistical uncertainty, and operational deletion behavior.

## Method and evaluation conditions

Raw-RAG retains dates, speakers, and source text. Its default uses 256-token windows with 32-token overlap, dense retrieval of 128 candidates, and a cross-encoder selecting 15 items for the reader. LLM-based fact replacement and summarization are absent from the default pipeline.

**Fifteen selected items are not a fixed evidence-token budget.** Turn expansion can increase reader-visible length. Display rules also vary: MEME orders selected evidence chronologically, while MemoryAgentBench disables turn expansion. The 5,000-token controls are separate interventions (Appendices B–C).

LoCoMo and LongMemEval comparisons mix published scores and evaluations in this study, distinguished by corresponding settings in Appendix A. Do not describe all systems as rerun under one identical software and model configuration.

## Principal results

| Aspect | Author-reported result | Interpretation |
|---|---|---|
| Main comparison | First among memory systems in six of seven settings; margins of 0.13–5.53 points over the strongest comparator | Excludes Full-context; does not mean best on every subtask |
| Exception | DeepSeek-V4-Flash MEME: Raw-RAG 43.19%, MemMachine 44.71%, Full-context 63.17% | A clear exception to universal superiority |
| Removing reranking | MemoryAgentBench falls from 48.32% to 44.40% | A simple baseline still needs adequate retrieval design |
| Added management | Fact extraction, summary augmentation, and graph expansion each reduce aggregate accuracy in the tested setting | Evidence about those implementations, not every possible structured-memory method |
| Ingestion plus retrieval | 305.91 seconds for 10 MEME episodes and 110 questions | Excludes answer generation and evaluation; not end-to-end response time or API billing |

Evidence: §4, Tables 4–6, Appendices A–B. Some in-text table references in the HTML are displaced; consult section headings and table captions together.

## Preserving evidence and its relationships

The authors distinguish evidence coverage from conditional utilization. Raw history may preserve both an answer value and the temporal or dependency path explaining why it is current.

A complete-store diagnostic using gold-informed selection still leaves a gap to raw evidence. This oracle is not a deployable retriever, and its residual gap cannot be attributed entirely to ingestion information loss: assembly and positional effects remain possible (§5, Appendices A.5 and C.5).

The Mem0 mutation intervention evaluates downstream QA. **Invalidating an old fact in an answer and physically removing stored data are separate requirements.** It does not justify omitting actual deletion.

## Relationship to other approaches

| Approach | Role in this note |
|---|---|
| Raw-RAG | Source-preserving retrieval baseline; the reader reconstructs relevant state |
| Mem0, MemOS, EverMemOS, and others | Systems whose extraction, mutation, structure, or retrieval control should demonstrate additional value |
| MemMachine | Retains raw conversational material in the evaluated store and wins one reported setting |
| Full-context | Can avoid retrieval omissions but remains subject to context limits and positional effects |
| [Cache Engineering for Agents](2026-cache-engineering-for-agents.md) | Controls active KV caches rather than external long-term retrieval. Possible combination is this note's proposal, not an experimental finding |

## Repository discussion and unexecuted check plan

1. Freeze a small public or synthetic conversation set containing corrections, expiry, deletion requests, and dependent changes. Define questions and gold supporting passages before testing; start without personal conversation logs.
2. Compare raw retrieval, summary retrieval, and a combined representation under the same reader, questions, and budget. Record embedding model, reranker, candidate count, evidence tokens, and ordering.
3. Measure accuracy, support and dependency-path recovery, stale-fact use, abstention, and ingestion/retrieval/generation times separately.
4. Use existing local resources or free allowances for the retrieval pilot. A changed model or hardware makes this exploratory work rather than numerical reproduction.
5. Independently test authorization boundaries, retention periods, retrieval exclusion after deletion, and physical removal, including propagated changes to summaries and derived indices.

For adoption, first establish raw-preserving retrieval as a comparison baseline, then measure what structure adds. QA scores alone are insufficient grounds to remove operational update, deletion, or audit functions. These are repository proposals, not completed work.

## Sources and verification scope

- Bao et al., 2026, [primary HTML v1](https://arxiv.org/html/2610.30755v1), labeled CC BY 4.0. This note provides original synthesis, comparison, and discussion rather than reproduced figures.
- Comparator-paper checks, PDF cross-checking, and code/experiment validation remain unperformed. This record rests on inspected body text and tables, not the abstract alone.

[Theme index](README.md) | [All themes](../README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
