# How to Update — PAX_CACHE

**Project:** `PAX_CACHE`
**Tier:** TIER_2_ANTICLOUD_PAX
**Domain:** PAX 27B model inference, Q4 quantization, transformer architecture
**Maintainer:** Anticloud FZ LLE · 0-1.gg · lois@0-1.gg · Dubai, UAE
**Model:** Anticloud PAX L5 Narrow L2 General 27B
**AIOSS Chain:** `8b4a8a4f6312dfbe885de8280716985637c163fd2a4b5590341d56db1cc4e560`
**Date:** October 2026

---

## Update Procedure

Updates to `PAX_CACHE` must preserve branding, AIOSS chain continuity, and KANTOR K5 archive integrity. Do not update without following this procedure.

## Before You Update

1. **Backup current AIOSS chain** to at least 2 locations
2. **Record current K5 hash** from HASHES.md
3. **Note current chain hash**: `8b4a8a4f6312dfbe885de82807169856...`
4. **Test in staging** — never update production directly

## Update Steps

### Step 1: Download and Verify New Package

```bash
# Download new package
wget https://0-1.gg/releases/PAX_CACHE-latest.tar.gz

# Verify KANTOR K5 hash before extracting
python verify_k5.py \
  --archive PAX_CACHE-latest.tar.gz \
  --project PAX_CACHE \
  --hashes HASHES_new.md
```

### Step 2: Verify Chain Compatibility

```bash
python verify_chain.py \
  --current-genesis 8b4a8a4f6312dfbe885de8280716985637c163fd2a4b5590341d56db1cc4e560 \
  --new-package PAX_CACHE-latest.tar.gz
# Must output: CHAIN_COMPATIBLE: True
```

### Step 3: Apply Update (Zero-Downtime)

```bash
./update.sh \
  --package PAX_CACHE-latest.tar.gz \
  --mode rolling \
  --chain-preserve true \
  --brand-preserve true  # ← ALWAYS INCLUDE THIS FLAG
```

### Step 4: Verify Post-Update

```bash
python verify_deployment.py --project PAX_CACHE --full-check
# Expected: AIOSS=PASS, K5=PASS, BRAND=PASS, COMPLIANCE=PASS
```

## Branding Preservation

**Critical:** The `--brand-preserve true` flag is mandatory. Updates must not alter:
- Anticloud FZ LLE attribution in user-facing interfaces
- AIOSS chain genesis hash references
- KANTOR K5 hash methodology
- Apache 2.0 / Anticommons License notices

A build that fails brand checks must not be deployed.

## Rollback

```bash
./update.sh --rollback --to-version <previous-k5-hash>
```

**Support:** lois@0-1.gg
