# Baseten Inference Stability: How Does It Compare?

**An analysis of Baseten's serving stability vs. other inference providers using [VAIL Stability Arena](https://arena.projectvail.com) data.**

*Generated: August 29, 2026*

---

## TL;DR

Baseten serves 9 models in the Stability Arena. Of the three with sufficient monitoring data, Baseten shows **strong stability scores** (avg 0.98–1.00) but **elevated divergence** from the provider consensus on two models, meaning its outputs differ more from other providers serving the same weights. Over 7 months of monitoring, Baseten's stability has **modestly improved** (0.962 → 0.989 monthly avg on GPT-OSS-120B), though divergence remains consistently high.

---

## Models Baseten Serves in the Arena

| Model | Baseten Endpoint | Other Providers |
|-------|-----------------|-----------------|
| GLM-4.7 | glm-4.7-baseten-chat | DeepInfra, Fireworks, Nebius, Novita, Parasail, Together, Vertex |
| GLM-5 | glm5-baseten-chat | DeepInfra, Fireworks, Nebius, Novita, OpenRouter, Parasail, Together, Vertex |
| GPT-OSS-120B | gpt-oss-120b-baseten-chat | Azure, Bedrock, DeepInfra, Fireworks, Groq, Nebius, Novita, OpenRouter, Parasail, SambaNova, Together, Vertex |
| Kimi K2 Instruct | kimi-k2-instruct-baseten-chat | DeepInfra, Fireworks, Groq, Nebius, Novita, Parasail, Together |
| Kimi K2.5 | kimi-k2.5-baseten-chat | Bedrock, DeepInfra, Fireworks, Novita, Parasail, Together |
| Kimi K3 | kimi-k3-baseten-chat | DeepInfra, Fireworks, Parasail, Together |
| MiniMax M2.5 | minimax-m2.5-baseten-chat | DeepInfra, Fireworks, Novita, Parasail, Together |
| Nemotron Ultra | nemotron-ultra-baseten-chat | DeepInfra, Nebius, OpenRouter |
| Qwen3 Coder 480B | qwen3-coder-480b-baseten-chat | DeepInfra, Fireworks, Nebius, Novita, Together, Vertex |

*6 of 9 models have insufficient monitoring data (recently onboarded). Analysis below focuses on the 3 with meaningful history.*

---

## Current Stability Scores (as of Aug 29, 2026)

Stability scores range from 0.0 to 1.0, measuring behavioral consistency over a trailing 72-hour window. Above 0.9 = stable. Below 0.75 = significant shift detected.

### GPT-OSS-120B — Provider Comparison

| Provider | Stability Score | Rating |
|----------|:-:|--------|
| Azure | 1.000 | 🟢 Excellent |
| **Baseten** | **0.967** | **🟢 Stable** |
| Bedrock | 1.000 | 🟢 Excellent |
| DeepInfra | 0.886 | 🟡 Moderate |
| Fireworks | 1.000 | 🟢 Excellent |
| Nebius | 1.000 | 🟢 Excellent |
| Novita | 0.833 | 🟡 Moderate |
| OpenRouter | 0.975 | 🟢 Stable |
| Parasail | 0.967 | 🟢 Stable |
| Together | 0.663 | 🔴 Unstable |

**Baseten ranks solidly mid-pack on stability** — on par with OpenRouter and Parasail, behind the hyperscalers (Azure, Bedrock) and Fireworks.

### Kimi K3 — Provider Comparison

| Provider | Stability Score | Rating |
|----------|:-:|--------|
| **Baseten** | **1.000** | **🟢 Excellent** |
| DeepInfra | 0.886 | 🟡 Moderate |
| Fireworks | 0.567 | 🔴 Unstable |
| Parasail | 0.957 | 🟢 Stable |
| Together | 1.000 | 🟢 Excellent |

**Baseten is top-tier here**, tied with Together for the highest stability score.

### Nemotron Ultra — Provider Comparison

| Provider | Stability Score | Rating |
|----------|:-:|--------|
| **Baseten** | **1.000** | **🟢 Excellent** |
| DeepInfra | 1.000 | 🟢 Excellent |
| Nebius | 0.833 | 🟡 Moderate |

**Baseten ties for best**, matching DeepInfra.

---

## Divergence: Does Baseten Serve the Same Model?

Divergence ratios measure how much a provider's outputs differ from the consensus of other providers serving the same weights. Near 1.0 = aligned with consensus. Well above 1.0 = the provider's outputs differ notably. Higher divergence doesn't necessarily indicate a problem — it can reflect different quantization schemes, batching strategies, or serving optimizations that are equally valid but produce distinct output distributions.

### GPT-OSS-120B — 90-Day Divergence Summary

| Provider | Avg Divergence | Min | Max | Assessment |
|----------|:-:|:-:|:-:|------------|
| OpenRouter | 0.46 | -0.33 | 1.76 | Closest to consensus |
| Bedrock | 0.75 | 0.04 | 1.95 | Near consensus |
| Parasail | 0.78 | 0.14 | 1.89 | Near consensus |
| Azure | 0.79 | 0.09 | 1.47 | Near consensus |
| Nebius | 0.86 | 0.14 | 1.59 | Near consensus |
| Together | 1.06 | 0.02 | 4.10 | At consensus |
| DeepInfra | 1.35 | 0.46 | 3.64 | Moderate divergence |
| Novita | 1.81 | -0.02 | 3.82 | Notable divergence |
| **Baseten** | **3.58** | **1.84** | **7.16** | **High divergence** |
| Fireworks | 4.10 | 1.96 | 9.05 | Highest divergence |

**Baseten's GPT-OSS-120B outputs differ significantly from the provider consensus** — second only to Fireworks. This likely reflects different serving optimizations (quantization, batching, inference engine). Whether this divergence matters depends on the use case: for applications that need reproducibility across providers, it's worth noting; for applications that just need quality and consistency from a single provider, Baseten's high stability score matters more than its divergence.

### Nemotron Ultra — 75-Day Divergence Summary

| Provider | Avg Divergence | Min | Max | Assessment |
|----------|:-:|:-:|:-:|------------|
| DeepInfra | 0.88 | 0.48 | 1.32 | Closest to consensus |
| Nebius | 1.45 | 0.51 | 2.78 | Moderate divergence |
| **Baseten** | **3.61** | **0.87** | **9.04** | **High divergence** |

**Same pattern**: Baseten serves the model stably, but its output distribution differs from the other providers. With only 3 providers in the comparison set, the "consensus" is thin — Baseten may simply be using a different (not worse) optimization approach.

### Kimi K3 — Early Divergence (3 days of data)

| Provider | Avg Divergence | Assessment |
|----------|:-:|------------|
| **Baseten** | **0.32** | **Closest to consensus** |
| Parasail | 0.42 | Near consensus |
| DeepInfra | 0.73 | Near consensus |
| Together | 1.41 | Moderate divergence |
| Fireworks | 7.65 | High divergence |

Early data suggests Baseten's Kimi K3 serving is well-aligned with consensus (though only 3 days of data).

---

## Has Baseten Improved Over Time?

Monthly stability trend for `gpt-oss-120b-baseten-chat` (7 months of data):

| Month | Avg Stability | Avg Divergence | Trend |
|-------|:-:|:-:|-------|
| Feb 2026 | 0.962 | 3.41 | Baseline |
| Mar 2026 | 0.964 | 2.91 | Divergence improving ↓ |
| Apr 2026 | 0.963 | 2.24 | Best divergence month ↓↓ |
| May 2026 | 0.988 | 3.07 | Stability jump ↑, divergence regressed |
| Jun 2026 | 0.977 | 3.58 | Stable, divergence back up |
| Jul 2026 | 0.978 | 3.64 | Holding steady |
| Aug 2026 | 0.989 | 3.51 | Best stability month ↑ |

**Stability has modestly improved** — from 0.962 in Feb to 0.989 in Aug 2026. However, **divergence has not improved**: after a promising dip to 2.24 in April, it regressed back to 3.5+ where it's remained since June. This suggests Baseten may be using different model configurations (quantization, batching, or custom serving optimizations) that remain stable over time but produce outputs that differ from the broader provider consensus.

### Nemotron Ultra on Baseten (3 months)

| Month | Avg Stability | Avg Divergence |
|-------|:-:|:-:|
| Jun 2026 | 1.000 | 8.20 |
| Jul 2026 | 1.000 | 1.44 |
| Aug 2026 | 0.994 | 3.38 |

Divergence dropped dramatically from June to July (potentially a config fix), but has crept back up.

---

## Key Takeaways

1. **Baseten's stability is competitive.** Across all models with data, Baseten scores 0.967–1.000, placing it in the "stable" to "excellent" range. It's not the best (hyperscalers like Bedrock consistently hit 1.000), but it's reliably above 0.9.

2. **Baseten's outputs diverge from the provider consensus on 2 of 3 models.** This means Baseten produces different output distributions from the majority of other providers serving the same weights. This likely reflects different quantization, serving engines, or optimization choices — not necessarily better or worse quality. Divergence is most relevant for use cases requiring cross-provider reproducibility; for single-provider deployments where consistency over time matters, stability scores are the more meaningful metric.

3. **Modest improvement over 7 months.** Stability scores have trended up (~3% gain). Divergence dipped in spring 2026 but returned to prior levels. This suggests Baseten has improved *consistency* (fewer behavioral shifts over time) while maintaining their own serving configuration — they're not converging toward other providers' approaches, which may be a deliberate choice.

4. **Fireworks shows a similar divergence pattern.** Fireworks has even higher divergence on GPT-OSS-120B, suggesting providers that invest in custom serving optimizations tend to diverge from the consensus of providers using more standard configurations. This is a natural outcome — providers optimizing for throughput, latency, or cost-efficiency may trade off exact output alignment with other providers.

5. **Too early to judge on most models.** 6 of 9 Baseten endpoints lack sufficient data. As more monitoring data accumulates, the picture will become clearer.

---

## Methodology

- **Data source:** [VAIL Stability Arena](https://arena.projectvail.com) API
- **Stability scores:** Behavioral consistency measured over a trailing 72-hour window (0.0–1.0 scale). Based on response fingerprinting across standardized evaluation prompts.
- **Divergence ratios:** Daily measure of how much one provider's outputs differ from the consensus of all other providers serving the same model. Near 1.0 = aligned, >1.0 = diverging.
- **Monitoring period:** February 6 – August 29, 2026 (GPT-OSS-120B), June–August 2026 (Nemotron Ultra), August 2026 (Kimi K3).

*Analysis by [Project VAIL](https://projectvail.com) — Verifiable AI Layer*
