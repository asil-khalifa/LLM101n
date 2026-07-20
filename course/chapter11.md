# Chapter 11 — Datasets

> Goal: understand where training data comes from and why it matters as much as architecture — web-scale scraping and filtering, dataset formats and loading, and synthetic data generation (which is exactly how TinyStories, your Storyteller's diet, was made).

## Core path (study in order)

1. 🟢 [Eldan & Li (2023) — TinyStories: How Small Can Language Models Be and Still Speak Coherent English?](https://arxiv.org/abs/2305.07759) — *the* paper for this course: a fully synthetic dataset (GPT-3.5/4-generated children's stories) that lets ~10M-param models tell coherent stories. Read it fully — it's approachable and it explains why your small model can work at all. Dataset: [roneneldan/TinyStories](https://huggingface.co/datasets/roneneldan/TinyStories).
2. 🟢 [Hugging Face NLP Course — Chapter 5: The 🤗 Datasets library](https://huggingface.co/learn/nlp-course/chapter5/1) — practical data loading: streaming, map/filter, memory-mapped datasets that don't blow up your RAM.
3. 🟡 [nanoGPT data preparation scripts](https://github.com/karpathy/nanoGPT/tree/master/data) — the simplest serious pipeline: tokenize once, write flat uint16 `.bin` files, `memmap` + random offsets at train time. Read `prepare.py` and the dataloader in `train.py`.
4. 🟡 [Hugging Face — FineWeb: decanting the web for the finest text data at scale](https://huggingface.co/spaces/HuggingFaceFW/blogpost-fineweb-v1) — the definitive modern write-up of web-scale data work: CommonCrawl extraction, quality filtering, deduplication, and the ablations behind every decision (includes FineWeb-Edu and its educational-quality classifier).

## Going deeper (optional)

- 🟡 [Gao et al. (2020) — The Pile](https://arxiv.org/abs/2101.00027) — the classic open pretraining corpus paper; good for understanding dataset *composition* thinking.
- 🟡 [Raffel et al. (2019) — T5 paper, §2 on C4](https://arxiv.org/abs/1910.10683) — where the "clean the Common Crawl" recipe started.
- 🔴 [Lee et al. (2021) — Deduplicating Training Data Makes Language Models Better](https://arxiv.org/abs/2107.06499) — why and how dedup (exact + MinHash) matters.
- 🔴 [Soldaini et al. (2024) — Dolma](https://arxiv.org/abs/2402.00159) — a fully documented open corpus + [tooling](https://github.com/allenai/dolma); the most transparent look at every pipeline stage.
- 🔴 [Gunasekar et al. (2023) — Textbooks Are All You Need (phi-1)](https://arxiv.org/abs/2306.11644) — the synthetic-data thesis at model scale; TinyStories' philosophical successor.
- 🔴 [Hugging Face — Cosmopedia](https://huggingface.co/blog/cosmopedia) — how to actually generate a 25B-token synthetic dataset, with code ([datatrove](https://github.com/huggingface/datatrove) is the accompanying processing library).

## Exercises & projects

- 🟢 Build your Storyteller data pipeline properly: download TinyStories, train-tokenizer → tokenize → shard into `.bin` files, and write a dataloader with deterministic resumption (save/restore its position).
- 🟡 Data ablation: train the same model on TinyStories vs. an equal-token slice of raw web text (e.g., a [FineWeb sample](https://huggingface.co/datasets/HuggingFaceFW/fineweb)) and compare story coherence — reproducing the TinyStories paper's core claim yourself.
- 🟡 Generate your own synthetic mini-dataset: use an LLM API with the TinyStories paper's prompt recipe (random word triplets + story features) to create ~1k stories; inspect diversity and dedup them.
- 🔴 Implement MinHash deduplication over your corpus and measure how many near-duplicate stories TinyStories itself contains.
- 🔴 Train a small quality classifier (FineWeb-Edu style) to score your synthetic stories, filter the bottom half, retrain, and see if quality-filtering beats quantity.

---
[← Need for Speed III: Distributed](chapter10.md) | [Index](../COURSE.md) | [Next: Inference I: kv-cache →](chapter12.md)
