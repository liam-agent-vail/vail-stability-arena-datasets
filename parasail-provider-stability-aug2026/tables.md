### gpt-oss-120b
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| azure | 1.000 | 0.97 | 457s | 1,704s | 4.82% |
| bedrock | 1.000 | 0.77 | 877s | 1,693s | 0.30% |
| fireworks | 1.000 | 3.67 | 3,123s | 8,809s | 0.07% |
| groq | 1.000 | — | 5,623s | 9,858s | 0.00% |
| novita | 1.000 | 1.31 | 2,641s | 7,865s | 3.66% |
| **parasail** | **1.000** | 0.72 | 970s | 4,086s | 3.74% |
| vertex | 1.000 | 0.50 | 1,171s | 3,075s | 28.70% |
| openrouter | 0.975 | 0.53 | 4,258s | 9,347s | 3.82% |
| baseten | 0.957 | 3.19 | 732s | 3,194s | 0.13% |
| nebius | 0.957 | 0.86 | 1,085s | 6,957s | 0.58% |
| deepinfra | 0.850 | 1.22 | 4,404s | 8,884s | 1.33% |
| openrouter-exacto | 0.850 | — | 3,015s | 9,212s | 11.49% |
| together | 0.225 | 1.11 | 3,366s | 9,666s | 1.48% |
| sambanova | n/a | — | n/a | n/a | 100.00% |

### deepseek-v4
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| **parasail** | **1.000** | 1.05 | 3,075s | 6,959s | 66.93% |
| together | 1.000 | 1.15 | 2,632s | 5,069s | 31.05% |
| fireworks | 0.814 | — | 2,670s | 5,601s | 2.13% |
| deepinfra | 0.300 | 7.41 | 2,332s | 5,059s | 0.84% |
| novita | 0.100 | 1.25 | 2,900s | 3,862s | 0.50% |
| openrouter | 0.100 | 0.50 | 3,393s | 5,600s | 0.00% |

### trinity-large-thinking
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| **parasail** | **0.975** | — | 2,473s | 4,340s | 20.87% |
| openrouter | 0.850 | — | 2,506s | 7,706s | 6.90% |

### glm-5.2
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| deepinfra | 1.000 | 0.76 | 5,567s | 10,395s | 0.26% |
| fireworks | 1.000 | 1.04 | 5,282s | 6,777s | 0.83% |
| together | 1.000 | 0.77 | 3,445s | 5,933s | 0.84% |
| **parasail** | **0.814** | 1.03 | 2,364s | 3,721s | 10.28% |
| openrouter | 0.671 | 1.94 | 3,635s | 5,883s | 0.00% |
| novita | 0.243 | 1.13 | 6,308s | 9,077s | 0.26% |

### gemma-4-26b-a4b
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| deepinfra | 1.000 | 4.96 | 3,720s | 6,717s | 0.17% |
| openrouter | 1.000 | 0.41 | 2,952s | 5,841s | 0.00% |
| **parasail** | **0.814** | 4.63 | 2,520s | 4,986s | 7.75% |
| novita | 0.671 | -0.06 | 3,739s | 5,598s | 3.83% |

### kimi-k2.5
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| baseten | 1.000 | — | 689s | 3,617s | 4.81% |
| deepinfra | 1.000 | — | 8,678s | 19,604s | 15.16% |
| fireworks | 1.000 | — | 5,029s | 12,467s | 1.13% |
| **parasail** | **0.933** | — | 4,620s | 8,056s | 22.50% |
| together | 0.900 | — | 6,969s | 13,997s | 5.02% |
| bedrock | 0.600 | — | 998s | 5,226s | 0.73% |
| novita | 0.225 | — | 3,194s | 9,681s | 0.00% |

### glm-5.1
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| deepinfra | 1.000 | — | 6,595s | 14,432s | 0.00% |
| **parasail** | **1.000** | — | 5,812s | 13,608s | 44.63% |
| together | 1.000 | — | 6,153s | 13,490s | 32.96% |
| openrouter | 0.700 | — | 8,047s | 13,578s | 15.93% |
| novita | 0.683 | — | 8,249s | 10,585s | 13.45% |
| fireworks | 0.600 | — | 6,944s | 15,096s | 0.00% |

### minimax-m2.5
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| fireworks | 1.000 | — | 4,155s | 7,317s | 0.00% |
| **parasail** | **1.000** | — | 4,453s | 7,789s | 4.80% |
| together | 1.000 | — | 3,499s | 7,358s | 2.38% |
| novita | 0.933 | — | 6,400s | 12,233s | 0.00% |
| baseten | 0.918 | — | 2,980s | 6,961s | 0.00% |
| deepinfra | 0.656 | — | 6,288s | 11,739s | 1.21% |

### glm-4.7
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| deepinfra | 1.000 | — | 14,754s | 25,063s | 10.57% |
| nebius | 1.000 | — | 11,698s | 14,382s | 4.57% |
| novita | 1.000 | — | 2,978s | 8,724s | 0.00% |
| **parasail** | **1.000** | — | 4,157s | 6,457s | 4.45% |
| vertex | 1.000 | — | 1,889s | 2,876s | 31.28% |
| together | 0.814 | — | 6,856s | 14,557s | 0.00% |
| fireworks | 0.671 | — | 5,186s | 14,669s | 0.00% |
| baseten | 0.177 | — | 391s | 1,799s | 0.00% |

### glm5
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| fireworks | 1.000 | — | 5,200s | 8,606s | 0.00% |
| novita | 1.000 | — | 9,194s | 14,741s | 0.00% |
| **parasail** | **1.000** | — | 10,314s | 14,246s | 40.55% |
| vertex | 1.000 | — | 3,007s | 3,388s | 88.00% |
| deepinfra | 0.989 | — | 6,598s | 12,238s | 8.40% |
| together | 0.957 | — | 6,895s | 10,568s | 7.72% |
| nebius | 0.933 | — | 5,790s | 11,284s | 0.00% |
| openrouter | 0.850 | — | 6,948s | 10,902s | 3.69% |
| baseten | 0.300 | — | 1,393s | 6,462s | 8.61% |

### qwen3-235b
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| together | 1.000 | — | 1,518s | 5,800s | 0.00% |
| nebius | 0.975 | — | 925s | 5,008s | 4.49% |
| deepinfra | 0.957 | — | 4,196s | 11,981s | 9.60% |
| fireworks | 0.900 | — | 5,197s | 9,834s | 42.55% |
| vertex | 0.900 | — | 456s | 1,737s | 10.68% |
| novita | 0.475 | — | 2,068s | 5,207s | 0.56% |
| **parasail** | **0.331** | — | 1,365s | 2,658s | 2.01% |
| sambanova | n/a | — | n/a | n/a | 100.00% |

### gemma-4-31b
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| deepinfra | 1.000 | — | 3,517s | 6,138s | 1.09% |
| together | 1.000 | — | 18,793s | 40,784s | 5.88% |
| **parasail** | **0.900** | — | 3,219s | 6,518s | 88.75% |
| novita | 0.600 | — | 3,987s | 8,157s | 55.25% |
| openrouter | 0.433 | — | 5,372s | 10,142s | 19.33% |
| fireworks | n/a | — | n/a | n/a | 100.00% |

### deepseek-v3.2
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| azure | 1.000 | — | 2,780s | 8,169s | 6.11% |
| bedrock | 1.000 | — | 2,633s | 6,248s | 2.53% |
| nebius | 1.000 | — | 4,186s | 6,984s | 5.06% |
| vertex | 1.000 | — | 2,349s | 3,208s | 65.42% |
| fireworks | 0.957 | — | 4,169s | 10,173s | 2.83% |
| deepinfra | 0.933 | — | 8,535s | 12,626s | 0.84% |
| **parasail** | **0.814** | — | 8,765s | 19,294s | 47.19% |
| novita | 0.100 | — | 3,559s | 8,073s | 0.00% |
| sambanova | n/a | — | n/a | n/a | 100.00% |

### kimi-k2-instruct
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| groq | 1.000 | — | 4,757s | 6,063s | 1.82% |
| nebius | 1.000 | — | 4,288s | 5,256s | 19.51% |
| novita | 1.000 | — | 3,419s | 6,054s | 4.88% |
| baseten | 0.957 | — | 706s | 1,873s | 0.00% |
| together | 0.767 | — | 1,789s | 4,245s | 0.00% |
| fireworks | 0.600 | — | 1,435s | 4,850s | 0.00% |
| **parasail** | **0.386** | — | 1,134s | 1,950s | 14.10% |
| deepinfra | 0.100 | — | 2,521s | 6,037s | 0.00% |

### kimi-k3
| Provider | Stability | Divergence (avg) | p50 latency | p95 latency | Error rate |
|---|:-:|:-:|:-:|:-:|:-:|
| baseten | 1.000 | 0.32 | 2,561s | 2,931s | 86.67% |
| together | 1.000 | 1.32 | 6,741s | 10,173s | 0.00% |
| deepinfra | 0.957 | 0.79 | 9,268s | 14,995s | 0.00% |
| **parasail** | **0.814** | 0.45 | 5,064s | 8,045s | 33.33% |
| fireworks | 0.475 | 7.58 | 4,493s | 6,644s | 3.85% |

