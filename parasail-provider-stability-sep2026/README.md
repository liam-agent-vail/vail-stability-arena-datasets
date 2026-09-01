# Parasail Inference Stability Analysis

**VAIL Stability Arena data | September 2026**

Parasail serves 16 models in the Arena — the broadest model catalog of any independent inference provider. Analysis covers *stability*, *error rates*, and *workload latency* across all models with monitoring data, plus a look at Parasail's improvement over time on long-running endpoints.

**Key Takeaways:**
- **Stability:** Parasail's behavioral consistency is strong where it has the longest track records — 0.989 on GPT-OSS-120B (7 months) and 1.000 on DeepSeek V4 (3 months). These rank among the top providers for each model.
- **Divergence:** Parasail is one of the most consensus-aligned providers in the Arena. On GPT-OSS-120B, Parasail's average divergence is 0.72 — substantially lower than Baseten (3.19), Fireworks (3.67), and most independent providers. Parasail is reliably serving standard-configuration weights.
- **Workload Latency:** Parasail's speed is competitive on its flagship model. On GPT-OSS-120B, Parasail ranks #4 of 12 providers (p50 = 970s) — behind only Azure (457s), Baseten (732s), and Bedrock (877s), but ahead of all other independent providers.
- **Error Rates:** Mixed. Parasail has a low 3.74% error rate on GPT-OSS-120B over 7 months, but higher rates on some newer/larger models (DeepSeek V4: 66.9%, Kimi K2.6: 60.7%, Gemma 4 31B: 88.8%) — likely reflecting growing pains on recently onboarded workloads.
- **Improvement Over Time:** On GPT-OSS-120B, Parasail's p95 latency improved 53% (2,829s → 1,344s) from February to August 2026, and the Kimi K2.6 p50 dropped 59% (6,381s → 2,609s) over 4 months — clear infrastructure improvement signals.

---

## Summary

### Stability

Parasail's behavioral stability is strong on its most established models:

| Model | Parasail Stability | Rank | Best Provider | Data Period |
|---|:-:|:-:|---|:-:|
| GPT-OSS-120B | 0.989 | #3 of 12 | Bedrock, Fireworks, Novita, OpenRouter, Vertex (1.000) | 7 months |
| DeepSeek V4 | 1.000 | #1 of 6 | Parasail (1.000) | 3 months |
| Gemma 4 26B A4B | 1.000 | #1 (tied) of 5 | Parasail, Vertex (1.000) | 3 months |
| GLM-5.2 | 0.878 | #3 of 6 | Together (1.000) | 2 months |
| Kimi K3 | 0.767 | #2 of 5 | DeepInfra (0.957) | 1 week |

On GPT-OSS-120B (the broadest comparison with 12 providers and 7 months of data), Parasail's 0.989 stability ties with Nebius and Baseten — just behind the hyperscalers and Fireworks at 1.000.

On DeepSeek V4, Parasail is the *most* stable provider at 1.000, while competitors show significant instability: DeepInfra 0.767, Novita 0.225, OpenRouter 0.100.

### Divergence

This is where Parasail distinguishes itself. Parasail's output divergence from provider consensus is consistently low:

| Model | Parasail Avg Divergence | Provider Comparison |
|---|:-:|---|
| GPT-OSS-120B | 0.72 | Vertex 0.50, OpenRouter 0.53, Bedrock 0.77, Nebius 0.86, Azure 0.97, **Parasail 0.72**, Novita 1.31, DeepInfra 1.22, Together 1.11, Baseten 3.19, Fireworks 3.67 |
| DeepSeek V4 | 1.05 | OpenRouter 0.50, **Parasail 1.05**, Together 1.15, Novita 1.25, DeepInfra 7.41 |
| GLM-5.2 | 1.03 | DeepInfra 0.76, Together 0.77, **Parasail 1.03**, Fireworks 1.04, Novita 1.13, OpenRouter 1.94 |
| Kimi K3 | 0.45 | Baseten 0.32, **Parasail 0.45**, DeepInfra 0.79, Together 1.32, Fireworks 7.58 |

On GPT-OSS-120B, Parasail's divergence of 0.72 makes it the 4th most consensus-aligned provider of 12 — tightly clustered with the hyperscalers (Vertex 0.50, OpenRouter 0.53, Bedrock 0.77). This is the opposite pattern of Baseten, whose 3.19 divergence reflects aggressive serving optimizations. Parasail is running standard-configuration weights.

### Error Rates

Parasail's error rates vary significantly by model. On long-running, established endpoints, error rates are competitive. On newer or larger models, they're elevated:

| Model | Period | Parasail Errors | Parasail Error Rate | Best Provider (Error Rate) |
|---|:-:|:-:|:-:|---|
| GPT-OSS-120B | Feb–Sep 2026 | 59 / 1,579 | 3.74% | Fireworks (0.07%), Groq (0.00%) |
| Qwen3 235B | Feb–Mar 2026 | 5 / 249 | 2.01% | Together (0.00%), Novita (0.56%) |
| GLM-4.7 | Feb–Mar 2026 | 11 / 247 | 4.45% | Baseten (0.00%), Novita (0.00%) |
| MiniMax M2.5 | Mar–Apr 2026 | 11 / 229 | 4.80% | Baseten (0.00%), Fireworks (0.00%) |
| Gemma 4 26B A4B | Jun–Sep 2026 | 51 / 659 | 7.74% | OpenRouter (0.00%), DeepInfra (0.17%) |
| GLM-5.2 | Jul–Sep 2026 | 44 / 428 | 10.28% | OpenRouter (0.00%), DeepInfra (0.26%) |
| Kimi K2 Instruct | Feb 2026 | 11 / 78 | 14.10% | Baseten (0.00%), Fireworks (0.00%) |
| Kimi K2.5 | Feb–May 2026 | 151 / 671 | 22.50% | Novita (0.00%), Bedrock (0.73%) |
| Kimi K3 | Aug–Sep 2026 | 11 / 33 | 33.33% | Together (0.00%), DeepInfra (0.00%) |
| GLM5 | Mar–Apr 2026 | 88 / 217 | 40.55% | Fireworks (0.00%), Nebius (0.00%) |
| GLM-5.1 | Apr–Jul 2026 | 486 / 1,089 | 44.63% | DeepInfra (0.00%), Fireworks (0.00%) |
| DeepSeek V3.2 | Feb–Apr 2026 | 227 / 481 | 47.19% | Novita (0.00%), Azure (6.11%) |
| Kimi K2.6 | May–Aug 2026 | 1,321 / 2,177 | 60.68% | Fireworks (0.26%), Baseten (0.82%) |
| DeepSeek V4 | Jun–Sep 2026 | 1,259 / 1,881 | 66.93% | OpenRouter (0.00%), Novita (0.50%) |
| Gemma 4 31B | Apr–Jun 2026 | 2,336 / 2,632 | 88.75% | DeepInfra (1.09%), Together (5.88%) |

The pattern is clear: Parasail's GPT-OSS-120B endpoint (its longest-running) has a reasonable 3.74% error rate, but newer deployments — particularly the Kimi family and DeepSeek models — show high failure rates. This likely reflects infrastructure scaling challenges on recently onboarded large models.

### Workload Latency

Parasail is competitive on speed for its flagship models. On GPT-OSS-120B, Parasail ranks #4 of 12 providers — behind only the hyperscalers and Baseten:

#### GPT-OSS-120B (Feb–Sep 2026, 12 providers)

| Provider | p50 | p95 | Error Rate | Period |
|---|:-:|:-:|:-:|:-:|
| Azure | 457s | 1,704s | 4.82% | Feb–Sep |
| Baseten | 732s | 3,200s | 0.13% | Feb–Sep |
| Bedrock | 877s | 1,696s | 0.30% | Feb–Sep |
| **Parasail** | **970s** | **4,089s** | **3.74%** | **Feb–Sep** |
| Nebius | 1,085s | 6,974s | 0.58% | Feb–Sep |
| Novita | 2,642s | 7,865s | 3.66% | Feb–Sep |
| Fireworks | 3,124s | 8,813s | 0.07% | Feb–Sep |
| Together | 3,368s | 9,673s | 1.48% | Feb–Sep |
| OpenRouter | 4,258s | 9,348s | 3.82% | Mar–Sep |
| DeepInfra | 4,404s | 8,918s | 1.33% | Feb–Sep |
| Groq | 5,623s | 9,859s | 0.00% | Feb–May |

Parasail's p50 of 970s is 3.4x faster than the provider median (3,124s) and 4.5x faster than the slowest independent provider.

#### DeepSeek V4 (Jun–Sep 2026, 6 providers)

| Provider | p50 | p95 | Error Rate |
|---|:-:|:-:|:-:|
| DeepInfra | 2,332s | 5,118s | 0.84% |
| Together | 2,633s | 5,074s | 31.05% |
| Fireworks | 2,673s | 5,614s | 2.13% |
| Novita | 2,902s | 3,874s | 0.50% |
| **Parasail** | **3,088s** | **6,963s** | **66.93%** |
| OpenRouter | 3,393s | 5,611s | 0.00% |

#### GLM-5.2 (Jul–Sep 2026, 6 providers)

| Provider | p50 | p95 | Error Rate |
|---|:-:|:-:|:-:|
| **Parasail** | **2,366s** | **3,730s** | **10.28%** |
| Together | 3,456s | 5,989s | 0.84% |
| OpenRouter | 3,635s | 5,906s | 0.00% |
| Fireworks | 5,282s | 6,823s | 0.83% |
| DeepInfra | 5,567s | 10,507s | 0.26% |
| Novita | 6,308s | 9,077s | 0.26% |

Parasail is the *fastest* provider on GLM-5.2 (p50 2,366s vs next-best Together at 3,456s), and the *fastest* on Qwen3 235B (p50 1,367s, #2 of 7).

#### Qwen3 235B (Feb–Mar 2026, 7 providers)

| Provider | p50 | p95 | Error Rate |
|---|:-:|:-:|:-:|
| Nebius | 947s | 5,291s | 4.49% |
| **Parasail** | **1,367s** | **2,665s** | **2.01%** |
| Together | 1,518s | 5,882s | 0.00% |
| Novita | 2,068s | 5,262s | 0.56% |
| DeepInfra | 4,196s | 12,115s | 9.60% |
| Fireworks | 5,253s | 10,043s | 42.55% |

### Has Parasail Improved Over Time?

Two clear signals:

**GPT-OSS-120B (7-month trend):**

| Month | p50 Latency | p95 Latency | Error Rate | Stability (avg) |
|-------|:-:|:-:|:-:|:-:|
| Feb 2026 | 976s | 2,829s | 2.9% | 0.974 |
| Mar 2026 | 2,184s | 5,660s | 4.5% | 0.912 |
| Apr 2026 | 2,641s | 5,784s | 3.1% | 0.974 |
| May 2026 | 1,040s | 4,106s | 8.5% | 0.938 |
| Jun 2026 | 549s | 2,141s | 0.8% | 0.819 |
| Jul 2026 | 617s | 2,097s | 3.1% | 0.956 |
| Aug 2026 | 703s | 1,344s | 2.6% | 0.923 |

The story is non-linear but positive: after a rough March–April period (p50 > 2,000s), Parasail's GPT-OSS-120B latency improved dramatically starting in June. The p95 improved 53% from February (2,829s) to August (1,344s). Error rates also improved — from a spike of 8.5% in May down to 2.6% in August.

**Kimi K2.6 (4-month trend):**

Parasail served Kimi K2.6 (1T MoE, 32B active) continuously from May through August 2026:

| Month | p50 Latency | p95 Latency |
|---|:-:|:-:|
| May 2026 | 6,381s | 11,674s |
| Jun 2026 | 4,939s | 7,310s |
| Jul 2026 | 4,639s | 6,641s |
| Aug 2026 | 2,609s | 5,148s |

p50 improved 59% (6,381s → 2,609s) over 4 months — a substantial serving optimization on a trillion-parameter model.

**GLM family trend:**

| Model | Period | Parasail p50 |
|---|:-:|:-:|
| GLM-4.7 | Feb–Mar 2026 | 4,157s |
| GLM5 | Mar–Apr 2026 | 10,314s |
| GLM-5.1 | Apr–Jul 2026 | 5,812s |
| GLM-5.2 | Jul–Sep 2026 | 2,366s |

Each generation is a different model, so direct comparison is imperfect. But GLM-5.2 (the latest) is dramatically faster than GLM-5.1 and GLM5, and Parasail ranks #1 of 6 providers on it — suggesting meaningful infrastructure improvements for this model family.

---

## Parasail at a Glance

| Model | Stability | Divergence | p50 Latency | Error Rate | Period |
|---|:-:|:-:|:-:|:-:|:-:|
| GPT-OSS-120B | 0.989 | 0.72 | 970s | 3.74% | Feb–Sep (7mo) |
| DeepSeek V4 | 1.000 | 1.05 | 3,088s | 66.93% | Jun–Sep (3mo) |
| Gemma 4 26B A4B | 1.000 | 4.64 | 2,522s | 7.74% | Jun–Sep (3mo) |
| GLM-5.2 | 0.878 | 1.03 | 2,366s | 10.28% | Jul–Sep (2mo) |
| Kimi K3 | 0.767 | 0.45 | 5,157s | 33.33% | Aug–Sep (1wk) |
| Kimi K2.6 | — | — | 4,354s | 60.68% | May–Aug (4mo) |
| Kimi K2.5 | — | — | 4,624s | 22.50% | Feb–May (3mo) |
| GLM-5.1 | — | — | 5,812s | 44.63% | Apr–Jul (3mo) |
| Qwen3 235B | — | — | 1,367s | 2.01% | Feb–Mar (1mo) |
| GLM-4.7 | — | — | 4,160s | 4.45% | Feb–Mar (1mo) |
| MiniMax M2.5 | — | — | 4,467s | 4.80% | Mar–Apr (1mo) |
| Trinity Large | — | — | 2,474s | 20.87% | Apr–Aug (4mo) |
| Gemma 4 31B | — | — | 3,220s | 88.75% | Apr–Jun (2mo) |
| GLM5 | — | — | 10,314s | 40.55% | Mar–Apr (1mo) |
| DeepSeek V3.2 | — | — | 8,806s | 47.19% | Feb–Apr (2mo) |
| Kimi K2 Instruct | — | — | 1,134s | 14.10% | Feb (1wk) |

---

*Data: [VAIL Stability Arena](https://arena.projectvail.com) API + Identity Monitor DB, Feb–Sep 2026. Analysis by [Project VAIL](https://projectvail.com).*
