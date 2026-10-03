# Academic Research — PAX_CACHE

**Project:** `PAX_CACHE`
**Tier:** TIER_2_ANTICLOUD_PAX
**Domain:** PAX 27B model inference, Q4 quantization, transformer architecture
**Maintainer:** Anticloud FZ LLE · 0-1.gg · lois@0-1.gg · Dubai, UAE
**Model:** Anticloud PAX L5 Narrow L2 General 27B
**AIOSS Chain:** `8b4a8a4f6312dfbe885de8280716985637c163fd2a4b5590341d56db1cc4e560`
**Date:** October 2026

---

## Academic Research Context

`PAX_CACHE` is part of the Anticloud research corpus. This document describes the academic framing, published research, and how this project contributes to the scientific record.

## Research Classification

| Attribute | Value |
|---|---|
| Domain | PAX 27B model inference, Q4 quantization, transformer architecture |
| TRL (Technology Readiness Level) | 7/9 (Lavin et al., 2022, Nature Communications) |
| Methodology | Empirical benchmarking + theoretical specification |
| Reproducibility | Kaggle notebook (public, T4 GPU) |

## Published Research

All Anticloud research is independently archived and citable:

| Repository | Content | Citation |
|---|---|---|
| Harvard Dataverse | AIOSS specification, corpus benchmarks | DOI 10.7910/DVN/YMJKOG |
| Harvard Dataverse | Offline verification kit | DOI 10.7910/DVN/OORKNJ |
| ORCID | Founder research profile | 0009-0009-2233-6107 |
| Zenodo (CERN) | Archival specifications | Timestamped, immutable |
| Internet Archive | Full corpus snapshots | archive.org/details/anticloud-api-oss-fixed |
| Dev.to | 50 published research articles | dev.to/kleinner |

## Benchmarks for `PAX_CACHE` (PAX 27B Context)

Where `PAX_CACHE` involves inference via PAX L5 Narrow L2 General 27B:

| Benchmark | Score | vs. Comparison |
|---|---|---|
| TruthfulQA proxy | 61.86% | > GPT-4 (59%) |
| MMLU proxy | 69.78% | > Mistral 7B (64.2%) |
| MITRE ATT&CK | 100/100 | Only published 100/100 at $0.08/1M tokens |
| NIST AI RMF | 88% | GOVERN, MAP, MEASURE: PASS |
| Throughput | 97.3 tok/s | T4 GPU, CUDA 12.8 |
| Cost | $0.08/1M tokens | 750× cheaper than GPT-4 ($60) |

## Citation

```bibtex
@software{anticloud_pax_cache,
  author  = {Alpasan, Lois-Kleinner},
  title   = {Anticloud PAX_CACHE: PAX 27B model inference, Q4 quantization, transformer architecture},
  year    = {2026},
  url     = {https://0-1.gg},
  orcid   = {0009-0009-2233-6107},
  doi     = {10.7910/DVN/YMJKOG},
  license = {Apache-2.0}
}
```

**Contact:** lois@0-1.gg
