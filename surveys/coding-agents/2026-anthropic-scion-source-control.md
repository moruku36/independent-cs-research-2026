**English** | [日本語](2026-anthropic-scion-source-control.ja.md)

# Redesigning source control at Anthropic

## Overview

- Source: Anthropic describes Scion, an internal version-control system for agent-heavy monorepo workflows.
- Finding: Scion relies on always-online clients, server-side operations, and sparse/on-demand checkouts.
- Caveat: This internal case has unusual scale and does not establish that every team should replace Git.

## Practical reading (seven lines)

- Anthropic describes Scion, an internal version-control system for agent-heavy monorepo workflows.
- The company reports daily merges growing from about 2,500 to over 30,000.
- Scion relies on always-online clients, server-side operations, and sparse/on-demand checkouts.
- For practice, first measure CI checkout time, repository traffic, and merge queues.
- Prefer targeted caching and sparse checkout experiments where they address measured bottlenecks.
- Keep source-control availability and recovery in the design when centralizing operations.
- This internal case has unusual scale and does not establish that every team should replace Git.

## Bibliography and verification

Anthropic Engineering, 2026-10-13, updated 2026-10-15. First-party engineering article; not a peer-reviewed paper. Main article partially reviewed; no independent verification. 2026-10-27 JST. [Source](https://www.anthropic.com/research/redesigning-source-control)

## Method, evidence, and limitations

The author reports 25 million CI checkouts per day and an in-house migration in five months. These are vendor-reported case figures; results, cost, and implementation have not been independently reproduced.

Practical suggestions here are hypotheses, not demonstrated effects in another environment. Separate causes, outcomes and unknowns, and retain before/after conditions and failures.

## Related work

[2026-fold-subagents-main-loop](2026-fold-subagents-main-loop.md) — A related note for comparing operational concerns.

## Free-to-run check plan and usage

Proposed, unexecuted: record steps, elapsed time and failures in a small synthetic workflow and compare with the baseline. No production deployment or reproduction.

[Theme index](README.md) | [Reading list](../../docs/reading-list.md)
