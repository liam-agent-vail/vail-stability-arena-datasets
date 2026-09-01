# Parasail Inference Stability: How Does It Compare?

**An analysis of Parasail's serving stability, output divergence, latency, and error rates vs. other inference providers using [VAIL Stability Arena](https://arena.projectvail.com) data.**

*Generated: September 1, 2026 — companion to the Baseten provider analysis*

---

## TL;DR

Parasail serves **15 models** in the Stability Arena — the widest independent-provider footprint we've profiled. Across models with sufficient data, Parasail is best characterized as the **mirror image of Baseten**:

- **Stability:** Strong to excellent. Parasail is top-tier or tied-for-top on most of its actively-served models (gpt-oss-120b 1.000, deepseek-v4 1.000, trinity 0.975), with a couple of weak spots (qwen3-235b 0.331).
- **Divergence:** **Consensus-aligned.** Where Baseten's outputs diverged sharply from the provider consensus (3.2–3.6), Parasail sits near or just above 1.0 on almost every model with divergence data — one of the *most* consensus-aligned providers on gpt-oss-120b (0.72). The exception is gemma-4-26b-a4b (4.63).
- **Latency:** **Mid-pack, and often the fastest independent** on ~200B-class models — but not the dramatic 5–20× speed leader Baseten is. Parasail is #1 of its group on 5 models, but slower than the hyperscalers/Baseten on the largest.
- **Error rates:** **Parasail's clear weak spot.** On several models Parasail carries meaningfully higher error rates than the field. Full-window rates are inflated by end-of-life windows on deprecated endpoints, but even the monthly trend shows Parasail runs hotter on errors than the low-error leaders (Baseten, Fireworks, Bedrock).

Net: Parasail is a **stable, consensus-faithful, reasonably fast** provider whose main reliability gap is **error rate**, not behavioral drift.

---

## Models Parasail Serves in the Arena

Parasail has 16 monitored endpoints (15 currently in the Arena stability set; `kimi-k2.6` is a superseded version). **6 are actively served**; the rest are older model generations Parasail has rotated out.

| Model | Active | Parasail stability | Parasail divergence | Parasail p50 | Providers | Stability days |
|---|:-:|:-:|:-:|:-:|:-:|:-:|
| gpt-oss-120b | ✅ | 1.000 | 0.72 | 970s | 14 | 207 |
| deepseek-v4 | ✅ | 1.000 | 1.05 | 3,075s | 6 | 72 |
| trinity-large-thinking | ✅ | 0.975 | — | 2,473s | 2 | 132 |
| glm-5.2 | ✅ | 0.814 | 1.03 | 2,364s | 6 | 48 |
| gemma-4-26b-a4b | ✅ | 0.814 | 4.63 | 2,520s | 4 | 76 |
| kimi-k3 | ✅ | 0.814* | 0.45 | 5,064s | 5 | 4 |
| kimi-k2.5 | ⚪️ | 0.933 | — | 4,620s | 7 | 83 |
| glm-5.1 | ⚪️ | 1.000 | — | 5,812s | 6 | 86 |
| minimax-m2.5 | ⚪️ | 1.000 | — | 4,453s | 6 | 41 |
| glm-4.7 | ⚪️ | 1.000 | — | 4,157s | 8 | 36 |
| glm5 | ⚪️ | 1.000 | — | 10,314s | 9 | 32 |
| gemma-4-31b | ⚪️ | 0.900 | — | 3,219s | 6 | 34 |
| deepseek-v3.2 | ⚪️ | 0.814 | — | 8,765s | 9 | 57 |
| qwen3-235b | ⚪️ | 0.331 | — | 1,365s | 8 | 35 |
| kimi-k2-instruct | ⚪️ | 0.386* | — | 1,134s | 8 | 10 |

*`*` = thin data (kimi-k3 has 4 days; kimi-k2-instruct 10). ✅ = actively served; ⚪️ = deprecated/rotated out.*

The deepest comparisons are **gpt-oss-120b** (7 months, 14 providers) and **deepseek-v4**, **glm-5.2**, **gemma-4-26b-a4b**, **trinity** (active with meaningful history).

---

## Current Stability & Full Metrics by Model

Stability scores range 0.0–1.0 over a trailing 72-hour window (>0.9 stable, <0.75 = significant shift). Stability shown is the most recent daily score with sufficient data. Latency (p50/p95 of fingerprint generation time) and error rate come from the Identity Monitor DB over Feb 1 – Sep 1, 2026. Rows sorted by stability.

### gpt-oss-120b — the flagship comparison (14 providers, 7 months)

| Provider | Stability | Divergence | p50 | p95 | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| azure | 1.000 | 0.97 | 457s | 1,704s | 4.82% |
| bedrock | 1.000 | 0.77 | 877s | 1,693s | 0.30% |
| fireworks | 1.000 | 3.67 | 3,123s | 8,809s | 0.07% |
| groq | 1.000 | — | 5,623s | 9,858s | 0.00% |
| novita | 1.000 | 1.31 | 2,641s | 7,865s | 3.66% |
| **parasail** | **1.000** | **0.72** | **970s** | **4,086s** | **3.74%** |
| vertex | 1.000 | 0.50 | 1,171s | 3,075s | 28.70% |
| openrouter | 0.975 | 0.53 | 4,258s | 9,347s | 3.82% |
| baseten | 0.957 | 3.19 | 732s | 3,194s | 0.13% |
| nebius | 0.957 | 0.86 | 1,085s | 6,957s | 0.58% |
| deepinfra | 0.850 | 1.22 | 4,404s | 8,884s | 1.33% |
| openrouter-exacto | 0.850 | — | 3,015s | 9,212s | 11.49% |
| together | 0.225 | 1.11 | 3,366s | 9,666s | 1.48% |

**Read:** Parasail is a standout on gpt-oss-120b — **1.000 stability, the 2nd-lowest divergence (0.72) of any provider**, and **#4 fastest of 13** on p50 (behind only Azure, Baseten, Bedrock). Its one blemish is a 3.74% error rate — middling, well above Baseten (0.13%) and Bedrock (0.30%) but far better than Vertex (28.7%). This is the cleanest example of the Parasail profile: fast + stable + faithful to consensus, with error rate as the soft spot.

### deepseek-v4 — Parasail is the stability leader

| Provider | Stability | Divergence | p50 | p95 | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| **parasail** | **1.000** | **1.05** | **3,075s** | **6,959s** | **66.93%** |
| together | 1.000 | 1.15 | 2,632s | 5,069s | 31.05% |
| fireworks | 0.814 | — | 2,670s | 5,601s | 2.13% |
| deepinfra | 0.300 | 7.41 | 2,332s | 5,059s | 0.84% |
| novita | 0.100 | 1.25 | 2,900s | 3,862s | 0.50% |
| openrouter | 0.100 | 0.50 | 3,393s | 5,600s | 0.00% |

**Read:** Parasail (and Together) hold perfect stability while deepinfra/novita/openrouter collapse (0.10–0.30) — Parasail is serving deepseek-v4 far more consistently than most of the field, and its outputs are consensus-aligned (1.05). But the **66.9% full-window error rate is alarming**. Digging into the monthly trend (below) shows this was a genuine reliability incident in Jun–Jul 2026 (74–77% error months) that Parasail cut to ~40% by August — still the worst active-endpoint error rate we see, and worth flagging to the provider.

### trinity-large-thinking — Parasail beats the only other provider

| Provider | Stability | Divergence | p50 | p95 | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| **parasail** | **0.975** | — | 2,473s | 4,340s | 20.87% |
| openrouter | 0.850 | — | 2,506s | 7,706s | 6.90% |

**Read:** Only Parasail and OpenRouter serve this model. Parasail is more stable (0.975 vs 0.850) and comparable on latency, but carries a higher error rate (20.9% vs 6.9%) — again driven by a June spike (46% that month) that settled to 6–11% after.

### glm-5.2

| Provider | Stability | Divergence | p50 | p95 | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| deepinfra | 1.000 | 0.76 | 5,567s | 10,395s | 0.26% |
| fireworks | 1.000 | 1.04 | 5,282s | 6,777s | 0.83% |
| together | 1.000 | 0.77 | 3,445s | 5,933s | 0.84% |
| **parasail** | **0.814** | **1.03** | **2,364s** | **3,721s** | **10.28%** |
| openrouter | 0.671 | 1.94 | 3,635s | 5,883s | 0.00% |
| novita | 0.243 | 1.13 | 6,308s | 9,077s | 0.26% |

**Read:** Here Parasail is the **fastest provider (p50 2,364s)** and consensus-aligned (1.03), but stability is only mid-pack (0.814) and error rate elevated (10.3%, though improving: 18%→4% Jul→Aug).

### gemma-4-26b-a4b — the divergence exception

| Provider | Stability | Divergence | p50 | p95 | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| deepinfra | 1.000 | 4.96 | 3,720s | 6,717s | 0.17% |
| openrouter | 1.000 | 0.41 | 2,952s | 5,841s | 0.00% |
| **parasail** | **0.814** | **4.63** | **2,520s** | **4,986s** | **7.75%** |
| novita | 0.671 | -0.06 | 3,739s | 5,598s | 3.83% |

**Read:** The one model where Parasail shows **elevated divergence (4.63)** — but it shares that with deepinfra (4.96), and the average is skewed by a single extreme outlier day (max 208). Parasail is the fastest provider here (2,520s).

*Full per-model tables for all 15 models — including deprecated endpoints — are in [`tables.md`](./tables.md).*

---

## Divergence: Does Parasail Serve the Same Model?

Divergence measures how much a provider's outputs differ from the consensus of others serving the same weights (near 1.0 = aligned, well above = notably different). Daily divergence metrics exist for 5 Parasail models:

| Model | Parasail divergence | Assessment | For contrast |
|---|:-:|---|---|
| kimi-k3 | 0.45 | ✅ Very aligned | fireworks 7.58 |
| gpt-oss-120b | 0.72 | ✅ Very aligned | baseten 3.19, fireworks 3.67 |
| glm-5.2 | 1.03 | ✅ Aligned | openrouter 1.94 |
| deepseek-v4 | 1.05 | ✅ Aligned | deepinfra 7.41 |
| gemma-4-26b-a4b | 4.63 | 🔴 Elevated (outlier-driven) | deepinfra 4.96 |

**This is the headline contrast with Baseten.** Baseten's story was "stable but high output divergence (3.2–3.6) — likely aggressive custom quantization." Parasail is the opposite: it tracks the provider consensus closely on 4 of 5 models. Parasail appears to run **standard, consensus-faithful configurations** rather than heavily-customized serving stacks.

---

## Workload Latency: Where Does Parasail Rank?

p50 of fingerprint generation time, Feb–Sep 2026. Lower = faster.

| Model | Parasail p50 | Rank | Fastest provider |
|---|:-:|:-:|:-:|
| glm-5.2 | 2,364s | **#1 of 6** | parasail |
| gemma-4-26b-a4b | 2,520s | **#1 of 4** | parasail |
| trinity-large-thinking | 2,473s | **#1 of 2** | parasail |
| glm-5.1 | 5,812s | **#1 of 6** | parasail |
| gemma-4-31b | 3,219s | **#1 of 5** | parasail |
| qwen3-235b | 1,365s | #3 of 7 | vertex (456s) |
| gpt-oss-120b | 970s | #4 of 13 | azure (457s) |
| kimi-k2.5 | 4,620s | #4 of 7 | baseten (689s) |
| minimax-m2.5 | 4,453s | #4 of 6 | baseten (2,980s) |
| glm-4.7 | 4,157s | #4 of 8 | baseten (391s) |
| kimi-k3 | 5,064s | #3 of 5 | baseten (2,561s) |
| deepseek-v4 | 3,075s | #5 of 6 | deepinfra (2,332s) |
| deepseek-v3.2 | 8,765s | #8 of 8 | vertex (2,349s) |
| glm5 | 10,314s | #9 of 9 | baseten (1,393s) |

**Read:** Parasail is **#1 in its group on 5 models** and top-4 on most others — genuinely competitive, and frequently the *fastest independent provider* on ~200B-class models. But unlike Baseten (which posts 5–20× speed advantages and near-always ranks #1), Parasail is **fast, not dominant**: on the very largest models and where hyperscalers/Baseten compete, it lands mid-pack, and it's the slowest on a couple of deprecated endpoints.

---

## Error Rates: Parasail's Weak Spot

Error rate = fingerprinting errors ÷ (successful fingerprints + errors), matching the Baseten methodology. **Caveat:** full-window rates on *deprecated* endpoints are inflated by end-of-life windows (the monitor keeps probing after the provider rotates a model out). The fair signal is the **monthly trend on active endpoints**.

Monthly error rate for the 6 actively-served Parasail endpoints:

| Model | Jun | Jul | Aug | Trend |
|---|:-:|:-:|:-:|---|
| gpt-oss-120b | 0.8% | 3.1% | 2.6% | Steady low-single-digits |
| gemma-4-26b-a4b | 20.5% | 4.3% | 2.6% | ✅ Improved sharply |
| glm-5.2 | — | 18.3% | 4.2% | ✅ Improved |
| deepseek-v4 | 77.0% | 74.4% | 40.4% | 🔴 Improving but still high |
| trinity-large-thinking | 46.2% | 6.4% | 11.5% | ⚠️ Recovered from spike |
| kimi-k3 | — | — | 13.0%† | Thin data |

*†kimi-k3 Aug; Sep sample too small to be meaningful.*

**Read:** Most active endpoints have converged to acceptable single-digit error rates by August, but Parasail clearly runs **hotter on errors than the low-error leaders** (Baseten, Fireworks, Bedrock routinely <0.5%). **deepseek-v4 is the standout concern** — a sustained high-error incident that's improving but was still 40% in August. This is the most actionable finding for the provider.

---

## Has Parasail Improved Over Time? (gpt-oss-120b, 7-month trend)

The one Parasail endpoint with a full 7-month history:

| Month | Avg stability | Avg divergence | p50 | p95 | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| Feb 2026 | 0.974 | 0.56 | 976s | 2,829s | 2.9% |
| Mar 2026 | 0.912 | 0.69 | 2,184s | 5,660s | 4.5% |
| Apr 2026 | 0.974 | 0.71 | 2,641s | 5,784s | 3.1% |
| May 2026 | 0.938 | 0.69 | 1,040s | 4,106s | 8.5% |
| Jun 2026 | 0.819 | 0.76 | 549s | 2,141s | 0.8% |
| Jul 2026 | 0.956 | 0.82 | 617s | 2,097s | 3.1% |
| Aug 2026 | 0.923 | 0.77 | **703s** | **1,344s** | 2.6% |

**Read:** The clearest improvement is **latency**: p50 fell from a spring peak of ~2,640s to ~550–700s (a ~4× speedup), and p95 tightened dramatically from 5,784s to 1,344s (Parasail's p95 is now among the best in the fleet). **Divergence stayed low and flat (0.56–0.82) the entire time** — Parasail never drifted from consensus, unlike Baseten whose divergence hovered at 3.5+. Stability bounced in a healthy 0.82–0.97 band, and error rate held in low single digits. So Parasail's gpt-oss-120b serving got substantially *faster* while remaining consistently *faithful* — the inverse of Baseten's "fast but divergent" pattern.

---

## Key Takeaways

1. **Parasail = the anti-Baseten on divergence.** It tracks the provider consensus closely (0.45–1.05 on 4 of 5 models), suggesting standard, un-customized serving configs. Where Baseten trades consensus-alignment for a heavily-optimized stack, Parasail keeps outputs faithful.

2. **Stability is strong on what it actively serves.** gpt-oss-120b (1.000), deepseek-v4 (1.000), trinity (0.975). Weak spots (qwen3-235b 0.331, kimi-k2-instruct 0.386) are on deprecated/thin-data endpoints.

3. **Fast, not dominant.** Parasail is the fastest independent provider on several ~200B-class models and top-4 on most, but doesn't post Baseten's 5–20× advantages and lands mid-pack on the largest models.

4. **Error rate is the real gap.** Parasail runs hotter on errors than the low-error leaders. Most active endpoints recovered to single digits by August, but **deepseek-v4 (40% in Aug) is a live reliability concern** worth raising with the provider.

5. **Broadest independent footprint.** 15 Arena models is the widest we've profiled — but 9 are deprecated older generations, so the actively-monitored, decision-grade set is really the 6 active endpoints.

---

## Methodology

- **Data sources:** [VAIL Stability Arena](https://arena.projectvail.com) API (stability + divergence) and the VAIL Identity Monitor database (latency via `fingerprint_telemetry.generation_time_seconds`; error rate via `fingerprinting_errors`).
- **Stability:** behavioral consistency over a trailing 72-hour window (0.0–1.0). "Current" stability = most recent daily score with ≥5 observations (single-point scores as of Sep 1 were null for many endpoints).
- **Divergence:** daily measure of output difference vs the consensus of all other providers serving the same model. Available for 5 Parasail models.
- **Latency:** p50/p95 of per-fingerprint generation time, Feb 1 – Sep 1, 2026. This is workload/generation latency, not first-token latency.
- **Error rate:** errors ÷ (successful fingerprints + errors) over the window, per endpoint. Full-window rates on deprecated endpoints are inflated by post-decommission probing; monthly trends give the fair picture for active endpoints.
- **Monitoring period:** February 1 – September 1, 2026.

*Analysis by [Project VAIL](https://projectvail.com) — Verifiable AI Layer. Companion to the Baseten provider stability analysis in this repo.*
