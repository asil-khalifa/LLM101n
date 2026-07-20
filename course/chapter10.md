# Chapter 10 — Need for Speed III: Distributed

> Goal: understand how training scales past one GPU — data parallelism (DDP), sharding optimizer state (ZeRO/FSDP), and the tensor/pipeline parallelism used for models that don't fit on one device.

*No multi-GPU machine? You can still do almost everything here conceptually, and simulate multi-process training with the `gloo` backend on CPU.*

## Core path (study in order)

1. 🟢 [Lilian Weng — How to Train Really Large Models on Many GPUs](https://lilianweng.github.io/posts/2021-09-25-train-large/) — a survey of the whole landscape (data/tensor/pipeline parallelism, ZeRO, activation checkpointing) so you have the map before the territory.
2. 🟡 [PyTorch — Getting Started with Distributed Data Parallel](https://pytorch.org/tutorials/intermediate/ddp_tutorial.html) — the hands-on tutorial: process groups, `torchrun`, wrapping your model in DDP.
3. 🟡 [Karpathy — Let's reproduce GPT-2, DDP section](https://www.youtube.com/watch?v=l8pRSuU81PU) — watch him convert the single-GPU training loop to multi-GPU DDP with gradient accumulation; also read the same logic in [nanoGPT's train.py](https://github.com/karpathy/nanoGPT/blob/master/train.py).
4. 🟡 [Hugging Face — The Ultra-Scale Playbook: Training LLMs on GPU Clusters](https://huggingface.co/spaces/nanotron/ultrascale-playbook) — the modern bible of this topic, built from 4000+ real scaling experiments; interactive and thorough. Work through it section by section — this alone can carry the chapter.

## Going deeper (optional)

- 🔴 [Rajbhandari et al. (2019) — ZeRO: Memory Optimizations Toward Training Trillion Parameter Models](https://arxiv.org/abs/1910.02054) — sharding optimizer state, gradients, and parameters (stages 1/2/3).
- 🔴 [PyTorch — Getting Started with Fully Sharded Data Parallel (FSDP)](https://pytorch.org/tutorials/intermediate/FSDP_tutorial.html) — ZeRO-3 ideas natively in PyTorch.
- 🔴 [Shoeybi et al. (2019) — Megatron-LM](https://arxiv.org/abs/1909.08053) — tensor parallelism: splitting individual matmuls across GPUs.
- 🔴 [Huang et al. (2018) — GPipe](https://arxiv.org/abs/1811.06965) — pipeline parallelism and micro-batching.
- 🔴 [EleutherAI — Transformer Math 101](https://blog.eleuther.ai/transformer-math/) — back-of-envelope formulas for memory and compute; lets you predict whether a config fits before launching it.
- 🔴 [DeepSpeed](https://www.deepspeed.ai/) — the library where ZeRO lives, if you want to drive it directly.

## Exercises & projects

- 🟢 Do the memory math by hand first: for your Storyteller model, compute bytes for weights, Adam states, gradients, and activations; check your numbers against the Transformer Math 101 formulas.
- 🟡 Run nanoGPT with `torchrun --nproc_per_node=N` (multi-GPU if you have it; otherwise 2–4 CPU processes with the `gloo` backend) and verify the loss curve matches single-process training with the same effective batch size.
- 🟡 Implement gradient accumulation from scratch and prove (loss-curve overlay) that batch 32 == batch 8 × 4 accumulation steps.
- 🔴 Implement ZeRO stage 1 yourself in a toy setting: shard Adam's moment tensors across processes and all-gather updated params each step.
- 🔴 Work through the Ultra-Scale Playbook's throughput reasoning and write a one-page "training plan" (parallelism layout, memory budget, expected tokens/sec) for training a 1B model on 8 GPUs.

---
[← Need for Speed II: Precision](chapter09.md) | [Index](../COURSE.md) | [Next: Datasets →](chapter11.md)
