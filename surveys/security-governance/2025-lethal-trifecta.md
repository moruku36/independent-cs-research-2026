**English** | [日本語](2025-lethal-trifecta.ja.md)

# The lethal trifecta

- Source: [original article](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/)
- Published: 2025-06-16
- Type: A personal technical analysis of prompt injection and data exfiltration.
- Scope: primary article checked on 2026-10-30 JST; linked studies, implementations and incident claims were not independently reproduced.

## What it says

Private data access, untrusted input and outbound communication together create an exfiltration path. An attacker can hide instructions in an email, issue, web page or document. A model may treat those instructions as a task and send secrets through a tool. The author argues that prompt-only guards cannot reliably close this path. MCP tools can combine these capabilities across integrations.

## Practical application

Map each agent's data sources, credentials and outbound tools. Separate public research from private repositories; restrict egress and review messages before sending. Test with synthetic secrets and adversarial content.

## Limits and next check

This is guidance or an announcement, not an independent evaluation. Validate controls against the actual architecture and deployment; no tests or implementation were performed for this note.

[Security governance index](README.md)
