**English** | [日本語](2026-fold-subagents-main-loop.ja.md)

# When to fold subagents into the main agent loop

## Overview

- **What it is**: A practitioner article about simplifying agent architecture.
- **What it says**: Evaluate consolidation around shared context, skills, and tools.
- **Caveat**: Deployment anecdotes do not establish a universal performance ranking.

## Bibliography and verification

Diane Sarkis, *Building agents: When to fold subagents into your main agent loop*, Claude/Anthropic, 2026-10-22. Technical article, not a peer-reviewed paper; no DOI identified. Checked 2026-10-25 JST: article body and linked migration-kit landing page; kit not executed. [S1, S2]

## Question, method, and evidence

Which specialist boundaries improve task completion? S1 describes enterprise experience with progressive disclosure and shared end-to-end evaluation. It recommends retaining subagents for context isolation, independent parallel work, or conflicting tool/instruction requirements, and migrating one boundary at a time. An approximately twofold runtime improvement is one customer's observation, not a controlled benchmark. Tools should enforce permissions; skills supply procedures. [S1, “Using an agent loop,” “Task-completion evals,” “MCP tools”]

## Critical interpretation and validity

This survey's interpretation: the useful unit of decomposition is a dependency boundary. A planner and executor repeatedly exchanging the same evolving evidence deserve a consolidation experiment. An independent checker with a different permission set deserves a separate assessment. Neither decision follows from the number of teams owning the workflow.

The article does not provide enough common workload, sampling, variance, or cost-accounting detail to reproduce a comparative effect size. Treat its migration advice as a hypothesis generator. Faster completion could reflect skipped work; an evaluation must check obligations such as actually consulting the system that supplies a delivery date.

An audit should therefore distinguish:

| Proposed review axis | Evidence to retain |
|---|---|
| Task completeness | Required source lookup and acceptance conditions |
| Context continuity | Lost facts at each handoff |
| Isolation | Which component can read, write, or approve |
| Efficiency | Wall time, tokens, retries, and failed runs |

These are this survey's proposed assessment criteria, not additional reported results. A smaller agent graph must not silently broaden permissions.

## Related-work comparison

Conceptual connections, not benchmark comparisons:

- [FlowAgent](2026-flowagent.md): compare workflow acceptance and resource budgets.
- [Neuro-formal verification](2026-neuro-formal-verification.md): ask which constraints need enforcement outside model reasoning.
- [Reward hacking](../agent-safety/2025-reward-hacking-emergent-misalignment.md): include checks for apparently successful but invalid outcomes.

## Free-to-run check plan

Proposed, unexecuted: use ten fictional support cases and manually replay a fixed set of tool responses. Compare a specialist handoff and a shared-context procedure against the same rubric; repeat ambiguous cases. Record omitted obligations and permission differences before timing. This is a free protocol check, not an inference-performance reproduction. A live model comparison requires a separately recorded model and compute budget.

## Usage and unresolved checks

**Proposed only; not trialed or adopted.** Next: pin an S2 commit, inspect its evaluation harness, select a real workflow, and predeclare completeness and permission criteria before changing architecture.

## References

- S1: [Original article, Japanese URL with English body](https://claude.com/ja/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop).
- S2: [Official single-agent-loop migration kit](https://github.com/anthropics/single-agent-loop-kit), mutable landing page checked; code not reviewed or run.

[Theme index](README.md) | [Survey index](../README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
