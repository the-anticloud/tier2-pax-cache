# PAX Cache — KV Cache & Result Memoization Layer

![license](https://img.shields.io/badge/license-Apache--2.0-blue) ![licence](https://img.shields.io/badge/enterprise-dual--licence-informational) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![collection](https://img.shields.io/badge/collection-Anticloud%20FZ%20LLE-lightgrey)

> PAX Cache provides multi-level caching for the PAX system, including KV cache coordination across inference instances, embedding cache for repeated vector operations, and result memoization for deterministic queries. It reduces latency and cost by serving cached responses without re-computation.

| | |
|---|---|
| Collection | TIER 2 ANTICLOUD PAX |
| Vendor | Anticloud FZ LLE |
| Licence | Apache-2.0 + Enterprise commercial dual (Anticommons 1.0) |
| Payload | documentation, evidence and licence material |

## What this project is

PAX Cache provides multi-level caching for the PAX system, including KV cache coordination across inference instances, embedding cache for repeated vector operations, and result memoization for deterministic queries. It reduces latency and cost by serving cached responses without re-computation.

**Scope honesty:** no model decoding path ships in this project. It is a deterministic/offline component with AIOSS-style audit wiring. PAX may call it as a tool; no inference is claimed here.

## Architecture

```mermaid
graph LR
    D[docs/ handoff package] --> R[tier2-pax-cache]
    R --> E[EVIDENCE.json\nmeasured results + provenance]
    E --> A[SHA3-256 audit chain]
    A --> L[Apache-2.0]
```

## Install

```bash
# No executable package manifest was detected in this project.
# This repository ships documentation, evidence and licence material.
# See docs/ for the full handoff package.
```

Detected stack: docs-only

## Evidence and measured results

**NOT MEASURED.** No results file in this project carries both a value and run provenance (commit or date), so no benchmark number is claimed here. This is deliberate: Anticloud FZ LLE does not publish unmeasured scores.

### Metric ledger status

Rebuilt from this project's own metric ledger. Documented-but-unverified figures are deliberately dropped; nothing below is inferred.

```csv
metric,status,note
TRL,NOT-MEASURED,no verified run recorded
tok/s,NOT-MEASURED,no verified run recorded
NIST,NOT-MEASURED,no verified run recorded
license,MEASURED(Apache-2.0 + Enterprise dual),reported by project metric ledger
```

## Millennium problem proposals

This project packages Anticloud Millennium problem proposals: P01, P02, P03, P04, P05, P06, P07, P08, P09, P10, P11, P12, P13, P14.

Proposals are shipped as PDFs under `25_MILLENNIUM_PROBLEM_PROPOSALS/` in the internal handoff tree and summarised in `docs/`.

## Documentation map

- `01_INVESTOR_PACKAGE/`
- `02_COMMITMENT_TO_SOCIETY/`
- `03_COMMITMENT_TO_HUMANITY/`
- `04_COMMITMENT_TO_ENVIRONMENT/`
- `05_COMMITMENTS_TO_PAST_PRESENT_FUTURE/`
- `06_WHITELABELLING_AND_REPACKAGING/`
- `07_ENTERPRISE_LICENSE_AND_PRICING/`
- `08_INTELLECTUAL_PROPERTY_AND_RIGHTS/`
- `09_COMPLIANCE/`
- `10_TECHNICAL_HANDOFF/`
- `11_TUTORIAL_DEVELOPERS/`
- `12_TUTORIAL_ENTERPRISE/`
- `13_TUTORIAL_USERS/`
- `14_DEVELOPER_COOKBOOKS/`
- `15_DISASTER_RECOVERY/`
- `16_VULNERABILITY_MANAGEMENT/`
- `17_HOW_TO_UPDATE/`
- `18_COMMAND_LINE_INTERFACE/`
- `19_SYSTEM_OF_THINGS_SOT/`
- `20_ACADEMIC_RESEARCH/`
- `21_RELATED_SCIENTIFIC_RESEARCH/`
- `22_INDEPENDENT_INSURANCE/`
- `23_HOW_TO_CITE/`
- `24_ANTICOMMONS_LICENSE/`
- `25_MILLENNIUM_PROBLEM_PROPOSALS/`
- `26_INTEGRATIONS_AND_SDK/`
- `27_DEPENDENCIES/`
- `28_TECHNICAL_WHITEPAPER/`
- `29_INVESTOR_MEMO/`
- `30_LOI/`
- `31_UNIT_ECONOMICS/`
- `32_CONTRACTS/`
- `33_COMPETITIVE_MOAT/`
- `34_FOUNDER_PROFILE/`
- `35_INVESTOR_FAQ/`
- `36_ADVISORY_BOARD/`

## Archive manifest

- `_ARCHIVES/MANIFEST.sha3 (501 bytes)`
- `_ARCHIVES/PAX_CACHE_docs.7z (14910 bytes)`
- `_ARCHIVES/PAX_CACHE_docs.7z.k5 (64 bytes)`
- `_ARCHIVES/PAX_CACHE_docs.tar.gz (19737 bytes)`
- `_ARCHIVES/PAX_CACHE_docs.tar.gz.k5 (64 bytes)`
- `_ARCHIVES/PAX_CACHE_docs.zip (54955 bytes)`
- `_ARCHIVES/PAX_CACHE_docs.zip.k5 (64 bytes)`

## Licence

Licensed under **Apache-2.0 + Enterprise commercial dual (Anticommons 1.0)**. See `LICENSE` and `NOTICE.md`. Apache-2.0 governs the open-source component; commercial use inside closed enterprise products is governed by the Anticloud Enterprise licence.

SPDX-License-Identifier: Apache-2.0
