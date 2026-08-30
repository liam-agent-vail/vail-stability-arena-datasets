# Baseten Inference Stability Analysis

**VAIL Stability Arena data | August 2026**

Baseten serves 9 models in the Arena. Analysis covers *stability*, *error rates*, and *latency* across all models with sufficient monitoring data, plus a look at Baseten's improvement over time — particularly for large models.

**Key Takeaways:**
- **Latency:** Baseten is the fastest or second-fastest provider on nearly every model it serves, often 5–20x faster than the provider median on large (200B+) models.
- **Stability:** Baseten's behavioral consistency is competitive (0.967–1.000), ranking mid-pack to top-tier depending on the model.
- **Error Rates:** Baseten has the second-lowest error rate of any provider at 0.13%, with zero errors on multiple models.
- **Stack Improvement:** Over 7 months, Baseten has meaningfully improved both speed (32–45% faster) and stability (0.962 → 0.989) — likely driven by R&D investment in custom quantization and serving optimizations, which also explains its elevated output divergence from providers using more standard configurations.

> **Note on latency metric:** Generation time is total wall-clock time for a standardized fingerprinting workload (800 API calls per run with fixed concurrency). Lower = faster inference throughput. Same workload across all providers.

---

## Summary

### Stability

Baseten's behavioral stability is competitive across all models with data. On GPT-OSS-120B (7 months of monitoring), Baseten scores 0.967 — solidly stable, on par with Parasail and OpenRouter, behind the hyperscalers (Azure, Bedrock, Fireworks, Nebius all at 1.000). On Kimi K3 and Nemotron Ultra, Baseten achieves a perfect 1.000 — tied for best among all providers.

Baseten's output divergence (how much its responses differ from the consensus of other providers serving the same weights) is elevated on GPT-OSS-120B (3.58) and Nemotron Ultra (3.61). Fireworks shows a similar pattern (4.10 on GPT-OSS-120B). This likely reflects different quantization or serving optimizations rather than quality differences — providers optimizing aggressively for throughput naturally diverge from providers using more standard configurations.

### Error Rates

Baseten has among the lowest error rates of any provider. On GPT-OSS-120B — the most comprehensive comparison with 7 months of data — Baseten's error rate is 0.13% (2 errors out of 1,538 attempts), second only to Fireworks at 0.07%. This is lower than Bedrock (0.30%), Azure (4.84%), and all independent inference providers. On Nemotron Ultra and Kimi K3, Baseten has a 0.00% error rate — zero errors across hundreds of runs.

### Latency

This is where Baseten stands out most. Across nearly every model it serves, Baseten is the #1 or #2 fastest provider — often by a large margin:

| Model (approx size) | Period | Baseten Rank | vs Provider Median |
|---|:-:|:-:|:-:|
| Kimi K2.5 (~400B MoE) | Feb–May 2026 | #1 of 7 | 7–14x faster |
| Kimi K2.6 (~400B MoE) | May–Aug 2026 | #1 of 5 | 8–9x faster |
| Kimi K2 Instruct (~400B MoE) | Feb 2026 | #1 of 8 | 3.6x faster |
| Kimi K3 (~400B MoE) | Aug 2026 | #1 of 5 | 2.6x faster |
| GLM-4.7 (~200B+) | Feb–Mar 2026 | #1 of 8 | 12–20x faster |
| GLM-5 (~200B+) | Mar–Apr 2026 | #1 of 9 | 5x faster |
| Nemotron Ultra (253B MoE) | Jun–Aug 2026 | #1–2 of 4 | 2–3x faster |
| MiniMax M2.5 (~200B+ MoE) | Mar–Apr 2026 | #1 of 6 | 1.3–2.3x faster |
| GPT-OSS-120B (120B) | Feb–Aug 2026 | #2–4 of 11 | 2–5x faster |

The speed advantage is most dramatic on larger models (200B+), where Baseten is typically 5–20x faster than the median provider.

### Has Baseten Improved at Serving Large Models?

Two signals suggest yes:

**Within a single model:** Kimi K2.6 (~400B MoE), which Baseten served continuously from May through August 2026, shows a clear improvement: p50 latency dropped from 905s to 493s — a 45% speed improvement over 4 months.

**Across the Kimi model family:** Baseten served four generations of Kimi models (~400B MoE class) spanning the full Feb–Aug monitoring window:

| Model | Period | Baseten p50 |
|---|:-:|:-:|
| Kimi K2 Instruct | Feb 2026 | 706s |
| Kimi K2.5 | Feb–May 2026 | 597–810s |
| Kimi K2.6 | May–Aug 2026 | 905s → 493s |
| Kimi K3 | Aug 2026 | 2,561s |

Each generation is a different model with different architectures, so direct comparison is imperfect. But across similarly-sized models, Baseten has maintained a consistent #1 speed ranking while the absolute latency on Kimi K2.6 improved significantly. The Kimi K3 latency is higher, likely reflecting a larger or more complex model rather than a serving regression — Baseten still ranks #1 of 5 providers on K3.

**On GPT-OSS-120B (7-month trend):**

| Month | p50 Latency | p95 Latency | Stability |
|-------|:-:|:-:|:-:|
| Feb 2026 | 994s | 2,428s | 0.962 |
| May 2026 | 658s | 2,986s | 0.988 |
| Aug 2026 | 680s | 1,131s | 0.989 |

p50 improved 32%, p95 improved 53%, and stability improved from 0.962 to 0.989 — all while maintaining a near-zero error rate (2 total errors in 7 months).

---

*Data: [VAIL Stability Arena](https://arena.projectvail.com) API + Identity Monitor DB, Feb–Aug 2026. Analysis by [Project VAIL](https://projectvail.com).*
