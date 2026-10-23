**English** | [日本語](2026-camm-practical-evaluation.ja.md)

# CAMM: Practical Evaluation of the Crypto-Agility Maturity Model

## Overview

- **What it is**: An arXiv paper (FPS 2025) that evaluates the Crypto-Agility Maturity Model (CAMM), a model for judging how ready an organization is to migrate cryptography.
- **What it says**: It checks CAMM against maturity-model design principles and applies it to an internal HTTPS service, pointing out problems with scope, audience, measurable criteria and dependencies.
- **Caveat**: Only four researchers and one simplified scenario were used, and no improved CAMM is presented, so it does not show anything about real post-quantum migration.

- **Status**: primary PDF text checked (§1–6, Tables 1–3) / not reproduced.
- **Title, authors, year, venue, ID, primary URL**: *Practical Evaluation of the Crypto-Agility Maturity Model* / Leonie Wolf, Samson Umezulike, Gurur Öndarö, Sebastian Schinzel, Fabian Ising / 2026 / arXiv lists the venue as FPS 2025 / [arXiv:2604.12428v1](https://arxiv.org/abs/2604.12428v1) / [PDF](https://arxiv.org/pdf/2604.12428v1) / [DOI](https://doi.org/10.48550/arXiv.2604.12428).
- **Date checked and version**: 2026-10-15 UTC / v1, submitted 2026-04-14. The original CAMM paper and website cited by this one were not read separately.
- **Research question**: conformance of CAMM to design principles, practical applicability, and improvements (RQ1–3).
- **Method, data, comparison conditions**: analysis against maturity-model design principles, plus an application to an internal HTTPS service isolated from the internet. The designated browser and OS were assumed to be updated regularly. Four researchers classified requirements independently and reached agreement in discussion (§3–4).
- **Claims and evidence**: points out problems with scope and audience, measurable acceptance criteria, and dependencies (Tables 1 and 3). **A ✓ in Table 2 means an organization can satisfy a requirement by its own judgment**, not proof of implementation or migration success. Pi is the proportion of initial judgments matching the final consensus, a reference value only. It proposes clarifying scope, verifiable criteria, organizing dependencies, and audience-specific guidance (§5).
- **Limitations and threats to validity**: four people and one simplified scenario limit generalization. No improved CAMM is presented (§1). Do not treat this paper as demonstrating PQC performance, security, or the maturity of real systems.
- **Comparison with related work**: it evaluates the original CAMM paper and is not an alternative implementation of CAMM. It differs in both target and judging method from the lab's [own scoring](https://github.com/moruku36/pqc-crypto-inventory-lab/blob/main/docs/scoring.md). As with the other [AI paper records](README.md), it stresses the distinction between what is declared, observed, and verified.

## Free-to-run reproduction plan (this repository's proposal, not done)

A strict replication needs the versions of the original CAMM paper and web requirements the paper evaluated. If the current website is used as is, say it is an evaluation of a later version, not a replication of the v1 paper.

Start with only the lab's public synthetic samples and fix the files under evaluation, excluded scope, rationale, and responsibility boundaries. On an evaluation sheet, record requirement ID / criterion / applicability and reason / evidence / assessor / date / decision in separate columns. Do not confuse missing information with out of scope. Have two or more people save independent judgments before reconciling, and record the number of disagreements and interpretation changes. This small exercise does not replicate the original four-person evaluation or establish statistical validity.

- **Usage status**: proposed. Only a document addition tied to the [PQC-side improvement plan](https://github.com/moruku36/pqc-crypto-inventory-lab/blob/main/docs/camm-practical-evaluation.ja.md). No CAMM scoring, new schema, new feature, or experiment is implemented.
- **Unconfirmed points and next checks**: confirm the availability of the CAMM requirement version used in the original evaluation and of the individual judgment data, and set the exercise's prior criteria. No agreement rate or improvement effect is reported until measurement is done.

[Collection index](README.md) | [Full reading list](../../docs/reading-list.md)
