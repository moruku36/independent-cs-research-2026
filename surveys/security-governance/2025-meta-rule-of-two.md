**English** | [日本語](2025-meta-rule-of-two.ja.md)

# Agents Rule of Two

- Source: [original article](https://ai.meta.com/blog/practical-ai-agent-security/)
- Published: 2025-10-31
- Type: Meta engineering guidance.
- Scope: primary article checked on 2026-10-30 JST; linked studies, implementations and incident claims were not independently reproduced.

## What it says

Meta proposes allowing at most two capabilities per session: processing untrusted inputs, accessing sensitive systems or private data, and changing state or communicating externally. When all three are required, it calls for supervision or reliable validation. The framework is inspired by the lethal trifecta and extends outbound communication to state changes.

## Practical application

Run external browsing without production credentials; separate state-changing tools and verify consequential actions. Review full action content, not just a generic approval prompt. This does not address misinformation or replace least privilege.

## Limits and next check

This is guidance or an announcement, not an independent evaluation. Validate controls against the actual architecture and deployment; no tests or implementation were performed for this note.

[Security governance index](README.md)
