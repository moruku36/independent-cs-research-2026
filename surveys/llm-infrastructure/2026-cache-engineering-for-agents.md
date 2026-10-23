[日本語](2026-cache-engineering-for-agents.ja.md) | **English**

# Cache Engineering for Agents — Survey note

## Overview

- **What it is**: Cache Engineering for Agents (arXiv 2610.28577), a paper on controlling an agent's active KV cache directly without rewriting its text history.
- **What it says**: A rolling-drop policy beat threshold-triggered summarization by 1.7 points on average at 27.7% lower calculated cost, and a serving test showed 1.18x output throughput and 1.51x faster P95 latency.
- **Caveat**: Results depend on model, hardware and task mix, dropped content may still leave effects in retained KV, and the code was not checked.

## Reader summary

The paper studies direct control of an agent's active KV cache without editing its text trajectory. The authors report a 1.7-point mean benchmark score gain and 27.7% lower calculated cost for a rolling-drop policy versus threshold-triggered summarization across three models and four benchmarks. A separate serving experiment reports 1.18× output throughput and a 1.51× speedup in P95 request latency. These are reported results in specified settings, not a general API billing guarantee.

## Survey record

- **Status:** Primary source checked; main sections and appendix partially read. Code review and reproduction not performed.
- **Bibliography:** Tianyu Fu, Ruoxi Wang, Zihan Min, Zhongqi Ren, Zhihao Li, Tengxuan Liu, Shengxu Mu, Hanling Zhang, Yu Wang, *Cache Engineering for Agents*, October 20, 2026, [arXiv:2610.28577v1](https://arxiv.org/html/2610.28577v1), preprint. [Author-provided code](https://github.com/thu-nics/AKV) has not been checked.
- **Checked:** October 23, 2026; v1.
- **Question:** Can long agent trajectories avoid the KV recomputation caused by trimming or summarizing history?
- **Method and comparison:** `drop` excludes chosen KV entries from future attention and `repos` adjusts positional encodings without rewriting the text trajectory. AKV tracks operation history so equal token prefixes with different cache histories are not treated as equivalent. A rolling-drop policy retaining the most recent 12 tool responses is compared with threshold summarization across three models and four benchmarks. Serving evaluation uses SGLang and eight A800 80GB GPUs, including replay of 80 long-task trajectories.
- **Reported evidence:** Mean score +1.7 points and calculated cost −27.7%; at each method's maximum throughput configuration, 1.18× output throughput and 1.51× P95 latency speedup. See [§3–5, Tables 1–2, Appendix A.1](https://arxiv.org/html/2610.28577v1).
- **Limits:** Results depend on model, hardware, concurrency and task mix. Dropping KV need not preserve full-context output or improve every task. Retained KV may still carry effects of dropped content, so this is not a confidential-data erasure method.
- **Comparison:** Text summarization or trimming, low-level KV compression, and harness-controlled KV operations address different layers. Provider prompt caching is distinct from AKV.
- **Free initial check:** Analyze public trajectories and test cache-state identity with a small simulated state machine. This would not reproduce GPU performance. Not done.
- **Use status:** Proposal only. No implementation evidence.
- **Open checks:** Code, serving API, independent cost accounting, portability to other backends.

For this repository, a future evaluation could compare full history, summarization and rolling-drop under the same tasks, budget and stopping conditions, measuring quality, real cost or GPU time, KV memory and P95 latency. First confirm backend capability; an API-compatible interface does not imply that every provider supports KV operations.

[Category index](README.md) | [Reading list](../../docs/reading-list.md)
