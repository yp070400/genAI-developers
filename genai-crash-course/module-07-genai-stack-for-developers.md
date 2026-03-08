# Module 7 — The GenAI Stack for Developers

**Estimated time: 1 hour**

---

## 7.1 The Full Stack

```
┌─────────────────────────────────────────────────────────────────┐
│                         USER INTERFACE                          │
│              (Web, Mobile, CLI, Slack, API)                     │
├─────────────────────────────────────────────────────────────────┤
│                      APPLICATION LAYER                          │
│   (Your business logic, orchestration, prompt management)       │
├───────────────────────┬─────────────────────────────────────────┤
│   AGENT FRAMEWORKS    │         MEMORY & STORAGE                │
│   LangChain           │   Conversation: Redis/Postgres          │
│   LangGraph           │   Vector: Pinecone/Weaviate/pgvector    │
│   CrewAI              │   Files: S3 / local filesystem          │
│   AutoGen             │   Cache: Redis                          │
├───────────────────────┼─────────────────────────────────────────┤
│   LLM GATEWAY         │         EMBEDDING MODELS                │
│   LiteLLM             │   OpenAI text-embedding-3               │
│   OpenRouter          │   Cohere embed-v3                       │
│   Portkey             │   Voyage AI                             │
├───────────────────────┴─────────────────────────────────────────┤
│                        LLM PROVIDERS                            │
│  OpenAI (GPT-4o)  |  Anthropic (Claude)  |  Google (Gemini)    │
│  Cohere  |  Mistral  |  Meta (Llama)  |  AWS Bedrock           │
├─────────────────────────────────────────────────────────────────┤
│                       OBSERVABILITY                             │
│          LangSmith  |  Langfuse  |  Arize  |  Helicone         │
└─────────────────────────────────────────────────────────────────┘
```

---

## 7.2 LLM Providers

```
PROVIDER COMPARISON
────────────────────────────────────────────────────────────────────
OpenAI
  Models:     GPT-4o, GPT-4o-mini, o1, o3
  Strengths:  Best ecosystem, function calling, structured outputs
  Use for:    General purpose, most third-party integrations

Anthropic
  Models:     Claude 3.5 Sonnet, Claude 3 Haiku, Claude Opus 4
  Strengths:  Long context (200K), strong reasoning, safety
  Use for:    Document processing, coding, complex reasoning

Google
  Models:     Gemini 1.5 Pro, Gemini 1.5 Flash
  Strengths:  Massive context (1M), multimodal, cheap
  Use for:    Very long documents, multimodal (image + text)

Meta / Llama 3
  Models:     Llama 3.1 405B, 70B, 8B
  Strengths:  Open source, self-hostable, no data retention
  Use for:    Privacy-sensitive workloads, cost control at scale

Mistral
  Models:     Mistral Large, Mixtral 8x22B
  Strengths:  European provider, strong multilingual
  Use for:    EU data residency requirements

Cohere
  Models:     Command R+
  Strengths:  Native RAG features, strong retrieval
  Use for:    RAG-heavy applications
────────────────────────────────────────────────────────────────────
```

**Model tier guide:**

```
TASK → MODEL TIER MATCHING
─────────────────────────────────────────────────────────────────
Complex reasoning, multi-step tasks    → GPT-4o / Claude Sonnet
Simple classification, short answers  → GPT-4o-mini / Claude Haiku
Deep document analysis (200K+ tokens) → Claude Sonnet
Multimodal (images + text)             → GPT-4o Vision / Gemini
Privacy-critical, self-hosted          → Llama 3 (self-hosted)
Cost-optimized at scale                → GPT-4o-mini / Gemini Flash
─────────────────────────────────────────────────────────────────
```

---

## 7.3 Vector Databases

```
VECTOR DATABASE COMPARISON
────────────────────────────────────────────────────────────────────
Pinecone
  Type:        Managed cloud service
  Strengths:   Zero ops, fast, reliable, mature
  Use when:    You want hosted, no-maintenance solution
  Limitation:  Cost at scale

Weaviate
  Type:        Open source / managed
  Strengths:   Built-in embedding models, hybrid search native
  Use when:    You want self-hosted with rich feature set

Qdrant
  Type:        Open source / managed
  Strengths:   High performance, filtering, Rust-based
  Use when:    Performance-critical applications

Chroma
  Type:        Open source
  Strengths:   Extremely simple to use, local dev
  Use when:    Local development, prototyping

pgvector (PostgreSQL extension)
  Type:        Open source extension
  Strengths:   Already in your Postgres! Familiar tooling
  Use when:    < 1M vectors, existing Postgres infrastructure

Redis Vector
  Type:        Extension to Redis
  Strengths:   In-memory speed, already in your stack
  Use when:    Speed-critical, combined with caching needs
────────────────────────────────────────────────────────────────────
```

**Recommendation for most teams:**

```
START HERE                        SCALE TO
──────────────────────────────    ──────────────────────────────
pgvector                          Pinecone or Qdrant
  (if you have Postgres)            (when > 1M vectors or need
                                     managed ops)

Chroma                            Weaviate
  (local dev / prototyping)         (self-hosted with rich features)
```

---

## 7.4 Agent Frameworks

```
FRAMEWORK DECISION TREE
─────────────────────────────────────────────────────────────────
Simple RAG app?
  → Use LangChain (well-documented, huge ecosystem)

Complex stateful workflows with branching?
  → Use LangGraph (visual graph-based orchestration)

Need specialized role-based agents?
  → Use CrewAI (easiest for role-based multi-agent)

Conversational multi-agent with code execution?
  → Use AutoGen (Microsoft, strong for code-gen agents)

Building your own orchestration?
  → Use LiteLLM for the LLM abstraction layer
  → Handle agent loop and tool calling yourself
─────────────────────────────────────────────────────────────────
```

**LangChain ecosystem overview:**

```
LangChain ecosystem
├── langchain-core          Core abstractions (chains, prompts, parsers)
├── langchain-community     100s of integrations (DBs, APIs, tools)
├── langchain-openai        OpenAI-specific integrations
├── langchain-anthropic     Anthropic-specific integrations
├── langgraph               Stateful agent workflows (graph-based)
└── langserve               Deploy LangChain apps as REST APIs
```

---

## 7.5 Observability Tools

This is the most underrated layer. You cannot improve what you cannot measure.

```
WHAT TO OBSERVE IN GenAI SYSTEMS
────────────────────────────────────────────────────────────────
LangSmith (by LangChain)
  - Full trace of every LLM call + tool call
  - Prompt comparison and testing
  - Dataset management for evals

Langfuse (open source)
  - Traces, spans, generations
  - Cost tracking per user/feature
  - Prompt versioning
  - Evaluation datasets

Arize / Phoenix
  - Production monitoring
  - Drift detection
  - LLM-as-judge evaluation

Helicone
  - LLM API proxy with logging
  - Cost analytics
  - Rate limiting and caching
────────────────────────────────────────────────────────────────
```

**What a good trace looks like:**

```
REQUEST TRACE
─────────────────────────────────────────────────────────────────
request_id:     req_abc123
user_id:        user_456
timestamp:      2024-01-15 14:32:11

  [SPAN] rag_pipeline                          total: 2.3s
    [SPAN] embed_query                           22ms
    [SPAN] vector_search (top_k=10)             145ms
    [SPAN] rerank                               203ms
    [SPAN] llm_call                            1,847ms
      model:      gpt-4o
      input_tokens:  2,341
      output_tokens:   287
      cost:          $0.038

  final_answer:   [logged]
  user_feedback:  thumbs_up
─────────────────────────────────────────────────────────────────
```

---

## 7.6 Development Toolkit Summary

| Layer | Recommended Tools |
|-------|------------------|
| LLM API | OpenAI SDK, Anthropic SDK, or LiteLLM (multi-provider) |
| Prompt Management | LangChain PromptTemplate, Langfuse |
| Embeddings | OpenAI text-embedding-3-small, Cohere |
| Vector DB | pgvector (start), Pinecone/Qdrant (scale) |
| RAG Framework | LangChain, LlamaIndex |
| Agent Framework | LangGraph, CrewAI |
| Observability | Langfuse or LangSmith |
| Structured Output | Instructor (Python) / Zod (TypeScript) |
| Evaluation | RAGAS (RAG eval), DeepEval |

---

## 7.7 Avoiding Vendor Lock-in

```
LOCK-IN RISK MITIGATION
─────────────────────────────────────────────────────────────────
LLM Providers:
  Use LiteLLM as an abstraction layer
  One API, 100+ models from any provider
  Switch providers by changing one config value

Vector DBs:
  Use LangChain or LlamaIndex vector store abstraction
  Same code works with Pinecone, Weaviate, pgvector, etc.

Embeddings:
  Encapsulate embedding calls behind an interface
  Re-embedding is expensive if you switch models
  Document which model version was used for each index

Frameworks:
  Keep business logic separate from framework code
  LangChain changes APIs frequently — don't tightly couple
─────────────────────────────────────────────────────────────────
```

---

## Key Takeaways — Module 7

- The GenAI stack has distinct layers: UI → App → Frameworks → LLMs → Observability
- Choose your LLM provider based on your actual requirements (context length, cost, compliance)
- Start with pgvector before committing to a specialized vector database
- LangChain is the backbone of most RAG apps; LangGraph for complex agentic workflows
- Observability is non-negotiable in production — trace every LLM call and tool execution
- Use an abstraction layer (LiteLLM) to avoid vendor lock-in

---

**Next:** [Module 8 — Production Considerations](./module-08-production-considerations.md)
