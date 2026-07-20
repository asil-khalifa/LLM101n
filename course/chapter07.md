# Chapter 07 — Optimization

> Goal: understand what actually makes training work — weight initialization, normalization, learning-rate schedules, and the AdamW optimizer — and develop the practical skill of debugging a training run.

## Core path (study in order)

1. 🟢 [Karpathy — makemore Part 3: Activations & Gradients, BatchNorm](https://www.youtube.com/watch?v=P6sfmUTpUmc) — (rewatch from Chapter 3, now with full attention): why bad init kills training, saturation, dead neurons, and why normalization helps.
2. 🟢 [Karpathy — A Recipe for Training Neural Networks](https://karpathy.github.io/2019/04/25/recipe/) — the famous checklist blog post: become one with the data, overfit one batch first, verify loss at init. Bookmark it; reread before every project.
3. 🟡 [CS231n — Setting up the data and the loss / weight initialization](https://cs231n.github.io/neural-networks-2/) and [Learning: optimizers, babysitting the training process](https://cs231n.github.io/neural-networks-3/) — the written fundamentals of init, SGD variants, and monitoring.
4. 🟡 [Sebastian Ruder — An overview of gradient descent optimization algorithms](https://www.ruder.io/optimizing-gradient-descent/) — SGD → momentum → RMSProp → Adam in one coherent narrative.
5. 🟡 [Kingma & Ba (2014) — Adam](https://arxiv.org/abs/1412.6980) and [Loshchilov & Hutter (2017) — Decoupled Weight Decay Regularization (AdamW)](https://arxiv.org/abs/1711.05101) — the optimizer every LLM uses, and why weight decay must be decoupled from the adaptive step.

## Going deeper (optional)

- 🟡 [Distill — Why Momentum Really Works](https://distill.pub/2017/momentum/) — a gorgeous interactive explanation of the dynamics.
- 🔴 [He et al. (2015) — Delving Deep into Rectifiers (Kaiming init)](https://arxiv.org/abs/1502.01852) and [Glorot & Bengio (2010) — Xavier init](https://proceedings.mlr.press/v9/glorot10a/glorot10a.pdf) — where the init formulas come from.
- 🔴 [Ioffe & Szegedy (2015) — Batch Normalization](https://arxiv.org/abs/1502.03167) — the paper; note transformers use LayerNorm instead, and think about why.
- 🔴 [Loshchilov & Hutter (2016) — SGDR: warm restarts](https://arxiv.org/abs/1608.03983) — origin of the cosine learning-rate schedule used in the GPT-2/GPT-3 recipes.
- 🔴 [Kaplan et al. (2020) — Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361) and [Hoffmann et al. (2022) — Training Compute-Optimal LLMs (Chinchilla)](https://arxiv.org/abs/2203.15556) — the macro view of optimization: how loss scales with model size, data, and compute.
- 🔴 [Yang et al. — Tensor Programs V: μP transfer](https://arxiv.org/abs/2203.03466) — tune hyperparameters on a small model, transfer to a big one; frontier-lab standard practice.

## Exercises & projects

- 🟢 Implement SGD, SGD+momentum, RMSProp, and Adam **by hand** (raw tensor updates, no `torch.optim`) and race them on your Chapter 3 MLP. Plot the four loss curves.
- 🟡 Apply the Karpathy recipe to your Storyteller GPT end-to-end: verify init loss equals `-log(1/vocab_size)`, overfit a single batch to ~0 loss, then tune lr with a sweep.
- 🟡 Add a cosine schedule with linear warmup to your nanoGPT training (compare against the one in [nanoGPT's train.py](https://github.com/karpathy/nanoGPT/blob/master/train.py)); measure the effect of removing warmup.
- 🔴 Reproduce a mini scaling law: train 4–5 models of increasing size on TinyStories, plot final loss vs. parameters on log-log axes, and fit a power law.
- 🔴 Break things on purpose: initialize all weights to zero, then to N(0,1); remove the residual-projection scaling in nanoGPT. Diagnose each failure from the loss curve and activation stats alone.

---
[← Tokenization](chapter06.md) | [Index](../COURSE.md) | [Next: Need for Speed I: Device →](chapter08.md)
