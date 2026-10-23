**English** | [日本語](2026-slopcodebench.ja.md)

# SlopCodeBench: Code Quality Under Iterative Agent Development

## Overview

- **What it is**: SlopCodeBench (arXiv 2603.24755), a benchmark of how code quality degrades when coding agents repeatedly extend their own code.
- **What it says**: It specifies only externally visible behavior, carries the agent's workspace forward across stages, and measures correctness separately from structural quality; quality-oriented prompts help some metrics but do not solve degradation.
- **Caveat**: Passing tests and completion reports alone do not show maintainable code; this note read the main text and some appendices but did not audit code or reproduce results.

## Key points

Completion reports and passing tests alone do not establish that evolving code remains maintainable. SlopCodeBench measures functional correctness separately from structural quality while agents repeatedly extend their own code. Quality-oriented prompts improve some quality measurements but do not establish a general solution to degradation.

This is a single-paper survey with a comparison to an existing reading record, not a systematic literature review.

## 1. Bibliography and verification status

- **Title:** SlopCodeBench: Benchmarking How Coding Agents Degrade Over Long-Horizon Iterative Tasks
- **Authors:** Gabriel Orlanski, Devjeet Roy, Alexander Yun, Changho Shin, Alex Gu, Albert Ge, Dyah Adila, Nicholas Roberts, Frederic Sala, Aws Albarghouthi
- **Year / venue:** 2026, arXiv preprint; peer-reviewed acceptance unconfirmed.
- **Version:** arXiv:2603.24755v2; first submitted 2026-03-25, revised 2026-05-07.
- **Primary sources:** [Record](https://arxiv.org/abs/2603.24755v2), [PDF](https://arxiv.org/pdf/2603.24755v2), [HTML](https://arxiv.org/html/2603.24755v2), [DOI](https://doi.org/10.48550/arXiv.2603.24755).
- **Author resource entry point:** [Code and leaderboard](https://www.scbench.ai/); implementation and distributed data not independently checked.
- **Checked:** 2026-10-20 JST.
- **Status:** primary PDF body §§1–5, Tables 1–3, execution conditions and Table 7 in Appendix C, and Appendix D.1 checked. Not every appendix was closely read; no code audit or reproduction.
- **Usage:** proposed / not trialed / not adopted. Operating ideas below are untested proposals.

## 2. Research question

Can an agent accommodate future requirements while living with its earlier design decisions? Single-shot bug-fix evaluations can miss designs that satisfy the current specification but make later changes difficult. Replacing an agent's code with a human-designed repository state between stages also breaks the accumulation of its own decisions.

SlopCodeBench specifies externally observable CLI/API behavior, leaves internal architecture open, and carries the agent's workspace forward. It observes correctness and quality throughout the trajectory (§§1–2).

## 3. Method and comparison conditions

The benchmark has 36 problems and 196 checkpoints, with 3–8 checkpoints per problem. Agents start from an empty workspace and receive each new specification with their previous code. Conversation history is reset. Evaluation tests and their feedback are hidden, unlike ordinary development with visible CI feedback.

The contracts are language-agnostic, but experiments evaluate Python only. Fifteen models are evaluated through different CLI harnesses. Each checkpoint runs in a fresh non-root Docker container; only the workspace persists, while installed packages, shell history, and session state reset. Each run has a two-hour wall-clock limit without turn or cost caps (§3, Appendix C). This compares model-and-harness configurations, not models under a common harness.

| Measure | Unit and success condition |
|---|---|
| Strict | All tests at a checkpoint, including earlier regression tests |
| Isolated / ISO | All non-regression tests for the current checkpoint |
| Core | Tests for explicitly stated or illustrated core behavior |
| Partial | A problem with at least one strictly solved checkpoint |
| Fully solved problem | Every checkpoint in that problem solved |

Strict, ISO, and Core use a fixed denominator of 196; unexecuted checkpoints after interruption count as unsolved. Quality metrics include only checkpoints with produced workspaces (§2.4).

### Quality metrics

Structural erosion measures concentration of complexity. For each callable:

`mass(f) = CC(f) × sqrt(SLOC(f))`

Erosion is the proportion of total mass in functions with cyclomatic complexity **greater than 10**. It is not mean CC or raw code size (§2.3, Equations 2–3).

Verbosity is the union of lines flagged by 137 AST-grep rules and structural clone lines, divided by LOC; overlapping detections count once (Equation 4). These are proxies, not direct measurements of security, readability, total maintainability, or maintenance effort.

## 4. Findings and evidence

### Correctness and cost

| Model, Table 1 setting | Strict (%) | ISO (%) | Core (%) | USD/checkpoint |
|---|---:|---:|---:|---:|
| GPT 5.5 | 14.8 | 28.1 | 66.8 | 1.51 |
| GPT 5.3 Codex | 11.2 | 26.0 | 60.7 | 0.66 |
| GPT 5.4 | 10.7 | 23.5 | 62.8 | 0.72 |
| Opus 4.6 | 9.7 | 20.9 | 67.3 | 3.17 |

Source: selected rows of Table 1, best just-solve run per model. These are historical experiment costs, not current product prices or a general production ranking.

No configuration fully solved any of the 36 problems. The best 14.8% is a **strict checkpoint solve rate**, not a fully solved problem rate. Mean cost per checkpoint rose 2.2× from start to finish (§3.1).

### Quality and repository calibration

Erosion increased in 77% of trajectories and verbosity in 75.5% (§3.2). The comparison panel contains 473 Python OSS repositories and 13,667 commits. Table 2 compares their HEAD snapshots with 2,869 agent checkpoints: mean verbosity 0.19 versus 0.44 and erosion 0.34 versus 0.68, approximately 2.3× and 2.0× (§3.3).

A human commit and an agent checkpoint do not represent controlled, equal work. These ratios cannot be translated into maintenance-cost ratios. The before/after-2024 repository analysis is observational and does not identify whether individual commits used AI.

### Prompt interventions

The anti-slop prompt lists patterns to avoid; plan-first requires planning before coding (§3.4, Table 3). For GPT 5.5, anti-slop changes erosion from 0.49 to 0.21 and verbosity from 0.32 to 0.21, while Strict falls from 14.8% to 9.2% and cost rises from USD 1.51 to 1.68 per checkpoint.

Improved quality metrics therefore do not establish overall task success. The text reports a mean 12.1% cost increase across the two interventions, without a general elimination of degradation. It also identifies GPT 5.4 with anti-slop as an exception improving from start to finish; degradation is not universal in every trajectory.

### Unresolved inconsistencies in the source

- §3.1 attributes the best Core value, 67.3%, to Opus 4.5; Table 1 assigns it to Opus 4.6 and gives Opus 4.5 57.7%. This record uses the table.
- The introduction reports a 2.3-percentage-point correctness drop, whereas §3.4 gives mean Strict drops of 2.4 points for anti-slop and 3.6 for plan-first. This record keeps Table 3 model-level values rather than asserting one pooled average.
- The abstract's approximately one-third improvement wording and larger condition-specific body improvements should not be conflated. Initial values, trajectory means, metrics, and intervention types need separate reconciliation.
- Table 7 omits Opus 4.7 and GPT 5.5, although Table 1 evaluates them. It does not establish harness versions for every evaluated model.

## 5. Related work and synthesis

| Dimension | SlopCodeBench | Existing [SWE-Journey record](2026-swe-journey.md) |
|---|---|---|
| Main question | How agents' own designs behave under repeated extension | How simulated user collaboration affects long-horizon implementation |
| State and interaction | Code persists; conversation resets between checkpoints | Long-horizon work includes simulated-user dialogue |
| Main measurements | Strict/ISO/Core, erosion, verbosity | Requested/existing behavior test passes and interaction behavior |
| Complementary contribution | Observes structural debt missed by functional tests | Observes requirement communication and acceptance |

This conceptual comparison uses the existing partially read SWE-Journey record, not a matched reevaluation. Different tasks and scoring units prevent direct score comparisons.

Our synthesis is to treat **requirement acceptance** and **continued structural observation** as separate axes. SlopCodeBench does not independently manipulate erosion to demonstrate that it causes correctness failures. Dedicated refactoring stages and independent review are plausible interventions but were not validated by this experiment.

## 6. Limitations and validity threats

1. **Generalization:** 36 authored tasks and Python implementations do not establish outcomes for large mature systems, other languages, or workflows with CI feedback.
2. **Metric construction:** AST patterns, clone detection, and the CC threshold embed judgments. Necessary duplication and domain complexity can raise scores; minimizing them mechanically can harm correctness.
3. **Human comparison:** repositories differ in maturity, selection, and change granularity, and may include AI assistance. This is not a controlled human-versus-AI trial.
4. **Configuration confounding:** model, harness version, and reasoning settings vary. Current products require fresh measurements.
5. **Missingness and reproducibility:** correctness counts missing checkpoints as failures while quality excludes them. Run variance and agreement with released code have not been independently checked here.
6. **Reporting:** the text/table inconsistencies above remain unresolved without reconciliation of the original aggregation.

## 7. Free-to-start reproduction plan and operational ideas

These are repository proposals, not executed experiments.

1. Use a small publishable Python CLI with four incremental specifications, withholding future requirements. Record specifications, initial state, model/harness versions, and settings.
2. Use existing access or a local model without purchasing additional API capacity for a pilot. Hardware and electricity are not inherently free.
3. Record new-feature and regression test results, CC distributions, changed lines, and duplication at each stage. Until the original 137-rule implementation is checked, label any substitute measurement as a proxy, not a reproduced SlopCodeBench Verbosity score.
4. Compare baseline with quality guidance; optionally add a structural-review condition. Measure correctness, structural change, elapsed time, and cost together without assuming improvement.
5. Treat a few runs as a case study. A substantive replication should use multiple runs and a prespecified analysis before generalizing intervention effects or model rankings.

For practical PR review, separately ask whether requirements are met and whether branches are accumulating in already complex functions. Merely requesting concise code is not a demonstrated quality guarantee.

## 8. Next checks

- Inspect author-released code, data, complete execution settings, run counts, and licenses.
- Reconcile text/table differences against released aggregation and revision history.
- Test whether proxy metrics correspond to actual modification effort in a small pilot.
- Keep proposed, trialed, and adopted statuses separate.

[Collection index](README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
