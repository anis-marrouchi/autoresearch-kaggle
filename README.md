# Autoresearch for Kaggle 🧬

> Adapting [karpathy/autoresearch](https://github.com/karpathy/autoresearch) for Kaggle competitions with remote GPU constraints.

## The Challenge

Karpathy's autoresearch runs experiments locally on a single GPU with a tight 5-minute loop — ~12 experiments/hour. Kaggle competitions require remote execution (30-60 min per run), limited GPU sessions (max 2 concurrent), and async score retrieval. How do you run autonomous research when each experiment takes 30x longer?

## Our Approach

We're competing in [Stanford RNA 3D Folding 2](https://www.kaggle.com/competitions/stanford-rna-3d-folding-2) ($75K prize pool, deadline March 25, 2026) using an autonomous research loop powered by [OpenClaw](https://github.com/openclaw/openclaw) + Kaggle API.

### Key Adaptations

| Aspect | Original | Kaggle Adaptation |
|--------|----------|-------------------|
| Execution | Local GPU, 5 min | Remote Kaggle, 30-60 min |
| Loop speed | ~12/hour | ~2/hour (2 GPU slots) |
| Score | grep stdout | Kaggle Submissions API |
| Keep/discard | git commit/reset | experiments.json state |
| Loop driver | Claude session | OpenClaw cron (hourly) |
| Pre-screening | N/A | Local simulator (~40s) |

### Results

| Version | Score | Change | Status |
|---------|-------|--------|--------|
| v5 | 0.087 | Baseline (helix only) | ❌ |
| v12 | 0.378 | TBM + Protenix (pid≥50) | ✅ Best |
| v14 | 0.345 | Lowered pid to 30 | ❌ Regression |
| v15+ | pending | Optimized routing | ⏳ |

## Links

- 🏆 [Competition](https://www.kaggle.com/competitions/stanford-rna-3d-folding-2)
- 📓 [Our Notebook](https://www.kaggle.com/code/anismarrouchi/stanford-rna-3d-folding-2-baseline-v1)
- 🔬 [Original autoresearch](https://github.com/karpathy/autoresearch)
- 🤖 [OpenClaw](https://github.com/openclaw/openclaw)
- 🌐 [Noqta.tn](https://noqta.tn)

## License

MIT
