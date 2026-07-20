# LLM101n — Curated Self-Study Edition

Karpathy's official [LLM101n](README.md) course content doesn't exist yet — only the syllabus does. This is an unofficial, link-only study guide that follows his syllabus chapter by chapter. Nothing here is original course content: every chapter is a curated, ordered reading/watching list plus exercises and projects, so you can learn the material *now* while waiting for the real thing.

**End goal (same as the original):** understand and build a Storyteller LLM — a small GPT trained on [TinyStories](https://huggingface.co/datasets/roneneldan/TinyStories) that you tokenize, train, optimize, speed up, finetune, align, and finally deploy as a web app.

## How to use this course

- Each chapter has a **Core path** — do these in order; they take you from zero to working understanding.
- **Going deeper** sections are optional. Skip them on a first pass, return when curious.
- **Exercises & projects** are where the learning actually happens. Do at least one per chapter.
- Difficulty markers: 🟢 beginner-friendly · 🟡 intermediate · 🔴 advanced.
- The backbone of Chapters 1–7 is Karpathy's own [Neural Networks: Zero to Hero](https://karpathy.ai/zero-to-hero.html) video series — the closest thing to LLM101n that exists today.

## Syllabus

| # | Chapter | Topics |
|---|---------|--------|
| 00 | [Prerequisites](course/chapter00.md) | Python, PyTorch, calculus & linear algebra refreshers |
| 01 | [Bigram Language Model](course/chapter01.md) | language modeling |
| 02 | [Micrograd](course/chapter02.md) | machine learning, backpropagation |
| 03 | [N-gram model](course/chapter03.md) | multi-layer perceptron, matmul, GELU |
| 04 | [Attention](course/chapter04.md) | attention, softmax, positional encoding |
| 05 | [Transformer](course/chapter05.md) | transformer, residual, layernorm, GPT-2 |
| 06 | [Tokenization](course/chapter06.md) | minBPE, byte pair encoding |
| 07 | [Optimization](course/chapter07.md) | initialization, optimizers, AdamW |
| 08 | [Need for Speed I: Device](course/chapter08.md) | CPU, GPU, CUDA |
| 09 | [Need for Speed II: Precision](course/chapter09.md) | mixed precision, fp16, bf16, fp8 |
| 10 | [Need for Speed III: Distributed](course/chapter10.md) | DDP, ZeRO, parallelism |
| 11 | [Datasets](course/chapter11.md) | data loading, filtering, synthetic data |
| 12 | [Inference I: kv-cache](course/chapter12.md) | kv-cache, sampling |
| 13 | [Inference II: Quantization](course/chapter13.md) | int8, GPTQ, AWQ, llama.cpp |
| 14 | [Finetuning I: SFT](course/chapter14.md) | supervised finetuning, PEFT, LoRA, chat |
| 15 | [Finetuning II: RL](course/chapter15.md) | RLHF, PPO, DPO |
| 16 | [Deployment](course/chapter16.md) | API, web app |
| 17 | [Multimodal](course/chapter17.md) | VQVAE, diffusion transformer |
| — | [Appendix](course/appendix.md) | C, assembly, tensors, JAX, Llama, MoE, more |

## Suggested pacing

- **Chapters 0–7** are the heart of the course (Zero to Hero territory). Budget ~1 week each if you do the exercises; don't rush these.
- **Chapters 8–10** (speed) can be skimmed if you don't have GPU access, but do the CPU-runnable puzzle sets.
- **Chapters 11–16** turn your toy model into a product — each is doable in a few days.
- **Chapter 17** is a mini-course of its own; treat it as a capstone.

## The running project

To mirror the "Storyteller" spirit, carry one project through the whole course:

1. Ch 1–3: character-level models over TinyStories text.
2. Ch 4–7: your own small GPT trained on TinyStories (nanoGPT-style).
3. Ch 8–13: make it train and sample faster.
4. Ch 14–15: instruction-tune it to write stories on demand ("Tell me a story about a brave turtle").
5. Ch 16: ship it as a little ChatGPT-style web app.
6. Ch 17: illustrate the stories.
