**English** | [日本語](2026-ai-generated-terraform-guardrails.ja.md)

# AI-Generated Terraform in 2026: Benchmarks, Failure Modes, Guardrails

## Overview

- Source: Ajay Kumar, 2026-10-20, technical article
- Finding: Validation alone does not prove intent alignment or security.
- Caveat: The cited benchmark figures were not independently verified in this reading.

[Source](https://www.ajayk.sh/blog/llms-writing-infrastructure-code-safely-2026/) · Checked October 29, 2026; key sections read, not reproduced.

## Practical reading

1. The article reviews security risks in AI-generated Terraform and other IaC.
2. Valid syntax can coexist with excessive permissions, omitted encryption or obsolete settings.
3. Validation alone does not prove intent alignment or security.
4. It recommends combining plans, policy checks and human review.
5. Define access, exposure and encryption acceptance criteria and test in an isolated environment.
6. The cited benchmark figures were not independently verified in this reading.

## Proposed check

Define a small pilot, acceptance criteria, and safety constraints; record outcomes and human review effort. This is a proposal, not an implemented result.

[Theme index](README.md)
