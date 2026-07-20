# Chapter 15 — Finetuning II: RL

> Goal: understand alignment via preferences — reward models, RLHF with PPO, the simpler DPO alternative, and the newer RL-for-reasoning wave (GRPO) — and apply a preference-tuning method to your own model.

## Core path (study in order)

1. 🟢 [Hugging Face — Illustrating RLHF](https://huggingface.co/blog/rlhf) — the standard visual overview of the three-stage pipeline: SFT → reward model → RL against the reward.
2. 🟢 [Chip Huyen — RLHF: Reinforcement Learning from Human Feedback](https://huyenchip.com/2023/05/02/rlhf.html) — a second, more detailed pass with the math laid out gently.
3. 🟡 [Karpathy — Deep Dive into LLMs, RLHF section](https://www.youtube.com/watch?v=7xTGNNLPyMI) — rewatch the RL/RLHF part of the Chapter 14 video now that you have the vocabulary; his take on why RLHF is "barely RL" is clarifying.
4. 🟡 [Stiennon et al. (2020) — Learning to Summarize from Human Feedback](https://arxiv.org/abs/2009.01325) — the cleanest full RLHF paper (pre-ChatGPT); easier to follow than InstructGPT and shows reward over-optimization.
5. 🟡 [Rafailov et al. (2023) — Direct Preference Optimization (DPO)](https://arxiv.org/abs/2305.18290) — skip the reward model and RL loop entirely; a clever loss directly on preference pairs. This is the method you'll most realistically use yourself.
6. 🟡 [TRL library](https://github.com/huggingface/trl) — implementations of everything above ([DPOTrainer docs](https://huggingface.co/docs/trl/dpo_trainer) is the one you'll want).

## Going deeper (optional)

- 🔴 [Schulman et al. (2017) — Proximal Policy Optimization (PPO)](https://arxiv.org/abs/1707.06347) — the RL algorithm under classic RLHF. For the RL foundations needed to really read it: [OpenAI Spinning Up in Deep RL](https://spinningup.openai.com/en/latest/) and, for the full grounding, [Sutton & Barto — Reinforcement Learning: An Introduction](http://incompleteideas.net/book/the-book-2nd.html).
- 🔴 [Hugging Face — The N Implementation Details of RLHF with PPO](https://huggingface.co/blog/the_n_implementation_details_of_rlhf_with_ppo) — the gap between the paper and a working implementation; humbling and instructive.
- 🔴 [Bai et al. (2022) — Constitutional AI](https://arxiv.org/abs/2212.08073) — replacing human feedback with AI feedback guided by principles (RLAIF).
- 🔴 [DeepSeek-AI (2025) — DeepSeek-R1](https://arxiv.org/abs/2501.12948) — the GRPO-based RL-for-reasoning result that reshaped the field; where post-training is heading beyond RLHF.
- 🟢 [Karpathy — Deep RL: Pong from Pixels](https://karpathy.github.io/2016/05/31/rl/) — a classic standalone intro to policy gradients; genuinely fun and gives you REINFORCE intuition in one read.

## Exercises & projects

- 🟢 Build a toy preference dataset for your Storyteller: generate 2 stories per prompt, label which is better (yourself, or with an LLM judge), producing ~500 chosen/rejected pairs.
- 🟡 **Storyteller milestone:** run DPO on your SFT model with TRL's `DPOTrainer` using that dataset; compare pre/post outputs on held-out prompts and look for both improvement and reward-hacking artifacts (e.g., length bias).
- 🟡 Implement REINFORCE from scratch on a toy task (following the Pong-from-Pixels post) so policy gradients aren't magic.
- 🔴 Train a reward model (a classification head on your base model) on your preference pairs, then evaluate: does its score ordering agree with your judgments on held-out pairs?
- 🔴 Full classic RLHF: use the reward model with TRL's PPO trainer on your Storyteller, monitor KL from the SFT model, and deliberately over-optimize to watch the model degenerate — then explain why the KL penalty exists.

---
[← Finetuning I: SFT](chapter14.md) | [Index](../COURSE.md) | [Next: Deployment →](chapter16.md)
