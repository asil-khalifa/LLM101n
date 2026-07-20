# Chapter 02 — Micrograd

> Goal: understand backpropagation well enough to implement it. You'll build a tiny autograd engine (~100 lines) that can train a neural net — the same mechanism PyTorch uses, minus the tensors and the speed.

## Core path (study in order)

1. 🟢 [Karpathy — The spelled-out intro to neural networks and backpropagation: building micrograd](https://www.youtube.com/watch?v=VMj-3S1tku0) — 2.5 hours that many people call the best single explanation of backprop anywhere. Build it cell by cell yourself.
2. 🟢 [micrograd repository](https://github.com/karpathy/micrograd) — the finished ~150-line engine; read it top to bottom after the video.
3. 🟢 [3Blue1Brown — What is backpropagation really doing?](https://www.youtube.com/watch?v=Ilg3gGewQ5U) — the visual companion; watch after building to consolidate.
4. 🟡 [CS231n — Backpropagation, Intuitions](https://cs231n.github.io/optimization-2/) — Karpathy's own written notes: gradients as local circuits, patterns in gradient flow (add gate = distributor, max gate = router...).
5. 🟡 [Chris Olah — Calculus on Computational Graphs: Backpropagation](https://colah.github.io/posts/2015-08-Backprop/) — why backprop is just the chain rule organized efficiently, and why reverse-mode beats forward-mode.

## Going deeper (optional)

- 🟡 [Nielsen — How the backpropagation algorithm works](http://neuralnetworksanddeeplearning.com/chap2.html) — the same ideas with full matrix notation.
- 🔴 [PyTorch Autograd mechanics](https://pytorch.org/docs/stable/notes/autograd.html) — how the real thing handles graphs, leaf tensors, and gradient accumulation.
- 🔴 [Automatic Differentiation in Machine Learning: a Survey](https://arxiv.org/abs/1502.05767) — the academic overview: forward vs. reverse mode, and where backprop sits in the wider AD world.
- 🔴 [tinygrad](https://github.com/tinygrad/tinygrad) — a "what if micrograd grew up" codebase; a full deep learning framework kept deliberately small. Great to read after this chapter.

## Exercises & projects

- 🟢 Do the official [micrograd exercises notebook](https://colab.research.google.com/drive/1FPTx1RXtBfc4MaTkf7viZZD4U2F9gtKN) (linked from the video description): derive gradients by hand, then verify against your engine.
- 🟡 Extend micrograd: add `exp`, `log`, `sigmoid`, and a `softmax` + cross-entropy loss, and use it to train the Chapter 1 bigram neural net *without PyTorch*.
- 🟡 Add gradient checking: compare your backprop gradients against numerical finite-difference gradients.
- 🔴 Reimplement micrograd in another language you know (C, Rust, JS...) — the ultimate "do I actually understand this" test.
- 🔴 Upgrade the engine from scalars to tensors (NumPy arrays with broadcasting) — you'll rediscover why gradients need to be summed over broadcast dimensions.

---
[← Bigram Language Model](chapter01.md) | [Index](../COURSE.md) | [Next: N-gram model →](chapter03.md)
