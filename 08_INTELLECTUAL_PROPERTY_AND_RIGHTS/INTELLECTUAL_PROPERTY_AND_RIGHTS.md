# Intellectual Property and Rights — PAX_CACHE

**Project:** `PAX_CACHE`
**Tier:** TIER_2_ANTICLOUD_PAX
**Domain:** PAX 27B model inference, Q4 quantization, transformer architecture
**Maintainer:** Anticloud FZ LLE · 0-1.gg · lois@0-1.gg · Dubai, UAE
**Model:** Anticloud PAX L5 Narrow L2 General 27B
**AIOSS Chain:** `8b4a8a4f6312dfbe885de8280716985637c163fd2a4b5590341d56db1cc4e560`
**Date:** October 2026

---

## IP Overview

`PAX_CACHE` incorporates both open-source components (Apache 2.0) and Anticloud FZ LLE proprietary innovations (USPTO pending). This document describes what is owned, what is open, and how rights are structured.

## Anticloud FZ LLE Proprietary Assets (USPTO Pending)

### 1. KANTOR K5 Post-Quantum Hash
- **Scope:** The specific construction `SHA3-256(archive_sha3 || file_size_le64 || project_name_utf8 || NULL || timestamp_iso)`
- **Prior art:** Harvard Dataverse DOI 10.7910/DVN/YMJKOG (2025-2026), Internet Archive, Zenodo, ORCID 0009-0009-2233-6107
- **Status:** USPTO provisional drafting in progress

### 2. AIOSS Format (AI Operating System Specification)
- **Scope:** The append-only SHA3-256 chain format for AI inference audit logging
- **Construction:** `H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n)`
- **Prior art:** Published 2025-2026, archived across multiple independent repositories
- **Chain hash:** `8b4a8a4f6312dfbe885de8280716985637c163fd2a4b5590341d56db1cc4e560`

### 3. System of Things (SoT) Architecture
- **Scope:** Proprioceptive typed-component AI system architecture
- **Description:** Self-state model → prediction layer → typed action → AIOSS entry → output → feedback
- **Prior art:** Published and archived Anticloud FZ LLE specifications

### 4. PAX L5 Narrow L2 General 27B Model Weights
- **Scope:** Trained model weights and fine-tuning methodology for regulated-domain optimization
- **Classification:** Morris et al. (2023) AGI taxonomy arXiv:2311.02462

## Open-Source Components

`PAX_CACHE` incorporates open-source libraries under their respective permissive licenses (Apache 2.0, MIT). Full dependency listing in `27_DEPENDENCIES/DEPENDENCIES.md`.

## Contributor Assignment

All contributions to `PAX_CACHE` by third parties require execution of the Anticloud FZ LLE Contributor Agreement (CA), which assigns copyright to Anticloud FZ LLE while preserving attribution rights. CA template: see `COMMONS/02_Contributor_Agreement.md`.

**Contact:** lois@0-1.gg
