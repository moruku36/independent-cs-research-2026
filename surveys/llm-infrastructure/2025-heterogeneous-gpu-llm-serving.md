**English** | [日本語](2025-heterogeneous-gpu-llm-serving.ja.md)

# Demystifying Cost-Efficiency in LLM Serving over Heterogeneous GPUs

## Overview

- **What it is**: An arXiv paper on cost-efficient LLM serving over a mix of GPU types, with a scheduler that decides what to rent and how to dispatch requests.
- **What it says**: It benchmarks six GPU types, then uses a mixed-integer linear program to choose GPUs, replica deployment and dispatch under a budget, reporting up to 41% higher throughput or 54% lower latency than baselines at equal price.
- **Caveat**: Only the first part of the paper was read (through part of section 4.2), and results depend on cloud prices at measurement time.

## Key points for people and PMOs

- **What we learned**: serving LLMs on a mix of GPU types can be more cost-efficient than serving on one type, because different workloads stress different resources. The authors benchmark six GPU types and then build a scheduler (mixed-integer linear programming, MILP) that decides which GPUs to rent, how to deploy model replicas, and how to dispatch requests under a price budget and live GPU availability. Reported: up to 41% (average 20%) higher throughput, or up to 54% (average 20%) lower latency, at the same price budget versus baselines.
- **What it's useful for**: a framework for thinking about GPU choice by workload shape (compute-heavy prompts vs. memory-heavy long outputs), and a model of the decision as an optimization problem rather than "buy the biggest GPU".
- **Caution**: only the first part of the paper was read (abstract through part of §4.2). The benchmark is limited to six GPU types, two Llama3 models, and nine workload types, and depends on cloud prices and availability at measurement time. The authors' own conclusion and limitations were not seen.
- **Next step**: none done. No reproduction, no code check, no price re-check.

## Survey record

- **Status**: **partially read**. Primary HTML checked through a summarizing fetch tool; the extraction stopped partway through §4.2, so the remainder of the method, the full evaluation, the discussion, the conclusion, and the appendices (profiling, discussion) were **not** seen. PDF not cross-checked, cited works not read, not reproduced. Numbers below are as reported by that extraction and should be re-checked against the PDF.
- **Title, authors, year, venue, DOI / arXiv ID, primary URL**: *Demystifying Cost-Efficiency in LLM Serving over Heterogeneous GPUs* / Youhe Jiang, Fangcheng Fu, Xiaozhe Yao, Guoliang He, Xupeng Miao, Ana Klimovic, Bin Cui, Binhang Yuan, Eiko Yoneki / year inferred from the arXiv ID as 2025 (v2; the submission and revision dates were not shown) / the keywords list "Machine Learning, ICML", but **acceptance and venue are unconfirmed**. [arXiv:2502.00722v2](https://arxiv.org/abs/2502.00722v2), [HTML](https://arxiv.org/html/2502.00722v2).
- **Date checked and version examined**: 2026-10-22 / v2.
- **Research questions** (as stated in the paper):
  1. Can serving LLMs over heterogeneous GPU resources achieve better cost-efficiency than homogeneous GPU resources?
  2. If so, how can that cost-efficiency be enhanced?
- **Method, data, and comparison conditions** (portion read):
  - **Benchmark**: six GPU types (A6000, A40, L40, A100, H100, 4090), two models (Llama3-8B, Llama3-70B), and nine workload types drawn from ShareGPT, WildGPT, and Azure-Trace, grouped as compute-intensive (long input, short output) or memory-intensive (short input, long output). From this the authors identify three levers for cost-efficiency: GPU composition, deployment configuration, and workload assignment.
  - **Problem formulation**: choose a GPU composition under a price budget and availability limits, organize GPUs into serving groups with parallelism strategies, and assign workloads to replicas, minimizing overall makespan for all incoming workloads.
  - **Scheduler**: MILP, accelerated by heuristics and binary search, with an extension to multi-model serving. A one-time profiling step is described in an appendix (not seen). Baselines are homogeneous and heterogeneous alternatives; their exact definitions were not seen.
- **Claims and evidence** (as reported):
  - Data-center GPUs (H100, A100) handle compute-intensive workloads well with Llama3-70B.
  - Workstation GPUs (A40, A6000, L40) suit memory-intensive workloads, with on average 1.2x memory bandwidth and 1.8x memory capacity per unit price versus data-center GPUs.
  - Consumer 4090 GPUs perform well on Llama3-8B, with about 1.9x memory bandwidth per unit price versus A100/H100.
  - Picking the right GPU type improves cost-efficiency by up to 2.27x; the best deployment configuration improves system performance by up to 2.61x.
  - End to end, at the same price budget: up to 41% (average 20%) higher throughput, or up to 54% (average 20%) lower latency, versus baselines, across diverse workload traces, varying GPU availability, and multi-model serving.
- **Limitations and threats to validity**: the authors' limitations were **not seen**. Our observations, not statements from the paper: the evaluation covers six GPU types, two model sizes, and nine workload types; results depend on cloud GPU prices and availability at measurement time; "per unit price" comparisons shift whenever prices change; MILP scheduling cost at larger scale was not seen.
- **Comparison with related work**: not checked (related-work section not seen). Do not read the numbers above as a ranking against other serving systems.
- **Free-to-run reproduction plan**: the benchmark needs rented GPUs and cannot be reproduced for free. A free substitute is to write the optimization problem as a toy MILP (for example with an open-source solver) using **fictional** prices, throughputs, and availability, and see how the chosen GPU mix changes when you change the budget or the workload mix. This tests the formulation idea only, not the paper's numbers. Untested.
- **Usage status**: proposed (idea below); not trialed.
- **Unconfirmed points and next checks**: publication date and venue; the full §4–§6 and appendices (profiling, discussion); the authors' conclusion and limitations; baseline definitions; whether code is public; PDF cross-check of all numbers.

## Idea worth trying (not demonstrated by the paper)

When sizing GPU capacity for an internal LLM service, separate the workload into prompt-heavy and output-heavy traffic first, and compare "performance per unit price" for each GPU class instead of picking one class for everything. Check current prices and availability before relying on any ratio above.

## Summary

The paper asks whether LLM serving over heterogeneous cloud GPUs is more cost-efficient than over homogeneous GPUs, and how to improve it further. It benchmarks six GPU types, two Llama3 models, and nine workloads, finds that GPU type and deployment configuration each shift cost-efficiency by up to 2.27x and 2.61x, and proposes a MILP scheduler that chooses GPU composition, deployment, and workload assignment under a price budget. Reported gains at equal budget: up to 41% (average 20%) throughput or up to 54% (average 20%) latency. Only part of the paper was read, the authors' conclusion and limitations were not seen, venue is unconfirmed, and nothing was reproduced.

[Collection index](README.md) | [Reading list](../../docs/reading-list.md)
