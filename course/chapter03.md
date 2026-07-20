# Chapter 03 — N-gram model (MLP)

> Goal: go from lookup tables to a real neural language model — a multi-layer perceptron over character embeddings, following the classic Bengio et al. (2003) architecture. Along the way: matrix multiplication as the workhorse op, activations (tanh/GELU), and reading training diagnostics.

## Core path (study in order)

1. 🟢 [Karpathy — makemore Part 2: MLP](https://www.youtube.com/watch?v=TCH_1BHY58I) — implements the Bengio-style MLP language model: embeddings, hidden layer, minibatches, learning-rate tuning, train/dev/test splits.
2. 🟡 [Bengio et al. (2003) — A Neural Probabilistic Language Model](https://www.jmlr.org/papers/volume3/bengio03a/bengio03a.pdf) — the paper you just implemented; your first "read a real paper" moment, and very readable.
3. 🟢 [matrixmultiplication.xyz](http://matrixmultiplication.xyz/) — an animated matmul visualizer; make sure the mechanical picture is burned in, since everything from here on is matmuls.
4. 🟡 [Karpathy — makemore Part 3: Activations & Gradients, BatchNorm](https://www.youtube.com/watch?v=P6sfmUTpUmc) — how to *look at* a training net: activation saturation, dead neurons, gradient statistics. (Also previews Chapter 7 material.)
5. 🟡 [Karpathy — makemore Part 5: Building a WaveNet](https://www.youtube.com/watch?v=t3YJ5hKiMQ0) — grows the MLP into a hierarchical, tree-structured model and gets the code closer to PyTorch's `nn.Module` style.

## Going deeper (optional)

- 🟡 [CS231n — Neural Networks Part 1: Setting up the Architecture](https://cs231n.github.io/neural-networks-1/) — activation functions and representational power, in note form.
- 🟡 [Gaussian Error Linear Units (GELU)](https://arxiv.org/abs/1606.08415) — the activation GPT-2 uses (and the syllabus names); short paper, skim for the idea.
- 🔴 [WaveNet: A Generative Model for Raw Audio](https://arxiv.org/abs/1609.03499) — the paper behind makemore Part 5's architecture.
- 🔴 [Karpathy — makemore Part 4: Becoming a Backprop Ninja](https://www.youtube.com/watch?v=q8SA3rM6ckI) — manually backprop through the entire 2-layer MLP + BatchNorm without autograd. Hard and optional, but this is where backprop mastery is forged.

## Exercises & projects

- 🟢 The [Part 2 video description](https://www.youtube.com/watch?v=TCH_1BHY58I) exercises: beat the video's validation loss by tuning embedding size, hidden units, and learning rate; try different context lengths.
- 🟡 Upgrade your Storyteller: train the MLP model on TinyStories characters with a context of 8; sample and compare against your Chapter 1 bigram output.
- 🟡 Plot train vs. dev loss as you scale the hidden layer from 10 to 1000 neurons — watch underfitting turn into overfitting.
- 🔴 Do the [Backprop Ninja](https://www.youtube.com/watch?v=q8SA3rM6ckI) exercise notebook to the end (all gradients matching `.grad` exactly).
- 🔴 Replace `tanh` with GELU in your MLP and measure the difference; then implement GELU's exact form from the paper and compare with the tanh approximation.

---
[← Micrograd](chapter02.md) | [Index](../COURSE.md) | [Next: Attention →](chapter04.md)
