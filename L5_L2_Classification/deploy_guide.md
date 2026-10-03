# Deploy Guide — PAX_CACHE
**Stack:** Python 3.11, mmap, CUDA unified memory, numpy, AIOSS_FORMAT | Air-gap capable

## Prerequisites
Anticloud core stack installed. PAX 27B weights (pax-27b-q4.gguf). AIOSS_FORMAT.

## Install
```bash
pip install anticloud-pax-cache
```

## AIOSS Integration
```bash
aioss init --module PAX_CACHE --output ./pax_cache.aioss
```

## Air-Gap
```bash
pip download -r requirements.txt -d ./wheels/
pip install --no-index --find-links ./wheels/ -r requirements.txt
```

## PAX Harness Wiring
```python
from anticloud_pax import PAXHarness
harness = PAXHarness(model_path="./pax-27b-q4.gguf", module="PAX_CACHE",
                     aioss_chain="./pax_cache.aioss",
                     classification="L5_NARROW_L2_GENERAL")
```

## Verification
```bash
aioss verify --chain ./pax_cache.aioss --verbose
python -m pax_cache.tests.smoke
```
