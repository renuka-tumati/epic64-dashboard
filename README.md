# Bug Epic #64 agent-factory run: tokens, cost and waste

Source: https://github.com/armandodollia-slalom/AI-Immersion-eShop/pull/96 · run 04:17–11:03 CST · human rate $220/h

| Metric | Value |
|---|---|
| Human cost (6.77 run h × $220) | $1,489 |
| Agent tokens | 58,261,637 |
| Agent token cost | $46.38 (184 runs) |
| **Total cost** | **$1,536** |
| Per verified ticket | 5.30M tokens · $4.22 |
| Cost per successful heal | $4.26 |

## Waste from model hand-offs and rework

| Category | Tokens | Token $ | Eng. time | Eng. $ @ $220/h | Total $ |
|---|---:|---:|---:|---:|---:|
| Sonnet output rejected → redone | 5.88M | $3.13 | 0.81 h | $177 | $180 |
| Opus output rejected → redone | 3.33M | $2.05 | 0.24 h | $52 | $54 |
| Copilot → Claude switch redo | 4.20M | $1.97 | 0.31 h | $67 | $69 |
| Failed / timed-out runs | 0.00M | $0.00 | 0.55 h | $120 | $120 |
| Pipeline restart re-runs (D6) | 1.62M | $1.30 | 0.12 h | $26 | $27 |
| Quota outage stall | 0.00M | $0.00 | 0.57 h | $125 | $125 |
| **Total** | **15.0M** | **$8.45** | **2.6 h** | **$568** | **$576** |

Opus PR-check caught 2 blocking and 2 major findings after Sonnet gates passed (30 upheld total).

Interactive dashboard: download `epic64-dashboard.html` from this gist (Raw → Save as) and open it in a browser. Raw data: `metrics.json`, `metrics.csv`.

_Measured from .agent-metrics on 5 pushed group branches: 11 of 13 verified tickets. All-worktree checkpoint at 10:18 was $52.48 / 235 runs. Engineering waste = rework agent time + 34 min outage, x rate (upper bound; some rework ran in parallel)._