# Chapter 17 — Multimodal

> Goal: extend beyond text — learn how images become tokens (VQ-VAE) and how diffusion models generate images (DDPM → diffusion transformers) — so your Storyteller can illustrate its stories. Treat this as a capstone mini-course.

## Core path (study in order)

1. 🟢 [Jay Alammar — The Illustrated Stable Diffusion](https://jalammar.github.io/illustrated-stable-diffusion/) — the gentle overview of a full text-to-image system: text encoder, latent space, denoising loop.
2. 🟢 [Hugging Face Diffusion Models Course](https://github.com/huggingface/diffusion-models-class) — hands-on notebooks: train a tiny diffusion model from scratch, then work up through the `diffusers` library.
3. 🟡 [Lilian Weng — What are Diffusion Models?](https://lilianweng.github.io/posts/2021-07-11-diffusion-models/) — the mathematical treatment; read after the notebooks so the math attaches to code you've run.
4. 🟡 [van den Oord et al. (2017) — Neural Discrete Representation Learning (VQ-VAE)](https://arxiv.org/abs/1711.00937) — images as a grid of discrete codes; the conceptual bridge from LLM-land ("image tokens") into vision.
5. 🟡 [Ho et al. (2020) — Denoising Diffusion Probabilistic Models (DDPM)](https://arxiv.org/abs/2006.11239) — the foundational diffusion paper, paired with [The Annotated Diffusion Model](https://huggingface.co/blog/annotated-diffusion) which implements it line by line.
6. 🔴 [Peebles & Xie (2022) — Scalable Diffusion Models with Transformers (DiT)](https://arxiv.org/abs/2212.09748) — the syllabus's "diffusion transformer": replace the U-Net with the transformer you built in Chapter 5; backbone of modern image/video generators (e.g., Sora).

## Going deeper (optional)

- 🔴 [Rombach et al. (2021) — Latent Diffusion Models (Stable Diffusion)](https://arxiv.org/abs/2112.10752) — diffusion in a VAE's latent space; how generation got cheap.
- 🔴 [Esser et al. (2020) — Taming Transformers (VQGAN)](https://arxiv.org/abs/2012.09841) — VQ-VAE + adversarial loss + autoregressive transformer over codes: literally "GPT for image tokens".
- 🔴 [Dosovitskiy et al. (2020) — Vision Transformer (ViT)](https://arxiv.org/abs/2010.11929) and [Radford et al. (2021) — CLIP](https://arxiv.org/abs/2103.00020) — how transformers see images, and how text and images share an embedding space.
- 🔴 [Liu et al. (2023) — Visual Instruction Tuning (LLaVA)](https://arxiv.org/abs/2304.08485) — the other direction of multimodal: bolting a vision encoder onto an LLM so it can *understand* images.
- 🔴 [Lipman et al. (2022) — Flow Matching](https://arxiv.org/abs/2210.02747) — the successor framework to diffusion used by newest generators; genuinely advanced.

## Exercises & projects

- 🟢 Do the first two units of the [HF diffusion course](https://github.com/huggingface/diffusion-models-class): train an unconditional DDPM on a small image dataset and sample from it.
- 🟡 Implement a VQ-VAE on MNIST or CIFAR-10 from the paper: encoder, codebook with straight-through estimator, decoder. Visualize the discrete code grid for sample images.
- 🟡 Then train your Chapter 5 GPT *on the VQ-VAE code sequences* and sample new images token by token — you've now built the VQGAN-style pipeline and united the whole course.
- 🔴 Swap the U-Net in your DDPM for a small transformer (mini-DiT) and compare training curves and samples.
- 🔴 **Storyteller finale:** illustrate your stories — run a small Stable Diffusion via [diffusers](https://github.com/huggingface/diffusers) on scene descriptions extracted from each generated story, and add an "illustrate" button to your Chapter 16 web app.

---
[← Deployment](chapter16.md) | [Index](../COURSE.md) | [Next: Appendix →](appendix.md)
