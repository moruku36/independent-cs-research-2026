[日本語](2026-adaptive-ephemeral-chaos-infrastructure.ja.md) | **English**

# Adaptive Ephemeral Chaos Infrastructure — survey note

## Reader summary

The paper designs a seven-phase workflow for fault injection across AWS accounts: request validation, safety checks, baseline capture, AWS FIS injection, telemetry collection, recovery verification and reporting. Its recovery design uses a 15-minute prior baseline, requires monitored values to remain within two standard deviations for three consecutive minutes, and marks an experiment UNRESOLVED with SNS notification if convergence has not occurred within 15 minutes; the next experiment is then blocked.

These are design parameters in the paper, not universal safety guarantees. Section 8 describes future evaluation, not measured performance or demonstrated real-world effects. Multiple AWS accounts are not multiple cloud providers.

## Survey record

- **Status:** All eight pages of the publisher PDF checked by a separate research contributor on October 23, 2026. Code, reproducibility and experiments have not been independently checked or reproduced.
- **Bibliography:** Tripatjeet Singh, *Adaptive Ephemeral Chaos Infrastructure for Resilience Validation in AWS Multi-Account Environments*, *International Journal of Emerging Trends in Computer Science and Information Technology* 7(1), 338–345, 2026; published March 19, 2026; [DOI:10.63282/3050-9246.IJETCSIT-V7I1P148](https://doi.org/10.63282/3050-9246.IJETCSIT-V7I1P148). [Publisher article](https://ijetcsit.org/index.php/ijetcsit/article/view/654); [publisher PDF viewer](https://ijetcsit.org/index.php/ijetcsit/article/view/654/593).
- **Checked:** October 23, 2026; linked eight-page PDF.
- **Question:** How should cross-account AWS fault injection control safety, experiment collisions and false declarations of recovery?
- **Method:** Seven phases: validate request, check safety conditions, capture baseline, inject a fault through AWS FIS, collect telemetry, verify recovery, and report. The design includes CI/CD collision detection and cross-account coordination. Application Dependency Graph mapping and centrality-based experiment selection are explicitly not implemented. Section 8 proposes future evaluation.
- **Reported design:** A 15-minute prior baseline; monitored values within two standard deviations for three continuous minutes; after 15 minutes without convergence, mark UNRESOLVED, notify through SNS and block the next experiment. See the [publisher PDF](https://ijetcsit.org/index.php/ijetcsit/article/view/654/593). The paper's description of four implemented capabilities is distinguished here from independently verified implementation or measurement.
- **Limits:** No measured result or real-environment effect is supplied by the future-evaluation section. Code and reproducibility remain unverified. The thresholds are not general safety guarantees. This is not a demonstration of a multi-cloud or autonomous LLM SRE agent.
- **Comparison:** Coordination, recovery checks and collision control are useful dimensions; superiority over other tools is not supported by verified measurements.
- **Free initial check:** Simulate transitions, interruption and recovery decisions with mock event sequences. Not done and not a cloud experiment.
- **Use status:** Proposal only. No implementation evidence in the SRE repository.
- **Open checks:** Author code, reproducible configuration, logs and independent comparison.

A possible extension is to separate “fault injection ended” from “service recovered” and continuously check user-facing SLIs, dependencies, configuration differences and residual resources. This is our proposal, not a validated multi-cloud feature of the paper.

[Category index](README.md) | [Reading list](../../docs/reading-list.md)
