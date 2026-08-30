# Baseten Inference Stability Analysis

**VAIL Stability Arena data | August 2026**

Baseten serves 9 models in the Arena. Three have sufficient monitoring data; the other six were recently onboarded.

---

## Current Stability Scores

*Stability (0.0–1.0): behavioral consistency over a 72-hour window. Above 0.9 = stable.*

### GPT-OSS-120B

| Provider | Stability | | Provider | Stability |
|----------|:-:|-|----------|:-:|
| Bedrock | 1.000 | | Parasail | 0.967 |
| Azure | 1.000 | | **Baseten** | **0.967** |
| Fireworks | 1.000 | | DeepInfra | 0.886 |
| Nebius | 1.000 | | Novita | 0.833 |
| OpenRouter | 0.975 | | Together | 0.663 |

### Kimi K3 & Nemotron Ultra

| Endpoint | Baseten | Best Other | Worst Other |
|----------|:-:|:-:|:-:|
| Kimi K3 | 1.000 | 1.000 (Together) | 0.567 (Fireworks) |
| Nemotron Ultra | 1.000 | 1.000 (DeepInfra) | 0.833 (Nebius) |

**Baseten stability is competitive** — mid-pack on GPT-OSS-120B, top-tier on the other two.

---

## Provider Divergence

*Divergence ratio: how much a provider's outputs differ from the consensus of others serving the same weights. Near 1.0 = aligned. Higher = more different. Higher divergence may reflect different quantization or serving optimizations — not necessarily worse quality.*

### GPT-OSS-120B (90-day avg)

| Provider | Avg Divergence | | Provider | Avg Divergence |
|----------|:-:|-|----------|:-:|
| OpenRouter | 0.46 | | DeepInfra | 1.35 |
| Bedrock | 0.75 | | Novita | 1.81 |
| Parasail | 0.78 | | **Baseten** | **3.58** |
| Azure | 0.79 | | Fireworks | 4.10 |
| Nebius | 0.86 | | | |
| Together | 1.06 | | | |

### Nemotron Ultra (75-day avg)

| Provider | Avg Divergence |
|----------|:-:|
| DeepInfra | 0.88 |
| Nebius | 1.45 |
| **Baseten** | **3.61** |

Baseten and Fireworks both show high divergence — a pattern consistent with providers applying custom serving optimizations. Whether this matters depends on the use case: cross-provider reproducibility vs. single-provider consistency.

---

## Baseten Trend (GPT-OSS-120B, 7 months)

| Month | Stability | Divergence |
|-------|:-:|:-:|
| Feb 2026 | 0.962 | 3.41 |
| Mar | 0.964 | 2.91 |
| Apr | 0.963 | 2.24 |
| May | 0.988 | 3.07 |
| Jun | 0.977 | 3.58 |
| Jul | 0.978 | 3.64 |
| Aug | 0.989 | 3.51 |

Stability has improved (~3%). Divergence dipped in spring but returned to prior levels — Baseten appears to have improved consistency while maintaining their own serving approach.

---

*Data: [VAIL Stability Arena](https://arena.projectvail.com) API, Feb–Aug 2026. Analysis by [Project VAIL](https://projectvail.com).*
