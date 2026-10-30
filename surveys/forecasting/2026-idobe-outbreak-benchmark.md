**English** | [日本語](2026-idobe-outbreak-benchmark.ja.md)

# IDOBE: Infectious Disease Outbreak forecasting Benchmark Ecosystem

## Overview

- A benchmark of outbreak time series and models across diseases and locations.
- It evaluates 11 baselines on 10,799 outbreaks from 13 diseases and 248 locations at one-to-four-week horizons.
- Preprint findings do not guarantee performance on new outbreaks.

## Source and verification

[arXiv:2604.18521v2](https://arxiv.org/html/2604.18521v2), 29 April 2026. The requested URL did not pin a version; v2 was current when checked. Abstract, dataset, methods and key results were partially read. No independent reproduction of data, code or results. [Authors' repository](https://github.com/NSSAC/IDOBE).

## Findings

The authors compare statistical, MLP and other models, assessing point errors and predictive intervals with NWIS. They report robust overall MLP performance and a slight statistical advantage before the peak. Performance differs by disease, location, outbreak stage and forecast horizon.

## Application and limitations

For operational time-series work, the study suggests evaluating uncertainty and performance by horizon, limited-data conditions and regime change, rather than only average error. Applying that evaluation idea to IT incidents or demand is an inference, not a result established by the paper.

[Forecasting index](README.md)
