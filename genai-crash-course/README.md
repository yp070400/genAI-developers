# Generative AI & Agentic AI — 10-Hour Developer Crash Course

> **Who this is for:** Experienced software developers who want to understand, design, and build GenAI systems — without getting lost in math or ML theory.
>
> **What you'll walk away with:** The mental models, vocabulary, architecture patterns, and practical knowledge to design and implement production GenAI systems.

---

## Course Map

| Module | Topic | Time | File |
|--------|-------|------|------|
| 1 | What is Generative AI | 1h | [module-01.md](./module-01-what-is-generative-ai.md) |
| 2 | How LLMs Work (Conceptually) | 1.5h | [module-02.md](./module-02-how-llms-work.md) |
| 3 | Building Basic GenAI Applications + **Context Engineering** | 1.5h | [module-03.md](./module-03-building-basic-genai-apps.md) |
| 4 | Retrieval Augmented Generation (RAG) | 2h | [module-04.md](./module-04-retrieval-augmented-generation.md) |
| 5 | Agentic AI Systems + **Deterministic vs. Autonomous Agents** | 2h | [module-05.md](./module-05-agentic-ai-systems.md) |
| 6 | Multi-Agent and Workflow Systems | 1h | [module-06.md](./module-06-multi-agent-workflow-systems.md) |
| 7 | The GenAI Stack for Developers | 1h | [module-07.md](./module-07-genai-stack-for-developers.md) |
| 8 | Production Considerations + **GenAI Security** | 1h | [module-08.md](./module-08-production-considerations.md) |
| 9 | **GenAI System Design Patterns** *(new)* | 30min | [module-09.md](./module-09-genai-design-patterns.md) |
| — | Capstone System Designs *(4 designs, with failure modes & costs)* | — | [capstone.md](./capstone-system-designs.md) |

**Total: ~10.5 hours of focused learning**

---

## How to Use This Course

1. **Read sequentially** — each module builds on the previous
2. **Study the diagrams** — every major concept has a visual representation
3. **Don't skip Module 4 (RAG)** — it's the most important architecture in production GenAI
4. **Read Module 9 after Module 6** — it synthesizes all patterns into a design decision framework
5. **Work through the capstone designs** — each includes architecture, reasoning, failure modes, and cost

---

## What's New (v2)

| Enhancement | Location |
|------------|----------|
| Context Engineering — what it is, how to assemble it, position effects | Module 3 §3.8 |
| Deterministic Workflows vs. Autonomous Agents — the production-critical distinction | Module 5 §5.10 |
| GenAI Security — prompt injection, data exfiltration, tool misuse, jailbreak | Module 8 §8.9 |
| GenAI System Design Patterns — the 5-pattern framework for every system | Module 9 (new) |
| Capstone: failure modes + scalability + cost for all 3 original designs | Capstone |
| Capstone Design 4: AI Code Review Assistant | Capstone |

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
| Context Engineering | Deciding what to include, exclude, compress, and order in the context window. |
| Agent | LLM + tool-calling loop that acts autonomously. |
| Tool | A function the LLM can request to call. |
| ReAct | Reason-then-Act pattern: explicit thought before each tool call. |
| Reranker | Model that re-scores retrieved chunks for relevance. |
| Guardrail | Safety check on LLM input or output. |
| Prompt Injection | Attack where user input overrides your system instructions. |
| Deterministic Workflow | A workflow where code (not the LLM) controls the execution path. |

---

### The 5 GenAI Design Patterns

| Pattern | Use When | Complexity |
|---------|----------|-----------|
| Simple LLM App | Task doesn't need your data or external actions | Low |
| RAG | Task needs domain knowledge or current information | Medium |
| Tool-Using LLM | Task needs real-time data or system integration | Medium |
| Agent Loop | Task requires multi-step autonomous reasoning | High |
| Multi-Agent | Task too large for one agent; benefits from specialization | Very High |

> Always start with the simplest pattern that could work.

---

## What to Learn Next

| Track | Next Steps |
|-------|-----------|
| **RAG Engineer** | LlamaIndex advanced features, RAGAS evaluation, hybrid search tuning |
| **Agent Builder** | LangGraph deep dive, OpenAI Assistants API, memory architectures |
| **ML Fundamentals** | Andrej Karpathy's "Let's build GPT", fast.ai courses |
| **Production Systems** | OWASP LLM Top 10, FinOps for LLMs, eval pipelines |
| **Security** | OWASP LLM Top 10, Llama Guard, Rebuff |
| **Multimodal** | Vision + text models, image embeddings, Whisper for audio |