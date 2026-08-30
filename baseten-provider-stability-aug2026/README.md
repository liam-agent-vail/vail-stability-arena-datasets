# Baseten Inference Stability Analysis

**VAIL Stability Arena data | August 2026**

Baseten serves 9 models in the Arena. Analysis covers three dimensions — *speed*, *error rate*, and *behavioral stability/divergence* — across the models with sufficient monitoring history.

> **Note on speed metric:** Generation time is total wall-clock time for a standardized fingerprinting workload (800 API calls per run with fixed concurrency). Lower = faster inference throughput. Same workload across all providers, so it's an apples-to-apples comparison.

---

## GPT-OSS-120B — Full Provider Comparison

*7 months of data (Feb–Aug 2026). Most comprehensive comparison.*

### Speed (fingerprint generation time, seconds)

| Provider | p50 | p95 | Avg |
|----------|:-:|:-:|:-:|
| Azure | 457 | 1,704 | 636 |
| **Baseten** | **729** | **3,202** | **1,152** |
| Bedrock | 878 | 1,695 | 930 |
| Parasail | 970 | 4,087 | 1,517 |
| Nebius | 1,085 | 6,974 | 2,128 |
| Vertex | 1,155 | 3,001 | 1,380 |
| Novita | 2,641 | 7,865 | 3,276 |
| Fireworks | 3,125 | 8,811 | 3,755 |
| Together | 3,368 | 9,670 | 4,146 |
| OpenRouter | 4,256 | 9,348 | 4,825 |
| DeepInfra | 4,404 | 8,911 | 4,849 |

**Baseten is the 2nd fastest provider** (p50 basis), behind only Azure. Notably faster than Bedrock, Vertex, and all independent providers.

### Error Rate

| Provider | Successes | Errors | Error Rate |
|----------|:-:|:-:|:-:|
| Fireworks | 1,407 | 1 | 0.07% |
| **Baseten** | **1,536** | **2** | **0.13%** |
| Bedrock | 1,987 | 6 | 0.30% |
| Nebius | 1,360 | 8 | 0.58% |
| DeepInfra | 1,403 | 19 | 1.34% |
| Together | 1,388 | 21 | 1.49% |
| Novita | 1,387 | 53 | 3.68% |
| Parasail | 1,511 | 59 | 3.76% |
| OpenRouter | 1,301 | 52 | 3.84% |
| Azure | 1,789 | 91 | 4.84% |
| Vertex | 1,484 | 600 | 28.79% |

**Baseten has the 2nd lowest error rate** — 0.13%, behind only Fireworks at 0.07%. Lower than Bedrock, Azure, and all other providers.

### Stability & Divergence (current)

| Provider | Stability | Divergence |
|----------|:-:|:-:|
| Azure | 1.000 | 0.79 |
| Bedrock | 1.000 | 0.75 |
| Fireworks | 1.000 | 4.10 |
| Nebius | 1.000 | 0.86 |
| OpenRouter | 0.975 | 0.46 |
| **Baseten** | **0.967** | **3.58** |
| Parasail | 0.967 | 0.78 |
| DeepInfra | 0.886 | 1.35 |
| Novita | 0.833 | 1.81 |
| Together | 0.663 | 1.06 |

Baseten stability is mid-pack (0.967). Divergence is high (3.58) — outputs differ from provider consensus, likely reflecting different serving optimizations. Fireworks shows a similar pattern (stable but high divergence).

---

## Kimi K3 — Provider Comparison

*3 days of data (newly onboarded).*

| Provider | p50 Speed | Error Rate | Stability | Divergence |
|----------|:-:|:-:|:-:|:-:|
| **Baseten** | **2,561s** | **0.00%** | **1.000** | **0.32** |
| Fireworks | 4,481s | 5.56% | 0.567 | 7.65 |
| Parasail | 5,147s | 11.11% | 0.957 | 0.42 |
| Together | 6,679s | 0.00% | 1.000 | 1.41 |
| DeepInfra | 8,942s | 0.00% | 0.886 | 0.73 |

**Baseten leads on all four dimensions** — fastest, zero errors, perfect stability, lowest divergence. Early data, but strong.

---

## Nemotron Ultra — Provider Comparison

*75 days of data (Jun–Aug 2026).*

| Provider | p50 Speed | Error Rate | Stability | Divergence |
|----------|:-:|:-:|:-:|:-:|
| Nebius | 784s | 1.65% | 0.833 | 1.45 |
| **Baseten** | **839s** | **0.00%** | **1.000** | **3.61** |
| DeepInfra | 2,137s | 3.00% | 1.000 | 0.88 |
| OpenRouter | 9,274s | 99.07% | N/A | N/A |

**Baseten is the fastest with zero errors and perfect stability.** Divergence is elevated — different from DeepInfra/Nebius outputs but perfectly consistent over time.

---

## Has Baseten Improved? (GPT-OSS-120B, 7-month trend)

| Month | p50 Speed | p95 Speed | Errors | Stability | Divergence |
|-------|:-:|:-:|:-:|:-:|:-:|
| Feb 2026 | 994s | 2,428s | 0 | 0.962 | 3.41 |
| Mar | 895s | 4,350s | 0 | 0.964 | 2.91 |
| Apr | 1,098s | 4,043s | 0 | 0.963 | 2.24 |
| May | 658s | 2,986s | 0 | 0.988 | 3.07 |
| Jun | 691s | 2,745s | 0 | 0.977 | 3.58 |
| Jul | 668s | 3,276s | 0 | 0.978 | 3.64 |
| Aug | 680s | 1,131s | 2 | 0.989 | 3.51 |

**Clear improvement across speed and stability:**
- *Speed:* p50 dropped from 994s → 680s (32% faster). p95 from 2,428s → 1,131s (53% faster tail latency improvement).
- *Errors:* Near-zero throughout — 0 errors for 6 months, 2 in August.
- *Stability:* Improved from 0.962 → 0.989.
- *Divergence:* Dipped to 2.24 in April but settled at ~3.5. Baseten maintains its own serving approach rather than converging toward other providers.

---

*Data: [VAIL Stability Arena](https://arena.projectvail.com) API + Identity Monitor DB, Feb–Aug 2026. Analysis by [Project VAIL](https://projectvail.com).*
