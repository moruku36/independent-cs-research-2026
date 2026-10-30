**English** | [日本語](2026-qers-pqc-iot.ja.md)

# QERS: post-quantum communication on IoT devices

## Overview

- An experimental preprint evaluates MQTT, HTTP and HTTPS under PQC workloads on ESP32-C6 and Raspberry Pi CM4.
- Weighted Basic, Tuned and Fusion scores combine performance and security-related measures.
- Results depend on the setup and weights, and the paper contains inconsistent result statements.

## Sources and scope

Jonatan Rassekhnia, 19 January 2026. The requested [ResearchGate record](https://www.researchgate.net/publication/399931145_Quantum_Encryption_Resilience_Score_QERS_for_MQTT_HTTP_and_HTTPS_under_Post-Quantum_Cryptography_in_Computer_IoT_and_IIoT_Systems) was access-limited. Its DOI identifies [arXiv:2601.13423v1](https://arxiv.org/html/2601.13423v1); abstract, method and results were partially checked. The HTML title differs from the ResearchGate record. Data, implementation, peer-review status and experiments were not independently verified.

## Findings and limits

Table III reports higher Basic/Tuned scores for MQTT and a higher security-weighted Fusion score for HTTPS. Composite rankings depend on selected weights and do not prove security. MQTT may itself run over TLS; avoid generalizing this comparison to a protocol-wide security ranking.

Section IV-B says HTTPS has reduced Fusion scores, whereas IV-A and Table III place it highest. Section V claims distance reduced Fusion scores for every protocol, but Table III shows MQTT unchanged and HTTP/HTTPS slightly higher. These discrepancies remain unresolved; inspect raw measurements and implementation. PQC and certificate configuration require independent verification.

## Practical use

In a PQC migration proof of concept, measure handshake time, latency, CPU, memory and power against a classical baseline on the intended hardware. Align cryptography, authentication and connection reuse, and retain raw measurements alongside composite scores.

[Security governance index](README.md)
