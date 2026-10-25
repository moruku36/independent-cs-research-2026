**English** | [日本語](2026-multi-cloud-security-architecture.ja.md)

# Multi-Cloud Security Architecture Design Across AWS, Azure, and GCP

## Overview

- **What it is**: A journal article proposing a cross-provider security architecture.
- **What it says**: Align identity, segmentation, data protection, monitoring, and policy controls.
- **Caveat**: The reported validation lacks reproducible quantitative evidence.

## Bibliography and verification

Bhuvan Bobba, *International Journal of Computer Engineering and Technology*, 17(5), 61–74, published 2026-09-24; DOI 10.34218/IJCET_17_05_005. Checked 2026-10-25 JST: publisher metadata and PDF §§1–9; cited works not individually verified. ResearchGate retrieval failed; publisher text was used instead. No implementation or reproduction. Individual peer-review history unverified. [M1–M3]

## Question, method, and evidence

How can shared security intent survive different cloud controls? The proposed layers combine identity federation, service-mesh segmentation, independently managed encryption, centralized SIEM/SOAR, and policy-as-code. Section 6 describes an IaaS testbed, configuration audits, and simulated attacks against siloed controls. It asserts fewer inconsistent resources and non-actionable alerts. [M2, §§5–6]

## Critical interpretation and validity

Evidence audit: the validation section supplies no before/after counts, detection-latency measurements, sample sizes, repeated trials, or uncertainty estimates. No deployable configuration or experiment repository was identified in the checked paper. Consequently, neither an improvement percentage nor statistical significance can be reconstructed. The abstract's strong validation language should not be read as an independently established effect size. [M2, abstract, §§6–7]

This survey's architectural assessment: the design is useful as a list of control objectives, while its implementation mappings require a fresh provider-documentation review. Do not turn a diagram's “same role” into an assumption of equivalent effective permissions.

| Proposed design-review question | Evidence needed before adoption |
|---|---|
| Identity semantics | Human/workload identity distinction, claim mapping, token audience, and denial tests |
| Policy equivalence | Effective permission outcomes, exceptions, and hierarchy |
| Control-plane failure | IdP, key custody, telemetry, and response failure scenarios |
| Segmentation coverage | Which traffic traverses the enforcement point and which bypasses it |
| Detection quality | Labeled events, dropped logs, false negatives, and end-to-end timestamps |

These are proposed audit requirements, not validated features of the reference architecture. Centralization could simplify review while also concentrating administrative power; evaluate recovery and blast radius explicitly. A service mesh alone should not be used as the acceptance criterion for all cloud access paths.

## Related-work comparison

Conceptual connections:

- [CAMM](2026-camm-practical-evaluation.md): use a maturity lens to assess whether key-management changes can be operated over time.
- [Cloud resilience and SRE](../cloud-resilience/README.md): ask how shared security dependencies affect recovery.
- [Neuro-formal verification](../coding-agents/2026-neuro-formal-verification.md): explore whether policy translations preserve a stated security property. This is a research idea, not an existing integration.

## Free-to-run check plan

Proposed, unexecuted: create fictional IAM and infrastructure fixtures for three providers and define a small common rule set, including expected denials. Review each translation offline; record exceptions and failing fixtures. Replay synthetic logs through a local normalizer to measure field loss.

This checks translation assumptions without provisioning cloud resources. It does not reproduce live federation, network enforcement, latency, or the paper's attack validation. A later live test must specify scope and cost separately.

## Usage and unresolved checks

**Proposed only; not trialed or adopted.** Request raw results and deployment artifacts; verify provider integration details against current official documentation; define a reproducible baseline before quoting efficacy.

## References

- M1: [Publisher record](https://iaeme.com/Home/article_id/IJCET_17_05_005).
- M2: [Publisher full-text PDF](https://iaeme.com/MasterAdmin/Journal_uploads/IJCET/VOLUME_17_ISSUE_5/IJCET_17_05_005.pdf), printed pp. 61–74.
- M3: [User-provided ResearchGate entry](https://www.researchgate.net/publication/414727265_MULTI-CLOUD_SECURITY_ARCHITECTURE_DESIGN_ACROSS_AWS_AZURE_AND_GCP), discovery link only; not retrieved.
- [DOI](https://doi.org/10.34218/IJCET_17_05_005).

[Theme index](README.md) | [Survey index](../README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
