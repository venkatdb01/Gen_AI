# Gen AI & Agentic AI Engineering — Master Roadmap

A 5-phase, 15-project learning journey from LLM fundamentals to production-ready agentic systems.

---

## Phase 1: LLM Foundations + Prompt Engineering
**Duration:** 4–6 weeks

### Goals
- Understand how LLMs work internally
- Master prompt engineering techniques
- Build first working AI-powered app

### Key Skills
- Tokens, context windows, temperature, top-p sampling
- System vs user prompts
- Zero-shot, few-shot, chain-of-thought prompting
- OpenAI API usage
- Running local LLMs with Ollama
- Building CLI tools in Python
- Basic FastAPI and Streamlit

### Skill Set Gained
| Skill | Level |
|-------|-------|
| Prompt Engineering | Intermediate |
| OpenAI API | Intermediate |
| Ollama (local LLMs) | Beginner |
| Python CLI development | Intermediate |
| FastAPI basics | Beginner |
| Streamlit basics | Beginner |

### Projects
- **P1: Smart Q&A CLI Tool** — Command-line tool that queries OpenAI/Ollama with various prompting strategies
- **P2: Prompt Engineering Playground** — Interactive app to experiment with prompt templates, temperature, and model comparisons

---

## Phase 2: Embeddings + RAG Systems
**Duration:** 5–7 weeks

### Goals
- Build complete Retrieval-Augmented Generation (RAG) pipelines
- Understand vector search deeply
- Evaluate RAG system quality

### Key Skills
- Embeddings and vector similarity (cosine, dot product, euclidean)
- Document chunking strategies (fixed, semantic, recursive)
- Vector stores: ChromaDB, FAISS, Pinecone
- Semantic search and hybrid search (BM25 + vector)
- Reranking with cross-encoders
- RAG evaluation with RAGAS framework
- HuggingFace embedding models

### Skill Set Gained
| Skill | Level |
|-------|-------|
| Embeddings & vector math | Intermediate |
| ChromaDB | Intermediate |
| FAISS | Intermediate |
| Pinecone | Beginner |
| RAG pipeline design | Intermediate |
| Hybrid search (BM25 + vector) | Intermediate |
| Reranking | Beginner |
| RAGAS evaluation | Beginner |
| HuggingFace embeddings | Beginner |

### Projects
- **P3: Document Q&A System** — Basic RAG pipeline with a vector store and OpenAI
- **P4: PDF Knowledge Base** — Multi-document RAG with advanced chunking and metadata filtering
- **P5: Hybrid Search Engine** — BM25 + vector search with reranking for improved retrieval

---

## Phase 3: LangChain + LangGraph + Agent Basics
**Duration:** 5–7 weeks

### Goals
- Move from raw API calls to agent frameworks
- Build autonomous agents that use tools
- Add observability to AI systems

### Key Skills
- LangChain chains, memory, and tools
- LangGraph state machines and conditional edges
- ReAct (Reasoning + Acting) pattern
- Tool calling and function calling
- LangSmith and LangFuse for tracing/observability
- CrewAI basics for multi-agent coordination

### Skill Set Gained
| Skill | Level |
|-------|-------|
| LangChain | Intermediate |
| LangGraph | Intermediate |
| ReAct agent pattern | Intermediate |
| Tool/function calling | Intermediate |
| LangSmith observability | Beginner |
| LangFuse observability | Beginner |
| CrewAI (basics) | Beginner |
| Agent memory management | Beginner |

### Projects
- **P6: LangChain-powered Chatbot** — Memory-aware conversational agent using LangChain
- **P7: Research Agent with Tools** — ReAct agent with web search, calculator, and code execution tools
- **P8: Multi-step Data Analysis Agent** — Agent that autonomously plans and executes data analysis tasks

---

## Phase 4: MCP Servers + Hugging Face + Fine-Tuning
**Duration:** 6–8 weeks

### Goals
- Build production integrations using the MCP protocol
- Leverage open-source models from HuggingFace
- Fine-tune a model for a specific domain

### Key Skills
- Model Context Protocol (MCP) — architecture and custom server development
- HuggingFace Hub: model cards, datasets, inference API
- HuggingFace Transformers library
- LoRA and QLoRA parameter-efficient fine-tuning
- PEFT library
- Model evaluation metrics (BLEU, ROUGE, perplexity)
- vLLM for fast local inference

### Skill Set Gained
| Skill | Level |
|-------|-------|
| MCP protocol | Intermediate |
| Custom MCP server development | Intermediate |
| HuggingFace Hub & Transformers | Intermediate |
| LoRA fine-tuning | Intermediate |
| QLoRA (quantized fine-tuning) | Intermediate |
| PEFT library | Intermediate |
| Model evaluation | Intermediate |
| vLLM inference | Beginner |

### Projects
- **P9: Custom MCP Server** — Build and integrate a custom MCP server exposing domain-specific tools
- **P10: HuggingFace Model Explorer** — Tool to browse, compare, and run inference on HF models
- **P11: Fine-Tuned Domain Chatbot** — LoRA/QLoRA fine-tuned model on a custom domain dataset

---

## Phase 5: Advanced Agentic AI + Production + Startup Ready
**Duration:** 6–8 weeks

### Goals
- Build production-grade multi-agent systems
- Deploy AI applications to the cloud
- Build a portfolio-ready end-to-end AI product

### Key Skills
- Multi-agent orchestration patterns
- CrewAI advanced features (roles, delegation, memory)
- Agentic RAG (agents that decide when/how to retrieve)
- Long-term and short-term agent memory systems
- Advanced token optimization (caching, batching, compression)
- Docker containerization for AI apps
- Cloud deployment: AWS / GCP / HuggingFace Spaces
- LLM security: OWASP LLM Top 10, prompt injection defense
- CI/CD for AI systems

### Skill Set Gained
| Skill | Level |
|-------|-------|
| Multi-agent orchestration | Intermediate |
| CrewAI (advanced) | Intermediate |
| Agentic RAG | Intermediate |
| Agent memory systems | Intermediate |
| Token optimization | Intermediate |
| Docker for AI apps | Intermediate |
| AWS / GCP deployment | Intermediate |
| HuggingFace Spaces | Intermediate |
| LLM security (OWASP Top 10) | Intermediate |
| CI/CD for AI | Beginner |

### Projects
- **P12: Multi-Agent Research System** — CrewAI-powered agents that collaboratively research and synthesize topics
- **P13: Agentic Data Pipeline** — Production-grade agent that autonomously ingests, transforms, and stores data
- **P14: Production RAG API** — Fully deployed RAG service with monitoring, logging, and observability
- **P15: End-to-End AI Startup Prototype** — Full product with frontend, backend, agents, RAG, fine-tuning, and cloud deployment

---

## Quick Reference

| Phase | Duration | Focus | Projects |
|-------|----------|-------|---------|
| 1 | 4–6 weeks | LLM Foundations + Prompt Engineering | P1, P2 |
| 2 | 5–7 weeks | Embeddings + RAG Systems | P3, P4, P5 |
| 3 | 5–7 weeks | LangChain + LangGraph + Agents | P6, P7, P8 |
| 4 | 6–8 weeks | MCP + HuggingFace + Fine-Tuning | P9, P10, P11 |
| 5 | 6–8 weeks | Advanced Agentic AI + Production | P12, P13, P14, P15 |
| **Total** | **26–36 weeks** | | **15 projects** |

---

## Cumulative Skill Progression

By the end of all 5 phases, you will have working knowledge of:

**APIs & Models**
- OpenAI API, Ollama, HuggingFace Inference API, vLLM

**Frameworks & Libraries**
- LangChain, LangGraph, CrewAI, PEFT, Transformers, RAGAS

**Vector Stores & Search**
- ChromaDB, FAISS, Pinecone, BM25 hybrid search

**Protocols & Integrations**
- MCP (Model Context Protocol), function/tool calling

**Observability**
- LangSmith, LangFuse

**Deployment & Infrastructure**
- FastAPI, Streamlit, Docker, AWS, GCP, HuggingFace Spaces

**Security**
- OWASP LLM Top 10, prompt injection defense
