**English** | [日本語](2026-agentic-overconfidence.ja.md)

# Agentic Uncertainty Reveals Agentic Overconfidence

## Overview

- Source/topic: Tests whether agents can predict success of work by the same underlying model.
- Claim/conclusion: Post-execution review remains overconfident; more information need not improve self-assessment.
- Caveat: Limited models and tasks do not establish that adversarial prompts guarantee correctness.

## Practical reading (seven lines)

- Tests whether agents can predict success of work by the same underlying model.
- Compares pre-, mid-, and post-execution assessments on 100 SWE-bench Pro tasks.
- Post-execution review remains overconfident; more information need not improve self-assessment.
- Bug-finding framing reduces overconfidence in the evaluated setup.
- Application proposal: ask reviewers for counterexamples, unchecked conditions, and failing inputs.
- Prefer test outputs, diffs, and logs to uncalibrated confidence percentages.
- Limited models and tasks do not establish that adversarial prompts guarantee correctness.

Research statements derive from the sources below; applications are this survey's proposals, not validated effects.

## Bibliography and verification

Jean Kaddour, Srijan Patel, Gbètondji Dovonon, Leo Richter, Pasquale Minervini, Matt J. Kusner. arXiv:2602.06948v1, 2026-02-06. Preprint; acceptance unverified.

2026-10-26 JST: Methods, main findings, calibration discussion, and limitations partially checked; code not run. Partial reading; no reproduction or independent experiment.

## Question, method, and evidence

Same base model for patch generation and assessment; compares calibration and discrimination across assessment regimes. Lower average confidence and better pass/fail discrimination are different outcomes; pairwise improvements are not uniformly significant. [S1, S2]

## Limitations and critical interpretation

Survey interpretation: an extra reviewer is useful only if it contributes independent evidence. Lower confidence alone can be a uniform shift. Validate routing thresholds against held-out task outcomes before using confidence for automatic acceptance.

## Related-work comparison

[Reward hacking](2025-reward-hacking-emergent-misalignment.md) — Conceptual comparison of outcome definitions, conditions, and inspectable evidence; not a head-to-head performance claim.

## Free-to-run check plan

Unexecuted: take ten known-correct/incorrect toy patches, compare ordinary and bug-finding review rubrics manually, and retain missed bugs. This checks review procedure, not model calibration; a live model run requires a separate inference budget.

## Usage and next checks

Proposed only; not trialed or adopted. Before application, inspect the target environment, comparison conditions, and unchecked primary material.

## References

- S1: [Primary source](https://arxiv.org/html/2602.06948v1).
- S2: [Companion/full text](https://arxiv.org/abs/2602.06948).

[Theme index](README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
