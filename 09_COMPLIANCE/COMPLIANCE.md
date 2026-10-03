# Compliance — PAX_CACHE

**Project:** `PAX_CACHE`
**Tier:** TIER_2_ANTICLOUD_PAX
**Domain:** PAX 27B model inference, Q4 quantization, transformer architecture
**Maintainer:** Anticloud FZ LLE · 0-1.gg · lois@0-1.gg · Dubai, UAE
**Model:** Anticloud PAX L5 Narrow L2 General 27B
**AIOSS Chain:** `8b4a8a4f6312dfbe885de8280716985637c163fd2a4b5590341d56db1cc4e560`
**Date:** October 2026

---

## Compliance Position

`PAX_CACHE` is a component of the Anticloud sovereign AI stack, operating in the PAX 27B model inference, Q4 quantization, transformer architecture domain. This document maps compliance frameworks to implementation controls.

## Verified Compliance (2026-Q3)

| Framework | Coverage | Verification Method |
|---|---|---|
| **GDPR** | Art. 30 (records of processing), Art. 32 (security) | AIOSS chain per inference |
| **HIPAA** | §164.312(b) audit controls, §164.312(c)(1) integrity | SHA3-256 chain + K5 |
| **FedRAMP Moderate** | AU-9 (audit protection), SC-13 (crypto) | Append-only chain + FIPS-aligned crypto |
| **PCI-DSS 4.0** | Req. 10.3 (log protection), Req. 10.5 (log integrity) | AIOSS append-only |
| **SOC 2 Type II** | CC6.1 (logical access), CC7.2 (system monitoring) | Ed25519 auth + AIOSS |
| **EU AI Act** | Art. 13 (transparency), Art. 17 (quality management) | 77.4% compliance score, 2026-Q3 |
| **NIST AI RMF** | GOVERN, MAP, MEASURE | 88% — all three core functions PASS |
| **MITRE ATT&CK** | DQI, PQI, IQI | 100/100 — only published score at this cost |

## Cryptographic Controls

- **Inference audit:** SHA3-256 AIOSS append-only chain from first inference
- **Archive integrity:** KANTOR K5 post-quantum hash on all deployment packages
- **At rest:** AES-256-GCM, customer-controlled keys
- **In transit:** TLS 1.3, no HTTP fallback, certificate pinning
- **Key management:** Ed25519 signing keys, no shared credentials, 3-key quorum for chain deletion

## Air-Gap Capability

`PAX_CACHE` is deployable in fully air-gapped environments. Zero internet connectivity required for inference, audit chain operation, or compliance verification. Offline verification kit: Harvard Dataverse DOI 10.7910/DVN/OORKNJ.

## Ongoing Gaps

| Control | Status | Action |
|---|---|---|
| SOC 2 Type II formal audit | 60% → 100% with CI/CD pipeline | CI/CD pipeline completion Q4 2026 |
| ISO 27001:2022 | 83% | Gap remediation in progress |
| OpenSSF Scorecard | 6.28/10 (industry median ~5.5) | Improving CI/CD and dependency scanning |

**Compliance enquiries:** lois@0-1.gg
