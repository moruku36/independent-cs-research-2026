**English** | [日本語](2026-tfdrift-severity-taxonomy.ja.md)

# tfdrift: severity classification for infrastructure drift

## Overview

- **What it is**: Demo paper; text states IC2E 2026 acceptance, not independently verified. tfdrift prioritizes Terraform drift rather than notifying every change equally.
- **What it says**: Interpretable rules are promising but require careful missed-event review.
- **Caveat**: Only eight security events and AWS-focused testing limit generalization to Azure or GCP.

## Source and reading status

- Author/provider: Sudarshan Bhagvanthakur
- Date/version: arXiv:2608.18173v1（HTMLヘッダ2026-08-17）
- [Requested primary source](https://arxiv.org/html/2608.18173v1)
- Checked: October 28, 2026, Japan time.
- Scope: Primary HTML body and Table I checked; code not run. Search index date August 20 differs from HTML header August 17.
- Usage: proposed only; no adoption, reproduction or effectiveness measurement.

## Practical reading (seven lines)

1. tfdrift prioritizes Terraform drift rather than notifying every change equally.
2. Resource and attribute patterns map changes to four severity tiers.
3. An AWS sandbox evaluation reports reducing 62 alerts to 17.
4. The claimed 94% security coverage conflicts with 7/8 detected, which equals 87.5%.
5. Interpretable rules are promising but require careful missed-event review.
6. Proposed use: retain all events and compare severity decisions with human labels before suppressing alerts.
7. Only eight security events and AWS-focused testing limit generalization to Azure or GCP.

## Approach and evidence

The sandbox includes 150+ workspaces, 847 resources and 62 injected events. Filtering plus ignore rules leaves 12 alerts. One Lambda runtime change was missed; reduction and security recall are different metrics.

The following is this note's proposed application, not a result established by the source.

## Free-to-start check plan

Unperformed pilot: inject authorized IAM, exposure, encryption, tag and scaling changes in an isolated lab; retain all events and measure recall, false alerts and scan failures without auto-remediation.

## Related work and comparison

Read alongside the [related note](2026-sequencefi.md). Vendor reports, commentary and papers provide different kinds of evidence and should not be pooled as independent confirmation.

## Unconfirmed points and next checks

Primary HTML body and Table I checked; code not run. Search index date August 20 differs from HTML header August 17. Before adoption, assess local data, permissions and workflow, and check for source updates.

[Theme index](README.md) | [Reading list](../../docs/reading-list.md)
