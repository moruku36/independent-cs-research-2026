**English** | [日本語](2026-10-21-openai-research-acceleration.ja.md)

# Research acceleration: The view inside OpenAI — reading record

## Overview

- **What it is**: An OpenAI company article (2026-09-06) reporting how heavily its own researchers use AI agents; this is a reading record, not a peer-reviewed paper.
- **What it says**: In mid-August 2026 median usage exceeded USD600/day and the 90th percentile USD7000/day at API prices, equal to about 3.1 agent-workdays per human workday after eight-hour normalization.
- **Caveat**: It is a company self-report; usage at API prices is not spend, and runtime is not productivity or quality, so causal claims are not supported.

## Bibliography and reading status

- Author / publisher: OpenAI.
- Primary article: [Research acceleration: The view inside OpenAI](https://openai.com/index/research-acceleration-view-inside-openai/).
- Published: 2026-09-06. Accessed and recorded: **2026-10-21 JST**.
- Source type: **OpenAI company research article / self-report, not a peer-reviewed paper**. Excluded from academic paper counts.
- Question: how should reported agent usage be interpreted when considering enterprise adoption?
- Status: primary article body and appendix checked. Additional **View methods** details were not verified; underlying data were not obtained. No reproduction, implementation, or adoption trial.

## Short source summary

OpenAI's self-report covers researchers, including infrastructure/project-support staff. In mid-August 2026, median usage exceeded USD600/day and the 90th percentile USD7000/day at API prices—not bills or allowances. Eight-hour normalization yielded 3.1 agent-workdays per human workday; runtime is not productivity or quality. Experiments correlated with adoption while compute rose; causality is unestablished. January–July success analysis excluded uncertain outcomes; over half of successful tasks estimated at 4–8 human-hours involved intervention. Agent-use coverage was incomplete.

## Enterprise considerations — original questions, not article findings

- **Cost:** should budgeting use API-price equivalents, actual spend, or staff allowances, and how would each be measured?
- **Concurrency:** what limits on simultaneous agents and queued work would fit cost and latency requirements?
- **Approval boundaries:** which actions require human approval, and when should an output count as accepted?
- **Measurement:** how should uncertain outcomes, human interventions, quality, and comparison conditions be recorded before drawing causal conclusions?

These are questions for a future review, not a tested deployment recommendation. A minimal proposed check is to define those four items for a fictional workflow and specify an acceptance criterion before any experiment. No paid experiment is proposed here.

## Author's reflection (2026-10-21)

Since around August–September, I have felt that AI runtime has been exceeding human working hours, so this scale of usage feels plausible to me. I am also interested in the token allowance a company might provide. The company's budget is unknown.

This records the author's impressions and interests, rather than an empirical result from the article. It does not attribute the change to a particular model.

## Limitations and next checks

The figures above remain the publisher's self-report. This record does not independently validate the measurements or generalize them to another employer. Before using them for a decision, check the additional methods, population and denominators, time windows, concurrent-session accounting, and handling of uncertain outcomes and interventions. Comparison conditions and any causal intervention remain to be specified.

Related reading records: [CLI coding-agent adoption](../coding-agents/2026-cli-coding-agents-adoption-impact.md) and [SlopCodeBench](../coding-agents/2026-slopcodebench.md). These are reading pointers; their results are not pooled with this article.

Draft assistance: MiMo V2.6 Pro. Source checks, bilingual editing, placement, and local insertion of the author's reflection: Codex. The reflection was not sent to MiMo. No article figures or full text are reproduced.

[Collection index](README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
