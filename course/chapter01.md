# Chapter 01 — Bigram Language Model

> Goal: understand what "language modeling" means — predicting the next token — by building the simplest possible model: a lookup table of character-pair counts. Also meet the loss function (negative log likelihood) you'll use for the rest of the course.

## Core path (study in order)

1. 🟢 [Karpathy — The spelled-out intro to language modeling: building makemore](https://www.youtube.com/watch?v=PaCmpygFfXo) — the heart of this chapter. Builds a bigram character-level model twice: from counts, then from a one-layer neural net trained by gradient descent. Code along, don't just watch.
2. 🟢 [makemore repository](https://github.com/karpathy/makemore) — the code from the video series; keep it open as reference.
3. 🟡 [Speech and Language Processing (Jurafsky & Martin), ch. "N-gram Language Models"](https://web.stanford.edu/~jurafsky/slp3/3.pdf) — the classical textbook treatment: probabilities, smoothing, and **perplexity**, the standard way to evaluate a language model.
4. 🟡 [Lena Voita — NLP Course For You: Language Modeling](https://lena-voita.github.io/nlp_course/language_modeling.html) — beautifully illustrated bridge from count-based models to neural ones.

## Going deeper (optional)

- 🔴 [Shannon (1951) — Prediction and Entropy of Printed English](https://www.princeton.edu/~wbialek/rome/refs/shannon_51.pdf) — the 75-year-old origin of "predict the next character": Shannon estimating the entropy of English with humans as the language model.
- 🔴 [Shannon (1948) — A Mathematical Theory of Communication](https://people.math.harvard.edu/~ctm/home/text/others/shannon/entropy/entropy.pdf) — where entropy and information theory come from; skim §3 on the series of letter-level approximations to English — that's literally an n-gram model.
- 🟡 [Karpathy — The Unreasonable Effectiveness of Recurrent Neural Networks](https://karpathy.github.io/2015/05/21/rnn-effectiveness/) — 2015 blog post that made character-level language models famous; great motivation for where this is all going.

## Exercises & projects

- 🟢 Do the exercises listed in the [video description](https://www.youtube.com/watch?v=PaCmpygFfXo) (e.g., extend the bigram model to a **trigram** model and compare losses; split data into train/dev/test; add smoothing).
- 🟢 Swap the names dataset for [TinyStories](https://huggingface.co/datasets/roneneldan/TinyStories) text and sample "stories" from a character bigram model. This starts your running Storyteller project — enjoy how bad it is; every later chapter improves it.
- 🟡 Grab a book from [Project Gutenberg](https://www.gutenberg.org/) and build a **word-level** bigram model. Implement perplexity evaluation and compare add-one vs. no smoothing on held-out text.
- 🔴 Reproduce Shannon's letter-guessing game: write a script where the model reveals its per-character probabilities and compute an entropy estimate of your corpus.

---
[← Prerequisites](chapter00.md) | [Index](../COURSE.md) | [Next: Micrograd →](chapter02.md)
