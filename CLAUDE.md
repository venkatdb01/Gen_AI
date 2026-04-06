# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a **learning roadmap and planning repository** for a personal journey into Gen AI and Agentic AI engineering. The primary artifact is `GenAI_Master_Roadmap.docx`, which defines a 5-phase, 15-project curriculum.

As projects are implemented, this repository will evolve from a planning repo into a multi-project implementation repo.

## Project Structure

Projects will be organized by phase as they are built:

```
Gen_AI/
├── GenAI_Master_Roadmap.docx   # Master learning plan
├── genai_roadmap.md            # Markdown version of roadmap
├── phase1/                     # LLM Foundations + Prompt Engineering (future)
├── phase2/                     # Embeddings + RAG Systems (future)
├── phase3/                     # LangChain + LangGraph + Agents (future)
├── phase4/                     # MCP Servers + HuggingFace + Fine-Tuning (future)
└── phase5/                     # Advanced Agentic AI + Production (future)
```

## Technology Stack (per roadmap)

Each phase introduces specific technologies:

- **Phase 1:** OpenAI API, Ollama (local LLMs), FastAPI, Streamlit, Python CLI
- **Phase 2:** ChromaDB, FAISS, Pinecone, RAGAS, HuggingFace embeddings
- **Phase 3:** LangChain, LangGraph, CrewAI (basics), LangSmith, LangFuse
- **Phase 4:** MCP protocol, HuggingFace Hub/Transformers, LoRA/QLoRA, PEFT, vLLM
- **Phase 5:** Multi-agent orchestration, Docker, AWS/GCP, LLM security (OWASP LLM Top 10)

## Expected Common Commands

As projects are added, commands will vary per project. The likely patterns:

```bash
# Python environment setup (per project)
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

# FastAPI projects
uvicorn main:app --reload

# Streamlit projects
streamlit run app.py

# Running tests
pytest tests/

# Docker (Phase 5)
docker build -t <project> . && docker run -p 8000:8000 <project>
```

## 15-Project Roadmap Summary

| Phase | Project | Description |
|-------|---------|-------------|
| 1 | P1: Smart Q&A CLI | CLI tool using OpenAI/Ollama API |
| 1 | P2: Prompt Playground | Experiment with prompting strategies |
| 2 | P3: Document Q&A | Basic RAG with vector store |
| 2 | P4: PDF Knowledge Base | Multi-doc RAG with chunking strategies |
| 2 | P5: Hybrid Search Engine | BM25 + vector search with reranking |
| 3 | P6: LangChain Chatbot | Memory-aware chatbot via LangChain |
| 3 | P7: Research Agent | ReAct agent with tool use |
| 3 | P8: Data Analysis Agent | Multi-step agentic pipeline |
| 4 | P9: Custom MCP Server | MCP protocol integration |
| 4 | P10: HF Model Explorer | HuggingFace Hub + Transformers |
| 4 | P11: Fine-Tuned Chatbot | LoRA/QLoRA domain fine-tuning |
| 5 | P12: Multi-Agent Research | CrewAI advanced orchestration |
| 5 | P13: Agentic Data Pipeline | Production-grade agent workflow |
| 5 | P14: Production RAG API | Deployed RAG with observability |
| 5 | P15: AI Startup Prototype | End-to-end production system |

## Notes

- SSH key files (`sshkey.docx`, `sshkey.docx.pub`) are tracked in git — remove them if they contain real credentials.
- Remote: https://github.com/venkatdb01/Gen_AI.git
