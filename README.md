# Maxim Maximov

Math & CS student at Saint Petersburg State University · Deep Learning · RecSys · Graph ML · LLM Agents

Building and breaking ML systems — recommenders, graph models, boosting pipelines — to find where a good metric stops being honest.

## Stack

**Used in projects:** Python, PyTorch, PyTorch Geometric, scikit-learn, XGBoost,
CatBoost, LightGBM, NumPy, Pandas, pyarrow, Optuna, SHAP, Git, Docker, FastAPI, Ollama, C++

**Worked with:** SQL (PostgreSQL), Kafka, Airflow, Linux, CI/CD (GitHub Actions), LangGraph

## Projects

### [SASRec on Yandex Yambda](https://github.com/mmmaximov/sasrec-yambda)
Decoder-only transformer for sequential recommendation, trained on 881K events from Yandex Music. Causal self-attention implemented from scratch; track audio embeddings are quantized into semantic IDs via RQ-VAE, turning recommendation into generative retrieval — the vocabulary collapses from 181K items to 1,026 tokens, making the model 45x lighter.

- NDCG@10 of 0.575 for the hybrid vs. 0.413 for standard item embeddings.
- Pure generative retrieval collapses (0.181) — per-position perplexity explains why: RQ-VAE was trained to reconstruct audio, so only the first of four quantization levels is predictable from behavior.
- Found a metric bug: the last-item baseline showed HitRate@10 = 1.0 due to rank ties; after a fair tie-break, it dropped to 0.0145.

### AML Detection on Transaction Graph
Money-laundering detection on 5M transactions with a 1:1122 class imbalance. Transfer graph topology compressed into 86 features via sliding windows over prefix sums: `searchsorted` instead of `groupby().rolling()`, which doesn't fit in memory — 40 seconds for 497K accounts.

- PR-AUC of 0.348 vs. 0.011 for the naive baseline, 0.462 on holdout, Precision@100 = 0.84.
- Error analysis by scheme type: star-shaped schemes caught at recall 0.53–0.62, chain schemes at 0.25–0.32 — the boundary tracks topology, since all features are limited to a one-hop neighborhood.
- Feature-group ablation diverged from gain-based importances: the receiver side contributes twice as much as XGBoost's importances would suggest.

### [Geometric Deep Learning for Molecular Tensors](https://github.com/mmmaximov/equivariant-molecular-tensors)
SO(3)-equivariant prediction of vector and tensor quantities: symmetry is built into the architecture rather than learned from augmentations. SchNet plus rank-1 and rank-2 heads, on QM9S.

- MAE of 0.038 D vs. 0.639 for a larger fully-connected network.
- Equivariance verified numerically on the untrained model.
- Three-seed ablation: topological features are useless, since they lie in the kernel of the group action.

## Competitions

| Competition | Result |
|---|---|
| MTS True Tech Hack, LocalScript | 19 / 131 |
| RWB WildHack, warehouse logistics automation (team track) | 35 / 443 |
| RWB WildHack, downtime-free shipments (individual track) | 125 / 672 |
| Yandex ML Challenge, Long Tour | 121 / 630 |
| Changellenge Cup IT, data analysis | HQA 15% |

## Education

- Saint Petersburg State University, Faculty of Mathematics and Mechanics, "Mathematics and Computer Science" — 2nd year, 2025–2029
- Deep Learning School, MIPT — 2025
- Agents Week, YSDA (Yandex) intensive — 2026

## Notes

The most interesting moment in ML, for me, is when a model hits a ceiling — and it turns out the problem isn't its size, but how the object is described. Three projects in a row, I ended up at exactly that point, each time from a different angle.

Interests: graph methods, deep learning, LLM agents.

## Contact

[Telegram](https://t.me/maximovmm) · [mmworkmaildaaa@gmail.com](mailto:mmworkmaildaaa@gmail.com)
