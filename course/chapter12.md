# Chapter 12 — Inference I: kv-cache

> Goal: understand generation-time behavior — why naive sampling recomputes everything, how the kv-cache fixes it, why inference is memory-bandwidth-bound, and how sampling strategies (temperature, top-k, top-p) shape output.

## Core path (study in order)

1. 🟢 [João Lages — Transformers KV Caching Explained](https://medium.com/@joaolages/kv-caching-explained-276520203249) — a short, animated explanation of exactly what gets cached and why it makes generation fast.
2. 🟡 [kipply — Transformer Inference Arithmetic](https://kipp.ly/transformer-inference-arithmetic/) — first-principles reasoning about inference: kv-cache size math, flops vs. memory-bandwidth boundedness, latency estimates. The single most valuable read of this chapter.
3. 🟡 [Holtzman et al. (2019) — The Curious Case of Neural Text Degeneration](https://arxiv.org/abs/1904.09751) — why greedy/beam decoding loops and repeats, and the nucleus (top-p) sampling fix; this is where your sampler settings come from.
4. 🟡 [karpathy/llama2.c](https://github.com/karpathy/llama2.c) — Llama-2 inference in ~700 lines of dependency-free C (`run.c`), kv-cache included. Read it end to end — it is the clearest complete picture of inference that exists. (Bonus: it trains and runs TinyStories models!)
5. 🔴 [Lilian Weng — Large Transformer Model Inference Optimization](https://lilianweng.github.io/posts/2023-01-10-inference-optimization/) — the survey that connects this chapter to the next: batching, distillation, sparsity, and more.

## Going deeper (optional)

- 🔴 [Kwon et al. (2023) — Efficient Memory Management for LLM Serving with PagedAttention (vLLM)](https://arxiv.org/abs/2309.06180) — virtual-memory-style paging for kv-caches; the idea behind the dominant open-source serving engine.
- 🔴 [Leviathan et al. (2022) — Fast Inference via Speculative Decoding](https://arxiv.org/abs/2211.17192) — use a small draft model to propose tokens the big model verifies in parallel.
- 🔴 [Shazeer (2019) — Fast Transformer Decoding: One Write-Head is All You Need (MQA)](https://arxiv.org/abs/1911.02150) and [Ainslie et al. (2023) — GQA](https://arxiv.org/abs/2305.13245) — shrinking the kv-cache by sharing key/value heads; used by Llama and most modern models.

## Exercises & projects

- 🟢 Implement temperature, top-k, and top-p sampling for your Storyteller and build a small comparison grid: same prompt, different settings, observe degeneration vs. incoherence at the extremes.
- 🟡 **Storyteller milestone:** add a kv-cache to your nanoGPT `generate()` (nanoGPT famously doesn't have one). Benchmark tokens/sec with and without, at several context lengths, and plot the speedup.
- 🟡 Verify kipply's math on your own model: predict kv-cache bytes per token from your model config, then measure actual GPU memory growth during generation.
- 🔴 Train a TinyStories model with llama2.c's `train.py` (or export your own to its format) and run it with `run.c`; then read `run.c` and annotate every kv-cache line.
- 🔴 Implement speculative decoding with your small char-model as drafter for a bigger model — measure acceptance rate and speedup.

---
[← Datasets](chapter11.md) | [Index](../COURSE.md) | [Next: Inference II: Quantization →](chapter13.md)
