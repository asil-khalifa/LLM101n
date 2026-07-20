# Appendix — Supporting Topics

The original syllabus lists these as "further topics to work into the progression." Dip into them when a main chapter demands it, or explore for their own sake.

## Programming languages: Assembly, C, Python

- 🟢 [CS50x — Introduction to Computer Science](https://cs50.harvard.edu/x/) — weeks 1–5 teach C, memory, and data structures; the ideal on-ramp for Chapter 8 and llm.c.
- 🟢 [Beej's Guide to C Programming](https://beej.us/guide/bgc/) — a free, friendly, complete C book if you just need the language.
- 🟡 *The C Programming Language* (Kernighan & Ritchie) — the classic; short enough to actually read.
- 🟡 [Putting the "You" in CPU (cpu.land)](https://cpu.land/) — a delightful short tour of what actually happens when a program runs: syscalls, execution, memory paging.
- 🔴 [Compiler Explorer (godbolt.org)](https://godbolt.org/) — paste C, see assembly; the best way to *acquire* assembly literacy incrementally.

## Data types: Integer, Float, String

- 🟢 [Joel Spolsky — The Absolute Minimum About Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/) — ASCII → Unicode → UTF-8 (also in Chapter 6).
- 🟢 [Float Toy](https://evanw.github.io/float-toy/) / [float.exposed](https://float.exposed/) — bit-level float intuition (also in Chapter 9).
- 🔴 [Goldberg — What Every Computer Scientist Should Know About Floating-Point Arithmetic](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html) — the deep reference.

## Tensors: shapes, views, strides

- 🟡 [ezyang — PyTorch internals](http://blog.ezyang.com/2019/05/pytorch-internals/) — the celebrated tour of how tensors really work: storage, strides, views, dispatch.
- 🟡 [PyTorch — Tensor Views documentation](https://pytorch.org/docs/stable/tensor_view.html) — which ops share memory and why `.contiguous()` exists.
- 🟢 [Tensor Puzzles](https://github.com/srush/Tensor-Puzzles) — (also in Chapter 0) the exercise set for this exact material.

## Deep Learning frameworks: PyTorch, JAX

- 🟢 [PyTorch Tutorials](https://pytorch.org/tutorials/) — the official hub, from basics to distributed.
- 🟡 [JAX documentation & tutorials](https://docs.jax.dev/en/latest/) — functional, composable `grad`/`jit`/`vmap`; learning JAX after this course is a great way to test your understanding.
- 🔴 [MiniTorch](https://minitorch.github.io/) — build your own mini-PyTorch (tensors, autograd, CUDA-ish backend) through structured assignments; the framework-internals capstone.

## Neural Net Architectures: GPT lineage, Llama, MoE

- 🟡 [GPT-1](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf) · [GPT-2](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) · [GPT-3](https://arxiv.org/abs/2005.14165) — read in sequence to watch the recipe stabilize and scale.
- 🟡 [Touvron et al. (2023) — Llama 2](https://arxiv.org/abs/2307.09288) and [Llama 3 herd of models (2024)](https://arxiv.org/abs/2407.21783) — the open-weights standard; spot the deltas from GPT-2: [RoPE](https://arxiv.org/abs/2104.09864), [RMSNorm](https://arxiv.org/abs/1910.07467), SwiGLU, [GQA](https://arxiv.org/abs/2305.13245).
- 🟡 [Hugging Face — Mixture of Experts Explained](https://huggingface.co/blog/moe) — the MoE survey blog; then [Switch Transformers](https://arxiv.org/abs/2101.03961) and [Mixtral of Experts](https://arxiv.org/abs/2401.04088) for the papers.
- 🔴 [DeepSeek-V3 Technical Report](https://arxiv.org/abs/2412.19437) — a frontier-scale open report tying together MoE, fp8, and pipeline engineering; a capstone read after Chapters 8–10.

## Multimodal extras: Audio, Video

- 🟡 [Hugging Face Audio Course](https://huggingface.co/learn/audio-course/chapter0/introduction) — audio transformers hands-on (ASR, TTS).
- 🔴 [Radford et al. (2022) — Whisper](https://arxiv.org/abs/2212.04356) — speech recognition as plain sequence-to-sequence transformer; very readable.

## Complete courses & books to continue with

- 🟡 [Stanford CS224n — NLP with Deep Learning](https://web.stanford.edu/class/cs224n/) — the academic NLP counterpart to this course (lectures on YouTube).
- 🔴 [Stanford CS336 — Language Modeling from Scratch](https://stanford-cs336.github.io/) — the closest university course to LLM101n's spirit: build everything (tokenizer → transformer → parallelism → RLHF) in five big assignments, all public.
- 🟡 [fast.ai — Practical Deep Learning](https://course.fast.ai/) — top-down complement to this course's bottom-up style (Part 2 builds Stable Diffusion from scratch).
- 🟡 [Sebastian Raschka — Build a Large Language Model From Scratch (repo)](https://github.com/rasbt/LLMs-from-scratch) — book-shaped version of Chapters 4–15 with exercises.
- 🔴 [ARENA 3.0](https://github.com/callummcdougall/ARENA_3.0) — the deepest exercise-driven curriculum out there: transformers, RL, and mechanistic interpretability.
- 🔴 [EleutherAI Cookbook](https://github.com/EleutherAI/cookbook) — practical utilities, benchmarks, and calculations for working with real LLMs at scale.

---
[← Multimodal](chapter17.md) | [Index](../COURSE.md)
