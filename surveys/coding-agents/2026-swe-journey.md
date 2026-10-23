**English** | [日本語](2026-swe-journey.ja.md)

# SWE-Journey: Evaluating Long-Horizon, Interactive Coding Assistance

## Overview

- **What it is**: SWE-Journey (arXiv 2610.11559), a benchmark for coding assistants in long, multi-turn development where requirements change step by step.
- **What it says**: It simulates four user personas on 30 tasks (594 subtasks) with 13 models, and the functional-test pass rate varies a lot with the simulated user's collaboration style.
- **Caveat**: Users are simulated and tasks are small and synthetic, so it does not show success rates for real users or the causal effect of expertise alone.

## Key points for people and PMOs

- **What we learned**: even on the same task, the pass rate of functional tests changes a lot with the simulated user's collaboration style. An AI's own completion report is not enough to judge the outcome.
- **What it's useful for**: a source of points when designing acceptance criteria for AI development, handoff of requirements, and verification after changes.
- **Caution**: this is an evaluation with simulated users. It does not show success rates for real users by job role, nor the causal effect of expertise alone.
- **Next step**: prepare an acceptance record that separates requirements, verification results, and open issues. The operating ideas below are untested and no experiment was run.

## Survey record

- **Status**: primary text checked / partially read. Checked body §1–5, Appendix A.3–A.4, B.1–B.3, B.5, and the description of C. A verbatim close read of all appendices and reproduction not done.
- **Title, authors, year, venue, ID, primary URL**: *SWE-Journey: Towards More Realistic Evaluation of Coding Assistants through Long-Horizon, Multi-Turn Interaction* / Hexuan Deng et al. / 2026 / arXiv preprint (peer-reviewed acceptance not confirmed). [arXiv:2610.11559v1](https://arxiv.org/abs/2610.11559v1), [HTML](https://arxiv.org/html/2610.11559v1), [PDF](https://arxiv.org/pdf/2610.11559v1), [DOI](https://doi.org/10.48550/arXiv.2610.11559) (value shown by arXiv; it carries a pending-registration notice and the redirect target is unconfirmed).
- **Date checked and version**: 2026-10-12 UTC / v1 (submitted 2026-10-08). The introducing article [AIDB 134413](https://ai-data-base.com/timeline/read/134413) could not be retrieved and its content is not cited. Everything below is based on the original paper.
- **Research question**: in long-horizon development where requirements change step by step, can an AI work with the user to implement features while keeping existing ones intact?
- **Method, data, comparison conditions**: tasks are composed in stages, and four personas derived from SWE-Chat are simulated with GLM-5.2. 30 tasks and 594 subtasks are evaluated on 13 models, using mini-swe-agent and a persistent Docker environment (§3–4, B.1). This is not a comparison of the commercial Claude Code or Codex products themselves.
- **Claims and evidence**: per-persona mean Final F2P is in the table below. The paper analyzes requirement elicitation, locating changes, and grounded fixes as tasks (§4.2).
- **Limitations and threats to validity**: small synthetic tasks, simulated users, and bias of the generating model. Expertise, control, requirement change, and verification conditions vary at once. The Non-coder condition is set to change goals easily for coverage and does not reproduce real population distributions (§5, A.3). Realized interaction volume and compute are not equal either (B.1). Behavior analysis is LLM-judged, and the Fix metric is missing for models without reasoning traces (B.3).
- **Comparison with related work**: adds staged requirements and persistent code state to earlier one-shot fix evaluations (§2). It can be used together with the existing [permission-deviation evaluation](../agent-safety/2026-unsanctioned-supply-chain-attacks.md), as they view different aspects: adherence to permissions versus correctness of outcomes. Do not compare defensive-effect numbers side by side.
- **Free-to-run reproduction plan**: manually check the acceptance record below against a small fictional change with a known correct answer. This does not reproduce the paper's model experiments.
- **Usage status**: proposed / not trialed / not adopted. This is a record of reading the published paper, not demonstration of operational improvement.
- **Unconfirmed points and next checks**: where the public implementation and data are and how to reproduce, variance across repeated runs, and generalization to real users. No experiments, paid runs, or environment configuration changes were made this time.

### Numbers and evaluation unit

| Simulated user condition | Final F2P (%) |
|---|---:|
| Non-coder | 23.00 |
| Product Manager | 30.48 |
| New Developer | 35.57 |
| Software Architect | 78.50 |

Source: Table 2 of the original paper. Each condition is the mean over 13 models. Recorded test nodes are aggregated across tasks per model and persona. The model-level values in Table 1 are equal-weight means of the four personas. **These are test pass rates, not the share of tasks fully solved** (§3.4). Final F2P is the requested feature; Final P2P is preservation of existing features. Proc. F2P is measured at the point where the user believes a stage is complete. The paper's Average is the mean of these three metrics and differs from feature completion rate. Cost comparisons also exclude the simulated user's token cost (B.1).

## Applying this to our own AI operations

These are design ideas of this repository, not measures whose effect the paper demonstrated.

1. **Make the goal verifiable**: attach "the result the user wants to see," "behavior that must not change," and "acceptance examples" to the request. Clarify only the ambiguities that steer implementation, with concrete examples; do not make the number of questions a goal.
2. **Tie changes to evidence**: for each requirement, record the affected location, the diff, and the verification result. Do not stretch a passing local test into evidence that the whole is complete.
3. **Separate stages from the final**: after a stage, check the new feature; at the end, recheck earlier requirements and existing behavior. Match screens and output examples that a non-technical person can check with the technical owner's verification.
4. **Carry corrections forward**: leave a short note of goals, acceptance conditions, reasons for changes, and known failures. Pass it to later AIs and distinguish "handled" from "unconfirmed."

Example acceptance record for a PMO:

| Requirement | Expected result | Diff / artifacts | Verification method and result | Unconfirmed / open items |
|---|---|---|---|---|
| Fictional example: add filtering to a list | Shows only items matching the given condition | Target screen and changed locations | Compare output with and without the condition | Boundary conditions and existing operations unconfirmed |

In the manual check, see whether this record can catch changes that differ from intent, changes that only pass the acceptance example, and defects that come back after later changes. Do not assume success; use the conditions that were missed to improve the record.

## Summary

SWE-Journey evaluates long-horizon coding collaboration with simulated users. The reported persona differences combine expertise, control, changing goals, and verification; they do not isolate expertise or estimate real-user success rates. Scores measure test-node passes, not fully solved tasks. Primary text checked; partial reading, no reproduction. The acceptance-record workflow above is our untested proposal.

[Collection index](README.md) | [Reading list](../../docs/reading-list.md)
