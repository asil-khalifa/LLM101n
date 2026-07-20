# Chapter 06 — Tokenization

> Goal: understand how raw text becomes integers — Unicode, UTF-8 bytes, and byte-pair encoding — by building a GPT-style tokenizer from scratch. Tokenization explains a surprising number of LLM quirks (spelling failures, arithmetic weirdness, "SolidGoldMagikarp").

## Core path (study in order)

1. 🟢 [Karpathy — Let's build the GPT Tokenizer](https://www.youtube.com/watch?v=zduSFxRajkE) — 2 hours building minBPE: Unicode → UTF-8 → BPE training → encode/decode → GPT-2/GPT-4 tokenizer details and the weird failure modes tokenization causes.
2. 🟢 [minbpe repository](https://github.com/karpathy/minbpe) — the reference code from the video: basic BPE, regex-split BPE (GPT-2 style), and GPT-4 tokenizer loading.
3. 🟢 [Tiktokenizer](https://tiktokenizer.vercel.app/) — interactive playground: paste text, see exactly how different models tokenize it. Build intuition by trying numbers, code, non-English text.
4. 🟡 [Joel Spolsky — The Absolute Minimum Every Software Developer Must Know About Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/) — the character-encoding background the video assumes.
5. 🟡 [Hugging Face NLP Course — Chapter 6: The Tokenizers library](https://huggingface.co/learn/nlp-course/chapter6/1) — how tokenizers work in the ecosystem you'll use later: WordPiece vs. BPE vs. Unigram, fast tokenizers, offsets.

## Going deeper (optional)

- 🟡 [Sennrich et al. (2015) — Neural Machine Translation of Rare Words with Subword Units](https://arxiv.org/abs/1508.07909) — the paper that brought BPE into NLP.
- 🟡 [tiktoken](https://github.com/openai/tiktoken) — OpenAI's production BPE implementation; compare its design against your minbpe.
- 🔴 [Kudo & Richardson (2018) — SentencePiece](https://arxiv.org/abs/1808.06226) — the tokenizer used by Llama and many others; language-agnostic, trains from raw text ([code](https://github.com/google/sentencepiece)).
- 🔴 [UTF-8 Everywhere](https://utf8everywhere.org/) — a manifesto-slash-deep-dive on why UTF-8 won.
- 🔴 [Xue et al. (2021) — ByT5: Towards a Token-Free Future](https://arxiv.org/abs/2105.13626) — what happens if you skip tokenization and model raw bytes.

## Exercises & projects

- 🟢 [minbpe exercise.md](https://github.com/karpathy/minbpe/blob/master/exercise.md) — the official exercise progression: build BasicTokenizer → RegexTokenizer → recover GPT-4's tokenizer merges yourself. Do this before peeking at the solution code.
- 🟡 **Storyteller milestone:** train a small BPE tokenizer (say, 4096 merges) on TinyStories, retrain your Chapter 5 GPT on token IDs instead of characters, and compare: loss per byte, story quality, effective context length.
- 🟡 Explore failure modes: using Tiktokenizer, explain why LLMs are bad at reversing strings and at arithmetic with long numbers. Write a short note connecting each quirk to tokenization.
- 🔴 Train two tokenizers (2k vs. 32k vocab) on the same corpus, train the same model on both, and study the compression-vs-model-difficulty tradeoff.

---
[← Transformer](chapter05.md) | [Index](../COURSE.md) | [Next: Optimization →](chapter07.md)
