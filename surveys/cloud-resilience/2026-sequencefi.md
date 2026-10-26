**English** | [日本語](2026-sequencefi.ja.md)

# SequenceFI: Non-intrusive Temporal Fault Injection for Microservice Systems

## Overview

- Source/topic: Controls when faults activate, beyond choosing a target service.
- Claim/conclusion: Four benchmark evaluations report precise triggering and efficient configuration search.
- Caveat: Protocol and After-guard limitations prevent a blanket production-resilience guarantee.

## Practical reading (seven lines)

- Controls when faults activate, beyond choosing a target service.
- A sidecar tracks message events and enables faults after temporal conditions hold.
- Four benchmark evaluations report precise triggering and efficient configuration search.
- Application proposal: test cases where a state update succeeds but its response is lost.
- Use the scenarios to check retries, idempotency, and compensation in payments or jobs.
- Add ordering and occurrence count to a fault-test matrix.
- Protocol and After-guard limitations prevent a blanket production-resilience guarantee.

Research statements derive from the sources below; applications are this survey's proposals, not validated effects.

## Bibliography and verification

Yuzhen Tan, Jian Wang, Bing Li, Shaolin Tan. arXiv:2607.20050v1, 2026-07-22. Preprint; acceptance unverified.

2026-10-26 JST: Implementation, evaluation, limitations, and conclusion checked; no code or PDF cross-check. Partial reading; no reproduction or independent experiment.

## Question, method, and evidence

Kubernetes sidecar prototype; HTTP/1.x and gRPC/HTTP2; trace-derived temporal guards. Evaluation uses four microservice benchmarks and nine timing scenarios. Trigger precision, search cost, and runtime overhead are distinct metrics. [S1]

## Limitations and critical interpretation

Survey interpretation: a correct injection is not evidence that recovery is correct. Define an independent business oracle for duplicate effects and consistency. Proxy placement, metadata propagation, and encrypted traffic need deployment-specific review.

## Related-work comparison

[AWS chaos infrastructure](2026-adaptive-ephemeral-chaos-infrastructure.md) — Conceptual comparison of outcome definitions, conditions, and inspectable evidence; not a head-to-head performance claim.

## Free-to-run check plan

Unexecuted: manually replay a local toy request with a completed write and missing response. Check retry count and final state. This tests the scenario, not the SequenceFI implementation; artifact reproduction requires locating and reviewing its code first.

## Usage and next checks

Proposed only; not trialed or adopted. Before application, inspect the target environment, comparison conditions, and unchecked primary material.

## References

- S1: [Primary source](https://arxiv.org/html/2607.20050v1).

[Theme index](README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
