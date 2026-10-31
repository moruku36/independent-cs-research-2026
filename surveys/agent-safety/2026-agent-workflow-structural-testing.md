**English** | [日本語](2026-agent-workflow-structural-testing.ja.md)

# Testing Agentic Workflows with Structural Coverage Criteria

## Overview
- **What it is:** A preprint on structural testing of multi-agent workflows.
- **What it says:** Graph-derived obligations and generated scenarios expose gaps in agent, tool and delegation coverage.
- **Caveat:** Abstract and results table totals disagree; SDK-style demo-scale evaluation and mocked tools limit generalization.

## Source and scope
Nafiseh Kahani and Mojtaba Bagherzadeh, [arXiv:2605.26521v1](https://arxiv.org/html/2605.26521v1), 26 May 2026. Checked 2026-10-31 JST: primary HTML abstract, method, evaluation, limitations and conclusion (selected sections). Code and PDF not checked; reproduction not performed.

## Question and method
End-to-end task success can conceal untested routes and access boundaries. The authors construct a typed graph of reachable agents, allowed and restricted tool edges, and delegation edges. They derive obligations, use DSPy to generate natural-language test scenarios with bounded refinement, and inspect runtime traces. Restricted-tool tests actively probe a negative obligation; absence of an observed call alone is not proof of security.

## Results and unresolved discrepancy
The paper describes ten OpenAI Agents SDK-derived workflows, 49 reachable agents, 47 tools and 403 obligations. The abstract reports 54/75 allowed-tool and 36/48 delegation obligations witnessed, with 23/248 restricted-call violations elicited. However, the cross-benchmark table for those ten workflows totals **45/65** and **31/41** respectively, while also reporting 23/248 restricted-call violations. These figures are inconsistent on their face; the cause has not been resolved. The denominator is obligations, not a production incident rate. Failure to elicit a violation under a bounded test does not demonstrate that the restriction is secure.

## Practical interpretation
- Map the AI team's agents, permitted tools, forbidden paths and handoffs before deployment.
- Generate representative scenarios and record whether each required path was actually exercised.
- Test unauthorized tool requests explicitly and keep missing coverage visible in CI.
- Pair structural checks with output correctness, policy, real API integration, and human-review tests.
- These are proposals, not demonstrated improvements in the user's environment.

## Limits and next checks
Most workflows are demo/research scale; tool backends were mocked, refinement was bounded, and structural witnesses do not establish semantic correctness or production safety. Compare table, abstract and underlying artifacts with the authors before using the reported totals. Reproduction and adoption: not performed.

[AI agent safety index](README.md)
