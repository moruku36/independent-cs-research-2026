**English** | [日本語](2026-agentic-evidence-black-box.ja.md)

# A Black Box for Agentic Processes

## Overview
- **What it is:** A working-paper architecture proposal for agentic audit evidence.
- **What it says:** Externally anchored hashes can make selected records verifiable for later investigation.
- **Caveat:** No empirical security or performance evaluation; hashes do not establish truth or complete capture.

## Source and reading scope
Arslan Brömme, [A Black Box for Agentic Processes: Blockchain-Anchored Evidence for AI Agent Communication, Human Oversight, and GRC Audits](https://arxiv.org/html/2609.04017v1), arXiv:2609.04017v1, 3 September 2026, draft v0.9.1.5. Position and architecture preprint. Checked 2026-10-31 JST: primary HTML abstract, architecture, ordering, governance, illustrative scenario and limitations; selected sections, not code or implementation. No reproduction.

## Question and proposal
How can an organization reconstruct agent messages, tool actions and human approvals if runtime logs can be altered? The proposed pipeline captures selected events, canonicalizes and hashes them, anchors commitments externally, issues verification evidence, and later checks retained artifacts. Sensitive contents stay in controlled off-chain storage. Merkle batching may reduce the number of anchored commitments. The author also identifies trusted timestamps, transparency logs and append-only logs as alternatives with different trust assumptions.

## Claims and limits
An independently verifiable commitment supports detecting changes to retained bytes and showing that the digest existed no later than its anchor time. It does not establish the event's exact time, truth, authenticity, capture completeness, causal order, authorization or compliance. Signed identities, protected capture, sequencing, policy controls and independent oversight require separate design. A compromised pipeline can omit or substitute events before anchoring. The cloud-remediation incident is illustrative, not an evaluated deployment; the paper reports no empirical security or performance results.

## Practical applications (proposals)
- Link high-risk cloud change requests, policy versions, human approvals, actual API parameters and post-change state.
- Separate audit storage and signing authority from agent runtime; define retention and access rules.
- Start with risk-based selection and evaluate append-only logs or trusted timestamps before choosing a ledger.
- Test missing events, substitution before capture, key compromise, ordering and recovery; measure cost and latency.
- These ideas are not proof of regulatory compliance or verified results in the user's environment.

## Next checks
Assess threat model, metadata leakage, evidence retention/deletion and applicable legal obligations with appropriate specialists. No implementation, independent verification or reproduction performed.

[Security governance index](README.md)
