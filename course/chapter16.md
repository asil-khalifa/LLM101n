# Chapter 16 — Deployment

> Goal: ship the Storyteller — wrap it in an API with streaming, put a chat UI on it, and understand what production serving engines add on top.

## Core path (study in order)

1. 🟢 [FastAPI Tutorial](https://fastapi.tiangolo.com/tutorial/) — the standard Python web framework; work through the basics up to request bodies and async endpoints.
2. 🟢 [MDN — Server-sent events](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events) — the streaming mechanism behind the "tokens appearing one by one" ChatGPT effect.
3. 🟢 [Gradio Quickstart](https://www.gradio.app/guides/quickstart) — the fastest path from model to shareable chat UI (see also its [ChatInterface guide](https://www.gradio.app/guides/creating-a-chatbot-fast)).
4. 🟡 [Hugging Face Spaces docs](https://huggingface.co/docs/hub/spaces) — free hosting for your Gradio app; how the world can actually use your Storyteller.
5. 🟡 [vLLM documentation](https://docs.vllm.ai/en/latest/) — what a real serving engine provides: continuous batching, PagedAttention (from Chapter 12), and an OpenAI-compatible API server.

## Going deeper (optional)

- 🟡 [Ollama](https://ollama.com/) and the [llama.cpp server](https://github.com/ggml-org/llama.cpp/tree/master/tools/server) — the local-first deployment path for GGUF models from Chapter 13.
- 🔴 [Hugging Face — text-generation-inference](https://github.com/huggingface/text-generation-inference) — a second production server to compare against vLLM (both readmes are educational about what serving requires).
- 🔴 [OpenAI API reference — Chat Completions](https://platform.openai.com/docs/api-reference/chat) — the de-facto API contract; design your endpoint to match it and every client tool works with your model.
- 🔴 [Chip Huyen — Designing Machine Learning Systems (book site)](https://huyenchip.com/books/) — the wider production-ML picture: monitoring, feedback loops, iteration.

## Exercises & projects

- 🟢 Wrap your Storyteller in a FastAPI `POST /generate` endpoint that streams tokens via SSE; test it with `curl -N`.
- 🟡 **Storyteller milestone (capstone):** build the full ChatGPT-style app — chat UI (Gradio, or hand-rolled HTML/JS talking to your SSE endpoint), conversation history using your Chapter 14 chat template, temperature/top-p controls — and deploy it on a Hugging Face Space.
- 🟡 Make your endpoint OpenAI-compatible (`/v1/chat/completions` with the standard request/response schema), then point an off-the-shelf client library at your server to prove it works.
- 🔴 Load-test it: fire 50 concurrent requests, measure p50/p99 latency and tokens/sec, then implement simple request batching in your server and measure the improvement.
- 🔴 Serve the same model three ways — your FastAPI server, vLLM, and llama.cpp — and write a short comparison of throughput, latency, and operational effort.

---
[← Finetuning II: RL](chapter15.md) | [Index](../COURSE.md) | [Next: Multimodal →](chapter17.md)
