**English** | [日本語](2026-goals-first-class-abstractions.ja.md)

# Goals as First-Class Abstractions in Human-AI Collaboration

## Overview

- Source/topic: Argues that goals should persist as shared information, beyond requested deliverables.
- Claim/conclusion: Proposes explicit goals linked to people, artifacts, workflows, and revision history.
- Caveat: Goals must remain revisable; this design argument is not a measured efficiency effect.

## Practical reading (seven lines)

- Argues that goals should persist as shared information, beyond requested deliverables.
- Reviews research, commercial tools, and meetings to identify implicit-goal problems.
- Proposes explicit goals linked to people, artifacts, workflows, and revision history.
- Application proposal: specify who should be able to decide what when the work is done.
- Record purpose, acceptance conditions, exclusions, and change reasons in issues and PRs.
- State the desired decision before meetings or everyday AI consultations.
- Goals must remain revisable; this design argument is not a measured efficiency effect.

Research statements derive from the sources below; applications are this survey's proposals, not validated effects.

## Bibliography and verification

Lev Tankelevitch, Sean Rintel. AutomationXP26 workshop at CHI 2026, 2026-04-14, 7 pages, as listed by Microsoft Research. Workshop position/design paper, not a CHI main-track experiment.

2026-10-26 JST: Publication metadata and PDF argument, six design requirements, and conclusion checked; cited studies not individually verified. Partial reading; no reproduction or independent experiment.

## Question, method, and evidence

Research/tool review and meeting examples motivate six requirements: articulation, first-class representation, alignment, provenance, outcome simulation, and situated workflow support. No new controlled productivity effect is established. [S1, S2]

## Limitations and critical interpretation

Survey interpretation: a goal object should aid judgment, not silently authorize actions. Keep desired outcomes separate from permitted means. AI-inferred goals need human correction paths, and revised goals should not erase the original acceptance history.

## Related-work comparison

[Workplace adoption](2026-genai-workplace-productivity-communication.md) — Conceptual comparison of outcome definitions, conditions, and inspectable evidence; not a head-to-head performance claim.

## Free-to-run check plan

Unexecuted: rewrite one fictional meeting request and one issue with goal, evidence, exclusions, owner, and revision history; manually compare proposed outputs against the intended decision. No API or production change required.

## Usage and next checks

Proposed only; not trialed or adopted. Before application, inspect the target environment, comparison conditions, and unchecked primary material.

## References

- S1: [Primary source](https://www.microsoft.com/en-us/research/publication/goals-as-first-class-abstractions-in-human-ai-collaboration/).
- S2: [Companion/full text](https://www.microsoft.com/en-us/research/wp-content/uploads/2026/04/2026-goals-as-first-class-abstractions-in-human-ai-collaboration-AutomationXP26_paper_0982.pdf).

[Theme index](README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
