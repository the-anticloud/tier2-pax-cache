# PAX Cache — KV Cache & Result Memoization Layer

**Status:** Production | **Version:** 1.0.0 | **Author:** PAX Performance Team  
**Domain:** 0-1.gg/pax/cache

---

## What Is PAX Cache?

PAX Cache provides multi-level caching for the PAX system, including KV cache coordination across inference instances, embedding cache for repeated vector operations, and result memoization for deterministic queries. It reduces latency and cost by serving cached responses without re-computation.

```
Incoming Request
    ↓
PAX Cache (lookup layer)
    ├─→ Check embedding cache (repeated vectors)
    ├─→ Check result memoization (exact matches)
    ├─→ Check KV cache (inference tokens)
    └─→ If hit: Return cached response (1-10ms)
    ↓
If miss: Proceed to PAX_INFERENCE_CORE
    ↓
Response + cache update
```

---

## Key Specifications

| Aspect | Details |
|--------|---------|
| **Cache Backends** | Redis (primary), In-memory, DynamoDB |
| **KV Cache Size** | 256GB+ (configurable, GPU memory) |
| **Embedding Cache Size** | 10M vectors, ANN index |
| **Result Cache TTL** | Configurable (1h-24h typical) |
| **Hit Rate (typical)** | 25-40% (task-dependent) |
| **Latency (cache hit)** | <5ms P95 (Redis) |
| **Latency (miss)** | <200ms P95 (network + lookup) |
| **Eviction Policy** | LRU, LFU, TTL hybrid |
| **Distributed Coordination** | Consistent hashing for multi-instance |

---

## Architecture

### Layer 1: Cache Lookup
- Hash-based key generation from request content
- Multi-level lookup (exact match, semantic match, prefix)
- Bloom filter for fast miss detection
- Tiered access (in-memory L1, Redis L2, disk L3)

### Layer 2: KV Cache Management
- Paged attention cache coordination
- Per-request cache slicing
- Cache line prioritization (high-confidence tokens prioritized)
- Eviction strategy based on utilization

### Layer 3: Embedding Cache
- Vector cache for repeated embeddings
- Approximate Nearest Neighbor (ANN) index
- Dimension-preserving compression
- Fast lookup via HNSW or similar

### Layer 4: Result Memoization
- Deterministic request hashing (content hash)
- Result deduplication
- Confidence scoring (how sure is this cached result?)
- Graceful degradation (stale cache acceptable in some contexts)

---

## Performance Characteristics

### Throughput Impact (Verified)
- **Cache hit:** Zero additional latency (response returned directly)
- **Cache miss:** <200ms lookup penalty
- **Distributed coordination:** <50ms for multi-instance consistency

### Cache Effectiveness
- **Math reasoning (GSM8K):** 35% hit rate (many students solve similar problems)
- **Semantic patterns (ARC):** 20% hit rate (unique puzzles, lower hits)
- **Knowledge queries:** 40-60% hit rate (FAQ-like questions)
- **Code generation:** 15-25% hit rate (unique requests)

### Scaling
- **Horizontal:** Consistent hashing enables cache sharding
- **Vertical:** Add more GPU memory for larger KV cache
- **Multi-region:** Distributed cache with async replication

---

## Quick Start

### Installation
```bash
pip install pax-cache

git clone https://github.com/0-1-gg/pax-cache.git
cd pax-cache
pip install -e .
```

### Configuration (YAML)
```yaml
cache:
  backend: "redis"  # or in_memory, dynamodb
  
  redis:
    host: "localhost"
    port: 6379
    db: 0
    password: null
    poolsize: 50
    ttl_seconds: 3600
  
  embedding_cache:
    enable: true
    max_vectors: 10000000
    dimension: 768
    index_type: "hnsw"  # or faiss
    
  result_cache:
    enable: true
    ttl_seconds: 3600
    max_entries: 1000000
    eviction_policy: "lru"  # or lfu, ttl
  
  kv_cache:
    strategy: "paged_attention"
    max_cache_size_gb: 256
    prefill_cache: true
    eviction_threshold: 0.9
  
  distributed:
    enable: false  # Set true for multi-instance
    consistent_hash: true
    replication_factor: 2
```

### Python API
```python
from pax_cache import Cache, KVCacheManager

# Initialize
cache = Cache.from_config("config.yaml")

# Store embedding
embedding = model.encode("What is 42 * 37?")
cache.store_embedding("math_q1", embedding)

# Retrieve (if exists)
cached_embedding = cache.get_embedding("math_q1")

# Store result
cache.store_result("math_q1", {"answer": 1554})

# Retrieve (if exists, else None)
cached_result = cache.get_result("math_q1")

# KV cache management
kv_manager = KVCacheManager(max_cache_gb=256)
kv_cache = kv_manager.allocate_cache(request_id, prefill_tokens=512)
```

### Docker Deployment
```bash
# Start Redis backend
docker run -d -p 6379:6379 redis:7

# Start PAX Cache server
docker run -p 8002:8002 \
  -e REDIS_URL="redis://host.docker.internal:6379" \
  pax-cache:latest \
  --config /etc/pax/config.yaml
```

---

## Integration Points

### Primary Consumers
- **PAX_ROUTER** — Router checks cache before backend dispatch
- **PAX_INFERENCE_CORE** — Inference Core populates cache with results
- **PAX_MATH_SOLVER** — Math solver benefits from cached embeddings
- **PAX_SEMANTIC_ENGINE** — Semantic engine caches pattern detection

### Complementary Systems
- **PAX_MONITOR_SYSTEM** — Monitor tracks cache hit rate + effectiveness
- **PAX_SCHEDULER** — Scheduler prioritizes cache-friendly requests
- **ANTICODE_AGENT** (Tier 1) — Caches generated code snippets
- **api-oss-gateway** (Tier 3) — Per-tenant cache isolation

### Deployment (Tier 3)
- **Redis cluster** — Distributed cache backend
- **DynamoDB** — Serverless result cache
- **Kubernetes** — Cache eviction coordination
- **PAX_MONITOR_SYSTEM** — Cache effectiveness monitoring

---

## Configuration Reference

### Cache Keys (Hashing Strategy)
```python
# Request hashing
request_hash = sha256(
    model || 
    messages.content ||  # Exact match
    temperature ||
    top_k
)

# Embedding hashing
embedding_hash = sha256(text || embedding_model || dimension)

# Result cache key: sha256(request_hash)
```

### Metrics Endpoints
```
GET /cache/stats
{
  "hit_rate_percent": 35.2,
  "total_requests": 1000000,
  "cache_hits": 352000,
  "avg_hit_latency_ms": 3.2,
  "avg_miss_latency_ms": 180.5,
  "total_saved_tokens": 15000000
}

GET /cache/health
{
  "redis_connected": true,
  "embedding_cache_size": 5000000,
  "result_cache_entries": 450000,
  "kv_cache_utilization": 0.75
}
```

---

## Security & Compliance

- **Cache isolation:** Per-tenant cache separation
- **Encryption:** At-rest encryption for sensitive cached results
- **TTL enforcement:** Automatic cache expiration
- **Audit logging:** Cache hits logged via AIOSS
- **Privacy:** Sensitive query results excluded from cache

---

## Roadmap

- **Q4 2026:** Predictive cache warming (pre-populate common queries)
- **Q1 2027:** Semantic caching (cache similar queries, not just exact)
- **Q2 2027:** Multi-region cache federation
- **Q3 2027:** ML-based cache eviction policies

---

## References

- **Source:** 0-1.gg/pax/cache
- **GitHub:** github.com/0-1-gg/pax-cache
- **Benchmarks:** MMLU, GSM8K (cache hit data in PAX_RESULTS.md)
- **Architecture:** TIER_2_MASTER_INDEX.md

---

**Next:** See APPENDIX/ for caching patterns and strategies
