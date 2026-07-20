# Chapter 05 — Transformer

> Goal: assemble attention into a full GPT — residual connections, LayerNorm, MLP blocks — train it, and understand GPT-2 as "your model, scaled up". This is the chapter where your Storyteller becomes real.

## Core path (study in order)

1. 🟢 [Karpathy — Let's build GPT (finish the video)](https://www.youtube.com/watch?v=kCc8FmEb1nY) — the second half: residual connections, LayerNorm, dropout, scaling up, and the connection to ChatGPT.
2. 🟢 [nanoGPT repository](https://github.com/karpathy/nanoGPT) — the cleaned-up production version of that video's code (~300 lines model + ~300 lines training loop). Read `model.py` line by line; this is your reference implementation for the rest of the course.
3. 🟢 [Brendan Bycroft — LLM Visualization](https://bbycroft.net/llm) — a stunning interactive 3D walkthrough of every tensor in a running GPT. Spend an hour here; it cements the architecture spatially.
4. 🟡 [Jay Alammar — The Illustrated GPT-2](https://jalammar.github.io/illustrated-gpt2/) — decoder-only transformers specifically, with the byte-level details of GPT-2.
5. 🟡 [Radford et al. (2019) — Language Models are Unsupervised Multitask Learners (GPT-2 paper)](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) — short and readable; the model you're rebuilding.
6. 🟡 [Karpathy — Let's reproduce GPT-2 (124M)](https://www.youtube.com/watch?v=l8pRSuU81PU) — a 4-hour masterclass: loads GPT-2 weights, matches the architecture exactly, and trains from scratch. Also your bridge into Chapters 7–10 (it covers mixed precision, torch.compile, DDP).

## Going deeper (optional)

- 🟡 [Peter Bloem — Transformers from scratch](https://peterbloem.nl/blog/transformers) — an alternative, more mathematical written build-up; great second perspective.
- 🟡 [The Annotated Transformer (Harvard NLP)](https://nlp.seas.harvard.edu/annotated-transformer/) — the original paper implemented line-by-line alongside the text (encoder-decoder variant).
- 🔴 [He et al. (2015) — Deep Residual Learning (ResNet)](https://arxiv.org/abs/1512.03385) — where residual connections come from and why they make deep nets trainable.
- 🔴 [Ba et al. (2016) — Layer Normalization](https://arxiv.org/abs/1607.06450) — the normalization GPT uses instead of BatchNorm.
- 🔴 [Brown et al. (2020) — Language Models are Few-Shot Learners (GPT-3 paper)](https://arxiv.org/abs/2005.14165) — what happens when you scale this exact recipe 1000×; skim §1–3 for in-context learning.
- 🔴 [minGPT](https://github.com/karpathy/minGPT) — nanoGPT's pedagogical predecessor; nice to diff against nanoGPT to see what "cleanup" looked like.

## Exercises & projects

- 🟢 The exercises in the [Let's build GPT video description](https://www.youtube.com/watch?v=kCc8FmEb1nY): e.g., train on your own dataset, tune into the lowest validation loss you can, add dropout.
- 🟡 **Storyteller milestone:** train nanoGPT (char-level or with its BPE prep) on [TinyStories](https://huggingface.co/datasets/roneneldan/TinyStories). Target coherent multi-sentence stories from a ~10M-parameter model — the [TinyStories paper](https://arxiv.org/abs/2305.07759) shows this is achievable.
- 🟡 Work through chapters 2–5 of [Sebastian Raschka — LLMs-from-scratch](https://github.com/rasbt/LLMs-from-scratch) (companion repo to *Build a Large Language Model From Scratch*) as a structured second pass with its own exercises.
- 🔴 [modded-nanogpt (Keller Jordan)](https://github.com/KellerJordan/modded-nanogpt) — the nanoGPT "speedrun" leaderboard. Study the tricks used to cut GPT-2 training time by an order of magnitude; try to explain each diff from baseline nanoGPT.
- 🔴 Ablate the architecture: remove residuals, remove LayerNorm, remove the MLP — train each variant and watch what breaks. Write up your findings.

---
[← Attention](chapter04.md) | [Index](../COURSE.md) | [Next: Tokenization →](chapter06.md)
