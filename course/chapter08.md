# Chapter 08 — Need for Speed I: Device

> Goal: understand the hardware your model runs on — memory hierarchies, why GPUs, what a CUDA kernel is, and why deep learning performance is usually about memory bandwidth, not FLOPs.

**Prerequisite for the C/CUDA path:** basic C. If you don't have it, do the C section of the [Appendix](appendix.md) first.

## Core path (study in order)

1. 🟢 [Horace He — Making Deep Learning Go Brrrr From First Principles](https://horace.io/brrr_intro.html) — *the* mental model: compute-bound vs. memory-bound vs. overhead-bound. Read this before anything else; it reframes all performance work.
2. 🟢 [Modal — GPU Glossary](https://modal.com/gpu-glossary) — a well-organized, readable reference for every GPU term you're about to encounter (SM, warp, HBM, occupancy...).
3. 🟡 [GPU MODE lectures](https://github.com/gpu-mode/lectures) — a community lecture series (videos + code) that works through *Programming Massively Parallel Processors* (PMPP), the standard CUDA textbook. Do lectures 1–4 to start; get the PMPP book if you want the full treatment.
4. 🟡 [karpathy/llm.c](https://github.com/karpathy/llm.c) — GPT-2 training in pure C/CUDA, no PyTorch. Start with `train_gpt2.c` (CPU reference, very readable), then explore the CUDA kernels in `dev/cuda/` which are written in progressive optimization steps.
5. 🟡 [CUDA C++ Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/) — the official reference; read ch. 1–3 (programming model, thread hierarchy, memory) alongside the lectures.

## Going deeper (optional)

- 🔴 [Simon Boehm — How to Optimize a CUDA Matmul Kernel](https://siboehm.com/articles/22/CUDA-MMM) — step-by-step from naive matmul to near-cuBLAS performance; the single best CUDA optimization walkthrough on the internet.
- 🔴 [Ulrich Drepper — What Every Programmer Should Know About Memory](https://people.freebsd.org/~lstewart/articles/cpumemory.pdf) — caches, prefetching, and why memory layout dominates CPU performance.
- 🔴 [Triton](https://triton-lang.org/main/index.html) — write GPU kernels in Python; how much of modern kernel work is actually done (used inside `torch.compile`).
- 🟡 [Tim Dettmers — Which GPU(s) for Deep Learning](https://timdettmers.com/2023/01/30/which-gpu-for-deep-learning/) — practical hardware-buying guide with a genuinely good explanation of what specs matter and why.

## Exercises & projects

- 🟢 [GPU Puzzles (Sasha Rush)](https://github.com/srush/GPU-Puzzles) — learn CUDA thread indexing by solving 14 puzzles in a notebook (runs on free Colab GPUs).
- 🟡 [Triton Puzzles](https://github.com/srush/Triton-Puzzles) — the same idea for Triton block programming.
- 🟡 [LeetGPU](https://leetgpu.com/) — LeetCode-style CUDA challenges you can run in the browser, no GPU required.
- 🟡 Profile your Storyteller training step with [PyTorch Profiler](https://pytorch.org/tutorials/recipes/recipes/profiler_recipe.html): find the top-5 kernels, classify each as compute- or memory-bound, then measure what `torch.compile` changes.
- 🔴 Write your own CUDA kernels for softmax and layernorm, verify against PyTorch, and benchmark. Compare your approach with the progressive versions in [llm.c dev/cuda](https://github.com/karpathy/llm.c/tree/master/dev/cuda).
- 🔴 Follow the [Simon Boehm matmul post](https://siboehm.com/articles/22/CUDA-MMM) and reimplement each optimization stage yourself, reproducing his speedup ladder.

---
[← Optimization](chapter07.md) | [Index](../COURSE.md) | [Next: Need for Speed II: Precision →](chapter09.md)
