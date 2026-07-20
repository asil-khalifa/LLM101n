# Chapter 09 — Need for Speed II: Precision

> Goal: understand floating-point formats (fp32, tf32, fp16, bf16, fp8) and mixed-precision training — how to halve memory and double speed without destroying your loss curve.

## Core path (study in order)

1. 🟢 [Float Toy](https://evanw.github.io/float-toy/) — flip the bits of fp16/fp32/fp64 numbers by hand until sign/exponent/mantissa is second nature.
2. 🟢 [float.exposed](https://float.exposed/) — a complementary visualizer; look up where numbers land and watch precision thin out as magnitudes grow.
3. 🟡 [Micikevicius et al. (2017) — Mixed Precision Training](https://arxiv.org/abs/1710.03740) — the foundational paper: fp16 master-weight copies, loss scaling, and which ops need fp32.
4. 🟡 [PyTorch Automatic Mixed Precision (AMP)](https://pytorch.org/docs/stable/amp.html) — how it works in practice: `autocast` + `GradScaler`, and which ops autocast to which dtype.
5. 🟡 [Google Cloud — BFloat16: the secret to high performance on Cloud TPUs](https://cloud.google.com/blog/products/ai-machine-learning/bfloat16-the-secret-to-high-performance-on-cloud-tpus) — why bf16 (fp32's exponent range, less mantissa) mostly eliminates the need for loss scaling and became the LLM training default.
6. 🟡 [Karpathy — Let's reproduce GPT-2, precision section](https://www.youtube.com/watch?v=l8pRSuU81PU) — watch the part of the video where he steps through tf32 → bf16 and measures the actual speedups on real hardware.

## Going deeper (optional)

- 🔴 [NVIDIA — Train With Mixed Precision guide](https://docs.nvidia.com/deeplearning/performance/mixed-precision-training/index.html) — the engineering reference: tensor cores, loss-scaling recipes, debugging overflow.
- 🔴 [Micikevicius et al. (2022) — FP8 Formats for Deep Learning](https://arxiv.org/abs/2209.05433) — the E4M3/E5M2 formats behind H100-era training.
- 🔴 [DeepSeek-V3 Technical Report](https://arxiv.org/abs/2412.19437) — §3.3 describes fp8 training at frontier scale actually working; a look at the state of the art.
- 🔴 [Goldberg — What Every Computer Scientist Should Know About Floating-Point Arithmetic](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html) — the classic deep reference on rounding, ulps, and error analysis.

## Exercises & projects

- 🟢 In a notebook, compute `(0.1 + 0.2)`, big+small sums, and long summations in fp32 vs fp16 vs bf16 tensors; explain each surprise using what Float Toy taught you.
- 🟡 Write an fp32 → bf16 converter by hand (bit masking/shifting, in Python or C) and verify it against `tensor.to(torch.bfloat16)`.
- 🟡 **Storyteller milestone:** train the same model in fp32, then bf16 autocast, then fp16 + GradScaler. Compare wall-clock time, memory usage, and final loss.
- 🔴 Implement manual fp16 mixed-precision training *without* `GradScaler` (your own loss-scaling logic with overflow detection), matching AMP's result.
- 🔴 Sweep loss-scale values in fp16 training until it diverges; log where gradients underflow to zero. Write up why bf16 doesn't have this problem.

---
[← Need for Speed I: Device](chapter08.md) | [Index](../COURSE.md) | [Next: Need for Speed III: Distributed →](chapter10.md)
