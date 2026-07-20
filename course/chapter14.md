# Chapter 14 — Finetuning I: SFT

> Goal: turn a base "document completer" into an assistant — supervised finetuning on instruction/chat data, chat templates and special tokens, and parameter-efficient methods (LoRA/QLoRA) that make finetuning affordable.

## Core path (study in order)

1. 🟢 [Karpathy — Deep Dive into LLMs like ChatGPT](https://www.youtube.com/watch?v=7xTGNNLPyMI) — the 3.5-hour big-picture video: pretraining → SFT → RLHF, what a "chat model" actually is, hallucinations, and tool use. Frames both this chapter and the next.
2. 🟢 [Karpathy — State of GPT (Microsoft Build talk)](https://www.youtube.com/watch?v=bZQun8Y4L2A) — the compact (45 min) version of the same pipeline; great as a recap.
3. 🟡 [Ouyang et al. (2022) — Training language models to follow instructions (InstructGPT)](https://arxiv.org/abs/2203.02155) — the paper that defined the SFT → reward model → RLHF pipeline; read §3 (methods) carefully now, the RL parts return in Chapter 15.
4. 🟡 [Hugging Face — Chat Templates](https://huggingface.co/docs/transformers/chat_templating) — the unglamorous but critical detail: how conversations get flattened into token sequences with special tokens, and how templates differ per model.
5. 🟡 [Hu et al. (2021) — LoRA: Low-Rank Adaptation](https://arxiv.org/abs/2106.09685) — finetune by learning low-rank deltas on frozen weights; the method behind nearly all hobbyist finetuning. Then skim the [PEFT library](https://github.com/huggingface/peft) that implements it.
6. 🟡 [TRL — SFTTrainer docs](https://huggingface.co/docs/trl/sft_trainer) — the standard practical tool for running SFT, including packing and completion-only loss masking.

## Going deeper (optional)

- 🟡 [Stanford Alpaca](https://crfm.stanford.edu/2023/03/13/alpaca.html) — the famous "52k GPT-generated instructions" recipe that kicked off open instruction tuning.
- 🔴 [Dettmers et al. (2023) — QLoRA](https://arxiv.org/abs/2305.14314) — LoRA on top of a 4-bit base model (ties Chapter 13 to this one); finetune big models on one consumer GPU.
- 🔴 [Zhou et al. (2023) — LIMA: Less Is More for Alignment](https://arxiv.org/abs/2305.11206) — 1,000 excellent examples rivaling huge SFT datasets; what SFT does and doesn't teach.
- 🔴 [Hugging Face — The Alignment Handbook](https://github.com/huggingface/alignment-handbook) — complete, real recipes (data + configs) used to train models like Zephyr; the reference for doing this seriously.
- 🟡 [Unsloth](https://github.com/unslothai/unsloth) — the fastest practical way to LoRA-finetune small models on a free Colab GPU.

## Exercises & projects

- 🟢 **Storyteller milestone:** finetune your base model on [TinyStories-Instruct](https://huggingface.co/datasets/roneneldan/TinyStories-Instruct) (instruction-augmented TinyStories) so it writes a story *on demand* — given features, words to include, or a summary — instead of just rambling.
- 🟡 Design your own chat format for the Storyteller: add special tokens (`<|user|>`, `<|assistant|>`, end-of-turn), build the training examples with loss masked on user turns, and verify the model learns to stop at end-of-turn.
- 🟡 LoRA-finetune a small open model (e.g., TinyLlama or Qwen-0.5B) on Alpaca-style data with PEFT or Unsloth; then merge the adapter and compare against the base model on held-out instructions.
- 🔴 Work through chapter 7 (instruction finetuning) of [Raschka — LLMs-from-scratch](https://github.com/rasbt/LLMs-from-scratch), which implements SFT with no libraries.
- 🔴 Run the LIMA experiment in miniature: SFT on 100 hand-curated story instructions vs. 10,000 noisy synthetic ones — which model follows instructions better?

---
[← Inference II: Quantization](chapter13.md) | [Index](../COURSE.md) | [Next: Finetuning II: RL →](chapter15.md)
