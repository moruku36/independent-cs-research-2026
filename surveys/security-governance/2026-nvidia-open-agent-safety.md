**English** | [日本語](2026-nvidia-open-agent-safety.ja.md)

# NVIDIA Open Agent Safety Platform

- Source: [original article](https://nvidianews.nvidia.com/news/open-agent-safety-platform)
- Published: 2026-09-28
- Type: NVIDIA product press release; vendor claims.
- Scope: primary article checked on 2026-10-30 JST; linked studies, implementations and incident claims were not independently reproduced.

## What it says

NVIDIA describes OpenShell as an open-source runtime for policy enforcement and action tracing, and Sentry as a separate out-of-band watchdog reference design on BlueField-4 DPUs. It claims Sentry can quarantine boundary violations in milliseconds. These are complementary software and hardware layers, with different platform requirements.

## Practical application

Evaluate OpenShell in a disposable lab with explicit file and network policies and synthetic secrets. Check current CPU support and deployment requirements independently; Sentry's DPU requirement should not be assumed to apply to every OpenShell deployment.

## Limits and next check

This is guidance or an announcement, not an independent evaluation. Validate controls against the actual architecture and deployment; no tests or implementation were performed for this note.

[Security governance index](README.md)
