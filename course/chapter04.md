# Chapter 04 — Attention

> Goal: deeply understand self-attention — queries, keys, values, softmax weighting, masking, and positional information. This is the single most important idea in the course; take your time.

## Core path (study in order)

1. 🟢 [3Blue1Brown — Attention in transformers, visually explained](https://www.youtube.com/watch?v=eMlx5fFNoYc) — the best first exposure; watch before touching any code.
2. 🟢 [Jay Alammar — The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) — the classic walkthrough with diagrams for Q/K/V, multi-head attention, and encoder-decoder structure.
3. 🟡 [Karpathy — Let's build GPT: from scratch, in code, spelled out](https://www.youtube.com/watch?v=kCc8FmEb1nY) — **watch up to the point where the full block is assembled** (roughly the first ~90 minutes): the "mathematical trick" of masked attention, then single-head, then multi-head attention, built in code. (You'll finish the video in Chapter 5.)
4. 🟡 [Eli Bendersky — The Softmax function and its derivative](https://eli.thegreenplace.net/2016/the-softmax-function-and-its-derivative/) — softmax done carefully, including the numerical-stability max-subtraction trick you'll see in every implementation.
5. 🟡 [Kazemnejad — Transformer Architecture: The Positional Encoding](https://kazemnejad.com/blog/transformer_architecture_positional_encoding/) — why attention needs position information at all, and how sinusoidal encodings work.
6. 🟡 [Vaswani et al. (2017) — Attention Is All You Need](https://arxiv.org/abs/1706.03762) — now read the original paper; after the above it will feel surprisingly approachable.

## Going deeper (optional)

- 🟡 [Lilian Weng — Attention? Attention!](https://lilianweng.github.io/posts/2018-06-24-attention/) — the historical arc: seq2seq, alignment, and the attention family tree.
- 🔴 [Bahdanau et al. (2014) — Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/abs/1409.0473) — where attention was invented, before transformers.
- 🔴 [Anthropic — A Mathematical Framework for Transformer Circuits](https://transformer-circuits.pub/2021/framework/index.html) — attention heads as information-moving circuits; the doorway into mechanistic interpretability.
- 🔴 [FlashAttention](https://arxiv.org/abs/2205.14135) — how attention is *actually* computed fast on GPUs (IO-aware tiling); revisit again after Chapter 8.
- 🔴 [RoFormer: Rotary Position Embedding (RoPE)](https://arxiv.org/abs/2104.09864) — the positional encoding modern models (Llama, etc.) actually use.

## Exercises & projects

- 🟢 Implement single-head self-attention three ways and check they match: (a) explicit loops, (b) masked matmul + softmax, (c) `torch.nn.functional.scaled_dot_product_attention`.
- 🟡 [GPT in 60 Lines of NumPy (Jay Mody)](https://jaymody.com/blog/gpt-from-scratch/) — work through it, then close the page and rewrite [picoGPT](https://github.com/jaymody/picoGPT) from memory.
- 🟡 Visualize attention: train the Chapter 5 model early (or use a pretrained one) and plot the attention matrices as heatmaps for a sample story sentence.
- 🔴 Ablation study: train tiny models with (a) no positional encoding, (b) learned positions, (c) sinusoidal — compare losses and generated text.
- 🔴 [ARENA — Transformer from scratch & interpretability track](https://github.com/callummcdougall/ARENA_3.0) — a full guided curriculum with exercises if you want to go deep on attention internals.

---
[← N-gram model](chapter03.md) | [Index](../COURSE.md) | [Next: Transformer →](chapter05.md)
