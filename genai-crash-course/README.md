# Generative AI & Agentic AI — 10-Hour Developer Crash Course

> **Who this is for:** Experienced software developers who want to understand, design, and build GenAI systems — without getting lost in math or ML theory.
>
> **What you'll walk away with:** The mental models, vocabulary, architecture patterns, and practical knowledge to contribute to or lead GenAI projects.

---

## Course Map

| Module | Topic | Time | File |
|--------|-------|------|------|
| 1 | What is Generative AI | 1h | [module-01.md](./module-01-what-is-generative-ai.md) |
| 2 | How LLMs Work (Conceptually) | 1.5h | [module-02.md](./module-02-how-llms-work.md) |
| 3 | Building Basic GenAI Applications | 1.5h | [module-03.md](./module-03-building-basic-genai-apps.md) |
| 4 | Retrieval Augmented Generation (RAG) | 2h | [module-04.md](./module-04-retrieval-augmented-generation.md) |
| 5 | Agentic AI Systems | 2h | [module-05.md](./module-05-agentic-ai-systems.md) |
| 6 | Multi-Agent and Workflow Systems | 1h | [module-06.md](./module-06-multi-agent-workflow-systems.md) |
| 7 | The GenAI Stack for Developers | 1h | [module-07.md](./module-07-genai-stack-for-developers.md) |
| 8 | Production Considerations | 1h | [module-08.md](./module-08-production-considerations.md) |
| — | Capstone System Designs | — | [capstone.md](./capstone-system-designs.md) |

**Total: ~10 hours of focused learning**

---

## How to Use This Course

1. **Read sequentially** — each module builds on the previous
2. **Study the diagrams** — every major concept has a visual representation
3. **Don't skip Module 4 (RAG)** — it's the most important architecture in production GenAI
4. **Do the capstone designs** — reading the system designs cements everything

---

## Quick Reference

### Key Concepts Cheatsheet

| Term | One-line definition |
|------|-------------------|
| Token | Atomic unit of text (~4 chars). Used for cost and limits. |
| Embedding | A vector of numbers representing semantic meaning of text. |
| Context Window | Max tokens an LLM can process in one call. |
| Temperature | Controls randomness: 0 = deterministic, 1 = creative. |
| Hallucination | When the model generates confident but wrong information. |
| RAG | Injecting retrieved documents into the prompt before generating. |
| Agent | LLM + tool-calling loop that acts autonomously. |
| Tool | A function the LLM can request to call. |
| Reranker | Model that re-scores retrieved chunks for relevance. |
| Guardrail | Safety check on LLM input or output. |

---

## What to Learn Next

| Track | Next Steps |
|-------|-----------|
| **RAG Engineer** | LlamaIndex advanced features, RAGAS evaluation, hybrid search tuning |
| **Agent Builder** | LangGraph deep dive, OpenAI Assistants API, memory architectures |
| **ML Fundamentals** | Andrej Karpathy's "Let's build GPT", fast.ai courses |
| **Production Systems** | OWASP LLM Top 10, FinOps for LLMs, eval pipelines |
| **Multimodal** | Vision + text models, image embeddings, Whisper for audio |
