**English** | [日本語](2026-mercari-ai-security-governance.ja.md)

# Mercari's enterprise agent security and governance

## Overview

- **What it is**: Conference presentation. The presentation covers security and governance for company-wide agent use.
- **What it says**: OAuth and granular MCP authorization remain issues after gateway adoption.
- **Caveat**: This is a partial transcript reading, not verified implementation guidance.

## Source and reading status

- Author/provider: Hiroki Akamatsu / 赤松宏紀 (hi120ki)
- Date/version: 2026-10-27（掲載日 / upload date）
- [Requested primary source](https://speakerdeck.com/hi120ki/mercari-ai-security-conference-2026)
- Checked: October 28, 2026, Japan time.
- Scope: Public transcript partially checked; many pages expose headings only. Diagrams, configuration details and talk audio not checked.
- Usage: proposed only; no adoption, reproduction or effectiveness measurement.

## Practical reading (seven lines)

1. The presentation covers security and governance for company-wide agent use.
2. Visible headings identify technical requirements, identity and autonomy as standards topics.
3. It emphasizes enforceable guardrails beyond written rules.
4. Topics include Claude Enterprise, centralized MCP control and Shadow AI visibility.
5. OAuth and granular MCP authorization remain issues after gateway adoption.
6. Proposed use: inventory approved AI services, connectors, tenants, permissions and logs.
7. This is a partial transcript reading, not verified implementation guidance.

## Approach and evidence

Use the visible topics as an assessment outline, separating authentication from per-action authorization; unseen implementation details remain unverified.

The following is this note's proposed application, not a result established by the source.

## Free-to-start check plan

Unperformed pilot: map one integration's human, agent and service identities, allowed actions, logs and revocation, then inspect its configuration.

## Related work and comparison

Read alongside the [related note](2026-claude-duet-safety-privacy-security.md). Vendor reports, commentary and papers provide different kinds of evidence and should not be pooled as independent confirmation.

## Unconfirmed points and next checks

Public transcript partially checked; many pages expose headings only. Diagrams, configuration details and talk audio not checked. Before adoption, assess local data, permissions and workflow, and check for source updates.

[Theme index](README.md) | [Reading list](../../docs/reading-list.md)
