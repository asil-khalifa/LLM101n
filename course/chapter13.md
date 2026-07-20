# Chapter 13 — Inference II: Quantization

> Goal: understand how models get compressed from fp16 to int8/int4 (and weirder) — the difference between symmetric/asymmetric, weight-only vs. weight+activation, and post-training methods like GPTQ and AWQ — so big models run on small machines.

## Core path (study in order)

1. 🟢 [Maarten Grootendorst — A Visual Guide to Quantization](https://www.maartengrootendorst.com/blog/quantization/) — 50+ diagrams covering the entire landscape: number formats, symmetric vs. asymmetric quantization, calibration, GPTQ, GGUF, BitNet. The perfect chapter backbone.
2. 🟡 [Hugging Face — Quantization docs](https://huggingface.co/docs/transformers/quantization) — the practical map of what you can actually run today (bitsandbytes, GPTQ, AWQ...) and how to load quantized models.
3. 🟡 [Dettmers et al. (2022) — LLM.int8()](https://arxiv.org/abs/2208.07339) — the first big-model int8 method, plus [Dettmers' blog on emergent outlier features](https://timdettmers.com/2022/08/17/llm-int8-and-emergent-features/) — why naive int8 breaks at scale and what to do about it.
4. 🟡 [llama.cpp](https://github.com/ggml-org/llama.cpp) — the project that made local LLMs a thing. Skim the README's quantization section and the GGUF quant types (Q4_K_M and friends) you'll use in the exercises.

## Going deeper (optional)

- 🔴 [Frantar et al. (2022) — GPTQ: Accurate Post-Training Quantization for GPT](https://arxiv.org/abs/2210.17323) — one-shot 3–4 bit weight quantization via approximate second-order information.
- 🔴 [Lin et al. (2023) — AWQ: Activation-aware Weight Quantization](https://arxiv.org/abs/2306.00978) — protect the ~1% of salient weights that activations say matter.
- 🔴 [Xiao et al. (2022) — SmoothQuant](https://arxiv.org/abs/2211.10438) — migrating quantization difficulty from activations to weights so W8A8 works.
- 🔴 [Ma et al. (2024) — The Era of 1-bit LLMs (BitNet b1.58)](https://arxiv.org/abs/2402.17764) — every weight is {-1, 0, 1}; a fun frontier read on how far compression might go.
- 🟡 [bitsandbytes](https://github.com/bitsandbytes-foundation/bitsandbytes) — the library behind 8-bit/4-bit loading (and the QLoRA machinery you'll meet next chapter).

## Exercises & projects

- 🟢 Implement absmax (symmetric) and zero-point (asymmetric) int8 quantization of a weight matrix in a notebook; measure quantization error, and compare per-tensor vs. per-channel scales.
- 🟡 **Storyteller milestone:** weight-only-quantize your trained model to int8 by hand (quantize weights, dequantize in the forward pass). Measure perplexity on held-out TinyStories and file size vs. the fp16 original. Then try int4 and watch quality drop.
- 🟡 Take a small open model (e.g., TinyLlama), convert to GGUF, and produce Q8_0 / Q4_K_M / Q2_K variants with llama.cpp's `llama-quantize`; compare size, speed, and output quality on the same prompts.
- 🔴 Plot a histogram of activation magnitudes per channel in a small transformer and find outlier channels — reproducing the observation that motivates LLM.int8() and SmoothQuant.
- 🔴 Implement a minimal GPTQ (greedy per-column quantization with error compensation) for one linear layer and compare against round-to-nearest at 4 bits.

---
[← Inference I: kv-cache](chapter12.md) | [Index](../COURSE.md) | [Next: Finetuning I: SFT →](chapter14.md)
