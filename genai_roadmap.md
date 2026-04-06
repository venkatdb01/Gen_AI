# AI / LLM Engineer Learning Roadmap

**Goal:** Transition from Data Engineering → LLM/AI Engineer
**Style:** Hands-on projects with books as reference
**Pace:** 10–15 hours/week
**Estimated Total Duration:** 9–11 months (updated with agentic AI deep-dive)

---

## How This Roadmap Works

Each phase follows the same structure:

- **Concepts** — what you need to understand
- **Hands-on Project** — what you'll build (this is your primary learning vehicle)
- **Resources** — books, docs, courses to reference while building
- **Claude Integration** — how Claude fits into that phase
- **Checkpoint** — how you know you're ready for the next phase

The phases are sequential. Don't skip ahead — each one builds muscle memory for the next.

---

## Phase 0: Python & API Foundations (Weeks 1–3)

> You're entry-level Python. That's fine — but LLM engineering requires comfortable, fluent Python. Not expert. Fluent.

### Concepts to Learn

- Python data structures beyond basics: list comprehensions, dict comprehensions, defaultdict, Counter
- Functions as first-class objects: passing functions, lambda, map/filter
- Working with JSON: parsing, nested access, serialization
- HTTP and REST APIs: requests library, status codes, headers, authentication
- Async basics: what async/await means, why it matters for API calls (conceptual understanding is enough)
- Environment management: virtual environments (venv), pip, .env files for API keys
- Error handling: try/except patterns, especially for API calls and retries

### Hands-on Project

**Build a "Daily Briefing" CLI tool:**

- Calls a free weather API + a free news API
- Parses JSON responses
- Formats and prints a clean daily summary
- Handles API errors gracefully
- Stores API keys in .env file (use python-dotenv)

This is intentionally not an AI project — it builds the exact Python + API muscles you'll use in every phase after this.

### Resources

- Python official tutorial (docs.python.org) — sections on data structures, modules, errors
- Real Python articles on: requests library, working with JSON, environment variables
- Your existing Python knowledge from PySpark work — list/dict operations transfer directly

### Checkpoint

You're ready for Phase 1 when you can:

- Call any REST API, parse the JSON response, and extract nested fields without looking up syntax
- Handle errors in API calls (timeouts, 4xx, 5xx) with retry logic
- Explain what an API key is, why it goes in .env, and how to load it

---

## Phase 1: Understanding LLMs — What They Are and How to Use Them (Weeks 4–7)

> Before you build with LLMs, you need a solid mental model of what they actually are, what they can and can't do, and how to interact with them through APIs.

### Concepts to Learn

**How LLMs work (conceptual, no math required):**

- What a language model does: next-token prediction
- Training process at a high level: pre-training on internet text → fine-tuning → RLHF/RLAIF
- Tokens: what they are, how tokenization works, why token count matters
- Context window: what it is, why it limits what you can do, how different models vary
- Temperature, top-p, max_tokens: what each parameter controls and when to adjust them
- Inference vs. training: the distinction and why it matters

**The model landscape:**

- Claude (Anthropic): Opus, Sonnet, Haiku — when to use which
- GPT (OpenAI): GPT-4o, GPT-4-turbo — capabilities and tradeoffs
- Open-source models: Llama, Mistral, Gemma — why they matter, when to choose them
- Cost vs. quality vs. speed tradeoffs between models

**LLM API basics:**

- Message format: system / user / assistant roles
- Streaming vs. non-streaming responses
- Token counting and cost estimation
- Rate limits and how to handle them

### Hands-on Project

**Build an "LLM Playground" — a Python CLI that lets you:**

1. Switch between Claude API and OpenAI API with a flag
2. Set system prompts, temperature, max_tokens from the command line
3. Have a multi-turn conversation (maintain message history)
4. Count and display tokens used + estimated cost per message
5. Save conversation history to a JSON file

This project forces you to understand the API structure, message formatting, and parameter effects by experimenting directly.

### Resources

- **Anthropic documentation** (docs.anthropic.com) — Messages API guide, model comparison page
- **Anthropic's prompt engineering tutorial** (docs.anthropic.com/en/docs/build-with-claude/prompt-engineering)
- **Book:** AI Engineering by Chip Huyen — Chapters 1–3 (foundation model landscape, understanding LLMs)
- **3Blue1Brown YouTube:** "But what is a GPT?" and "Attention in Transformers" — best visual explanations of how LLMs work, no math required
- **Andrej Karpathy YouTube:** "Intro to Large Language Models" (1 hour) — builds intuition fast

### Claude Integration

- Use the Claude API (Anthropic SDK for Python) as your primary API throughout
- Experiment with Claude's system prompt behavior — it's more instruction-following than other models
- Compare Claude Sonnet vs. Haiku responses for the same prompts — understand quality/cost tradeoff

### Checkpoint

You're ready for Phase 2 when you can:

- Explain to a non-technical person what an LLM does and how it generates text
- Call the Claude API with custom system prompts, temperature, and handle the response
- Articulate why you'd choose Sonnet over Haiku (or vice versa) for a given task
- Explain what a context window is and why a 200K context window matters differently than a 8K one

---

## Phase 2: Prompt Engineering & Contextual Engineering (Weeks 8–11)

> This is where most people stop — they learn "write good prompts" and think they're done. Real prompt engineering is systematic, testable, and deeply tied to how you structure context. Contextual engineering (a newer term) expands this to include everything that goes into the context window: instructions, examples, retrieved documents, tool definitions, conversation history.

### Concepts to Learn

**Prompt Engineering — Systematic Approach:**

- Zero-shot vs. few-shot prompting: when each works and when it doesn't
- Chain-of-thought (CoT) prompting: asking the model to reason step by step
- Role prompting: assigning the model a persona/role and why this changes behavior
- Output formatting: instructing the model to respond in JSON, XML, markdown, specific structures
- Negative prompting: telling the model what NOT to do (often more effective than positive instructions)
- Prompt chaining: breaking complex tasks into sequential prompt calls, each feeding the next

**Contextual Engineering — The Bigger Picture:**

- System prompts: designing effective system-level instructions
- Context window management: what goes in, in what order, and why order matters
- Structured input: using XML tags, delimiters, and sections to organize context (Claude responds very well to XML-structured prompts)
- Example selection: choosing the right few-shot examples and why bad examples hurt more than no examples
- Dynamic context: programmatically assembling prompts based on the situation (this is the bridge to RAG)

**Evaluation:**

- How to test whether Prompt A is better than Prompt B
- Building simple evaluation harnesses: run N examples, score outputs, compare
- Common failure modes: hallucination, instruction drift, format breaking

### Hands-on Project

**Build a "Document Analyzer" that takes any text document and:**

1. Summarizes it at 3 different detail levels (1-line, paragraph, full page) based on a parameter
2. Extracts structured data (key entities, dates, numbers, decisions) into JSON
3. Generates 5 questions someone should ask after reading the document
4. Answers those questions using only the document content (no hallucination)
5. Has an evaluation mode: feed it 10 documents with known correct answers and score accuracy

**Critical learning here:**

- You'll iterate on prompts dozens of times
- You'll learn that small wording changes produce dramatically different outputs
- The evaluation harness teaches you to think like an engineer, not just a prompt tweaker

### Resources

- **Anthropic's Prompt Engineering Guide** — the most comprehensive free resource: https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering
- **Book:** AI Engineering by Chip Huyen — Chapter on prompt engineering
- **Anthropic Cookbook** (GitHub) — practical prompt engineering examples
- **Claude's own ability** — literally ask Claude to help you improve your prompts. Use Claude to critique your prompt designs. This is meta-learning that actually works.
- **Simon Willison's blog** (simonwillison.net) — practical, grounded prompt engineering writing

### Claude Integration

- Claude excels with XML-tagged structured inputs — practice this extensively
- Use Claude's extended thinking feature (if available via API) to see chain-of-thought reasoning
- Use Claude to evaluate your own prompts: "Here's my prompt and the output. How would you improve this prompt?"

### Checkpoint

You're ready for Phase 3 when you can:

- Given a complex task, design a multi-step prompt chain without trial-and-error guessing
- Structure a system prompt with XML tags that consistently produces formatted output
- Build a simple eval harness that scores prompt quality across multiple test cases
- Explain the difference between prompt engineering and contextual engineering

---

## Phase 3: Tool Use, Function Calling & Structured Outputs (Weeks 12–14)

> This is the bridge between "LLMs generate text" and "LLMs take actions." Tool use is the foundation of everything agentic.

### Concepts to Learn

- **Function calling / Tool use:** How to define tools (functions) the LLM can call, how the LLM decides when to call them, and how to handle the results
- **Structured outputs:** Forcing the LLM to return valid JSON conforming to a schema
- **The tool-use loop:** User → LLM → tool call → tool result → LLM → response (understand this cycle deeply)
- **Tool design:** What makes a good tool definition — clear names, precise descriptions, well-typed parameters
- **Error handling in tool use:** What happens when a tool fails, how to let the LLM recover
- **MCP (Model Context Protocol):** Anthropic's open standard for connecting LLMs to external tools and data sources — this is becoming the industry standard

### Hands-on Project

**Build a "Personal Data Assistant" that:**

1. Connects to your own data (CSV files, a SQLite database, or a simple API)
2. Has tools defined for: querying data, creating charts (using matplotlib), calculating statistics, writing summaries
3. Takes natural language questions ("What were my top 5 expenses last month?") and uses the right tools to answer
4. Handles multi-step tool use (query data → calculate → generate chart → explain)

**Stretch goal:** Package one of your tools as an MCP server that Claude Desktop can connect to.

### Resources

- **Anthropic Tool Use docs** — https://docs.anthropic.com/en/docs/build-with-claude/tool-use
- **Anthropic MCP documentation** — https://modelcontextprotocol.io/
- **Book:** AI Engineering by Chip Huyen — chapters on tool use and agents
- **MCP GitHub repo** — examples of MCP server implementations

### Claude Integration

- Claude has native tool use built into its API — this is your primary implementation
- Build your first MCP server and connect it to Claude Desktop — this is a powerful way to understand the tool-use paradigm
- Explore how Claude decides between multiple available tools

### Checkpoint

You're ready for Phase 4 when you can:

- Define a set of tools in the Claude API and have the model correctly choose and call them
- Handle the full tool-use loop including multi-step tool chains
- Explain what MCP is and why it matters for the AI ecosystem
- Build a simple MCP server from scratch

---

## Phase 4: RAG — Retrieval-Augmented Generation (Weeks 15–20)

> RAG is the most in-demand skill in enterprise AI right now. This is where your data engineering background becomes a massive advantage — RAG is fundamentally a data pipeline problem.

### Concepts to Learn

**Embeddings:**

- What embeddings are: turning text into numerical vectors that capture meaning
- Embedding models: OpenAI embeddings, Cohere, open-source (sentence-transformers)
- Similarity search: cosine similarity, how "nearest neighbors" works conceptually

**Vector Databases:**

- What they are and why regular databases don't work for similarity search
- Options: ChromaDB (simple/local), Pinecone (managed), Weaviate, Qdrant, pgvector
- Indexing strategies: HNSW, IVF — conceptual understanding of tradeoffs

**The RAG Pipeline:**

- Document loading: PDFs, web pages, databases, APIs
- Chunking strategies: fixed-size, semantic, recursive — why chunking is the most underrated part of RAG
- Embedding and indexing: turning chunks into vectors and storing them
- Retrieval: query → embed → search → return top-K chunks
- Generation: feeding retrieved chunks into the LLM's context with a well-designed prompt
- The full loop: query → retrieve → augment prompt → generate → respond

**Advanced RAG:**

- Hybrid search: combining vector search with keyword (BM25) search
- Re-ranking: using a second model to re-order retrieved results
- Query transformation: rewriting the user's query for better retrieval
- Evaluation: measuring retrieval quality (recall@K, precision) and generation quality (faithfulness, relevance)
- Chunking experiments: why changing your chunk size from 512 to 1024 tokens can dramatically change results

### Hands-on Project

**Build a "Knowledge Base Q&A System":**

1. Ingest 20–50 documents (PDFs, markdown files — use your team's documentation or any domain you know well)
2. Implement chunking with at least 2 different strategies and compare results
3. Store embeddings in ChromaDB (start simple)
4. Build a retrieval pipeline that finds relevant chunks for a query
5. Feed retrieved chunks into Claude with a well-designed RAG prompt
6. Add a simple evaluation: 20 questions with known answers, measure accuracy
7. Iterate: try different chunk sizes, overlap, embedding models, and track what improves quality

**This project alone could take 4–6 weeks and that's fine.** RAG is where you'll spend the most time in real production work.

### Resources

- **Book:** AI Engineering by Chip Huyen — RAG chapters (this is the best treatment of RAG in book form)
- **LangChain documentation** — RAG tutorials and components
- **Anthropic Cookbook** — RAG examples with Claude
- **ChromaDB documentation** — getting started guide
- **Book (reference):** NLP Cookbook — the text processing recipes (tokenization, cleaning) become directly useful here for document preprocessing

### Claude Integration

- Use Claude as the generation model in your RAG pipeline
- Claude's 200K context window is unusually large — experiment with stuffing more chunks vs. fewer, better-selected chunks
- Use Claude to evaluate RAG outputs: "Given this source text and this generated answer, is the answer faithful to the source?"

### Checkpoint

You're ready for Phase 5 when you can:

- Build a RAG pipeline end-to-end from raw documents to accurate answers
- Explain why chunking strategy matters more than most people think
- Measure and articulate the quality of your RAG system with metrics
- Debug a RAG system: "The answer is wrong — is it a retrieval problem or a generation problem?"

---

## Phase 5: Agentic AI — Frameworks, Patterns & Multi-Agent Systems (Weeks 21–34)

> This is the biggest phase in the roadmap — and intentionally so. Agentic AI is the skill that defines the roles you're targeting. You'll learn 4 frameworks, multiple reasoning patterns, agent memory, error recovery, and cost management. This phase alone makes you job-ready for agentic AI roles.

### Phase 5A: Async Python Sprint (Week 21)

Before building agents, you need async fluency. Production agents run tools concurrently — not one after another.

**Concepts to Learn:**

- `async` / `await` syntax: defining and calling async functions
- `asyncio.run()`, `asyncio.gather()`: running multiple async tasks in parallel
- `aiohttp`: making concurrent HTTP requests (critical for calling multiple APIs simultaneously)
- `asyncio.Semaphore`: limiting concurrency (don't DDoS an API with 100 parallel calls)
- When to use async vs. sync: not everything needs to be async
- Error handling in async code: `try/except` inside async functions, `asyncio.gather(return_exceptions=True)`

**Mini-project:**
Build a script that takes 10 URLs, fetches all of them concurrently using `aiohttp`, and prints results as they arrive. Compare the total time vs. sequential `requests.get()` calls. You'll see a 5-10x speedup — that's why agents need async.

**Resources:**

- Real Python: "Async IO in Python" tutorial
- Python docs: asyncio module
- `aiohttp` documentation — getting started guide

### Phase 5B: LangGraph Deep Dive (Weeks 22–25)

LangGraph is your primary framework. You'll spend 4 weeks here because it's the most architecturally sound framework and maps closest to how production agents work.

**Concepts to Learn:**

**LangChain Essentials (learn enough to use, not everything):**

- Chains: composing LLM calls in sequence
- Memory: conversation history management
- Output parsers: structuring LLM responses
- Document loaders and text splitters (you already know this from RAG)
- Integration with vector stores

**LangGraph Core:**

- Graph-based agent design: nodes (actions), edges (transitions), state
- State management: how agents maintain context across steps
- `TypedDict` state: defining what information flows through the graph
- Conditional routing: letting the agent decide which path to take based on output
- Cycles and loops: agents that can retry, revise, and iterate
- Human-in-the-loop: pause execution and ask for human input/approval
- Checkpointing: saving and resuming agent state (this connects to your Fabric pipeline thinking)
- Subgraphs: nesting graphs inside graphs for complex workflows

**Reasoning Frameworks (implement each one):**

- ReAct (Reasoning + Acting): think → act → observe → think loop. The most common pattern. The agent reasons about what to do, takes an action (tool call), observes the result, and reasons again.
- Plan-and-Execute: agent creates a full plan upfront (list of steps), then executes each step sequentially. Better for tasks where the steps are predictable. Compare: ReAct discovers the plan as it goes; Plan-and-Execute commits to a plan first.
- Reflexion: after completing a task, the agent reviews its own output, identifies errors or gaps, and tries again with self-corrections. This is how agents get better within a single run.
- Tree-of-Thought: agent explores multiple reasoning paths in parallel (e.g., "Option A: search the web. Option B: check the database. Option C: ask for clarification."), evaluates each, and picks the best one. Use when the right approach isn't obvious.

**Agent Memory Systems:**

- Short-term memory: conversation history within a single session (you already know this from Phase 1)
- Long-term memory: persisting information across sessions using a database or vector store. The agent remembers what it learned yesterday.
- Episodic memory: the agent recalls similar past tasks and their outcomes ("Last time someone asked about Q3 revenue, I found the answer in the finance dashboard, not the data warehouse")
- Shared memory: multiple agents read/write to a common memory store. Agent A's research findings become Agent B's input.
- Implementation: use a simple SQLite database or ChromaDB for persistence. Don't over-engineer this — the pattern matters more than the technology.

**Error Cascading & Recovery:**

- What happens when step 3 of a 7-step agent fails?
- Retry strategies: simple retry, exponential backoff, retry with a different prompt
- Fallback strategies: if the primary tool fails, use an alternative tool
- Skip-and-continue: mark the step as failed and continue with partial results
- Rollback: undo the effects of previous steps if a later step fails (critical for agents that write to databases or send emails)
- Circuit breaker pattern: if an agent fails 3 times in a row, stop trying and escalate to a human
- Implementation: build explicit error handling into every node of your LangGraph workflow

**Cost Management:**

- Token budgets: set a maximum token spend per agent run (e.g., "this agent cannot spend more than $0.50 per request")
- Model routing: use cheap models (Haiku / GPT-4o-mini) for simple sub-tasks (classification, extraction) and expensive models (Sonnet / GPT-4o) for complex reasoning
- Tool result caching: if the agent calls the same tool with the same input twice, return the cached result
- Early termination: if the agent has a good-enough answer after 3 steps, don't force it to complete all 7
- Cost tracking: log token usage and cost per agent run. Build a dashboard.

**Multi-Agent Patterns:**

- Supervisor pattern: one orchestrator agent routes tasks to specialized worker agents
- Peer-to-peer: agents communicate directly without a supervisor
- Handoff pattern: Agent A completes its work and passes the result + context to Agent B
- Debate pattern: two agents argue opposing positions, a third agent judges
- When NOT to use multi-agent: single agents with good tool access often beat multi-agent setups. More agents = more latency, more cost, more failure points.

**Hands-on Project — "Research Agent" (LangGraph):**

1. Takes a research question as input
2. PLAN node: breaks the question into sub-questions
3. RESEARCH node: uses web search tool + document retrieval to find answers (async — search multiple sources concurrently)
4. SYNTHESIZE node: combines findings into a coherent answer
5. CRITIQUE node (Reflexion): reviews the answer for gaps or errors
6. Conditional routing: if critique finds gaps → loop back to RESEARCH (max 3 iterations — circuit breaker)
7. Human-in-the-loop: pause after plan step and let the user approve/modify the plan
8. Long-term memory: save completed research to a database, so future questions can reference past research
9. Cost tracking: log tokens used and cost per run
10. Error recovery: if web search fails, fall back to RAG-only; if RAG fails, ask the user for help
11. Produces a final formatted report

**Then extend it into a multi-agent version:**

- Agent 1: Researcher (finds information) — uses Haiku for speed
- Agent 2: Analyst (evaluates and synthesizes) — uses Sonnet for quality
- Agent 3: Writer (produces the final output) — uses Sonnet
- Supervisor: orchestrates the workflow, handles errors, enforces budget
- Shared memory: all agents read/write to a common knowledge store

### Phase 5C: CrewAI (Weeks 26–27)

> Rebuild your Research Agent in CrewAI. Same functionality, different framework. This teaches you that frameworks are tools, not religions.

**Concepts to Learn:**

- CrewAI's mental model: Agents, Tasks, Crews, Tools — how they map to LangGraph's nodes/edges/state
- Role-based agent design: each agent has a role, goal, and backstory (CrewAI's unique approach)
- Sequential vs. hierarchical crew execution
- Task delegation: one agent can delegate sub-tasks to another
- CrewAI's built-in memory system — compare with what you built manually in LangGraph
- CrewAI tools: how to wrap your existing tools for CrewAI

**Hands-on Project:**
Rebuild the Research Agent from Phase 5B using CrewAI:

- Researcher Agent (role: "Senior Research Analyst")
- Analyst Agent (role: "Data Analyst")
- Writer Agent (role: "Technical Writer")
- Run as a hierarchical crew with a manager

**After building, write a 1-page comparison:**

- What was easier in CrewAI vs. LangGraph?
- What was harder or less flexible?
- Where would you choose one over the other?
- How does error handling differ?

**Resources:**

- **CrewAI documentation** (docs.crewai.com)
- **DeepLearning.AI short course:** "Multi AI Agent Systems with CrewAI" (free)
- **CrewAI GitHub** — example crews and templates

### Phase 5D: OpenAI Agents SDK (Week 28)

> The newest framework. OpenAI released their Agents SDK to compete with LangChain/CrewAI. Learning it shows you understand the full ecosystem, not just one vendor.

**Concepts to Learn:**

- OpenAI Agents SDK architecture: Agent, Runner, Handoff, Guardrail
- Handoff pattern: how agents transfer control to each other (OpenAI's signature pattern)
- Built-in guardrails: input/output validation baked into the framework
- Tracing: OpenAI's built-in observability for agent runs
- How it differs from LangGraph: simpler but less flexible; opinionated about structure
- Using Claude (or other models) inside OpenAI's framework — it's not locked to OpenAI models

**Hands-on Project:**
Build a simpler version of your Research Agent using OpenAI Agents SDK:

- A Research agent that can search the web
- A Writer agent that formats the output
- Handoff from Research → Writer
- Built-in guardrails for output validation

**Key learning:** Compare the handoff pattern (OpenAI SDK) vs. supervisor pattern (LangGraph) vs. crew delegation (CrewAI). Same problem, three architectural approaches.

**Resources:**

- **OpenAI Agents SDK docs** (openai.github.io/openai-agents-python/)
- **OpenAI Cookbook** — agent examples
- **YouTube:** OpenAI Agents SDK launch walkthrough

### Phase 5E: AutoGen (Week 29)

> Microsoft's multi-agent framework. Important because many enterprises use Azure/Microsoft stack, and AutoGen has unique strengths in conversational multi-agent patterns.

**Concepts to Learn:**

- AutoGen's core concept: agents as conversational participants
- `ConversableAgent`, `AssistantAgent`, `UserProxyAgent` — the building blocks
- Group chat: multiple agents discussing a problem in a shared conversation
- Code execution: AutoGen agents can write and run Python code autonomously
- Human proxy: an agent that represents the human in the conversation
- AutoGen vs. LangGraph: AutoGen is conversation-first; LangGraph is workflow-first
- AutoGen Studio: the visual interface for building agent workflows (useful for demos)

**Hands-on Project:**
Build a "Code Review Agent System" using AutoGen:

- Agent 1: Code Writer — generates Python code for a given task
- Agent 2: Code Reviewer — reviews the code for bugs, style, and improvements
- Agent 3: Tester — writes and runs tests for the code
- Human Proxy: you approve/reject at key points
- Group chat: all agents discuss in a shared conversation until consensus is reached

**Resources:**

- **AutoGen documentation** (microsoft.github.io/autogen/)
- **Microsoft Research blog** — AutoGen design philosophy
- **DeepLearning.AI short course:** "AI Agentic Design Patterns with AutoGen" (free)

### Phase 5 — Framework Comparison Checkpoint (End of Week 29)

After building with all 4 frameworks, create a comparison document:

| Dimension            | LangGraph                  | CrewAI           | OpenAI SDK            | AutoGen                    |
| -------------------- | -------------------------- | ---------------- | --------------------- | -------------------------- |
| Best for             | Complex stateful workflows | Role-based teams | Simple handoff chains | Conversational multi-agent |
| State management     | Explicit TypedDict         | Implicit in crew | Runner-managed        | Chat history               |
| Error handling       | Manual (full control)      | Built-in retry   | Guardrail system      | Group chat retry           |
| Flexibility          | Very high                  | Medium           | Low-medium            | Medium                     |
| Learning curve       | Steep                      | Gentle           | Gentle                | Medium                     |
| Production readiness | High                       | Medium           | Growing               | Medium                     |
| When I'd choose it   | Production systems         | Quick prototypes | OpenAI-heavy stacks   | Microsoft/Azure stacks     |

This comparison becomes a valuable interview artifact — it shows you think architecturally, not just "I know tool X."

### Phase 5 Resources (All Sub-phases)

- **LangGraph documentation** (langchain-ai.github.io/langgraph/) — primary reference
- **CrewAI documentation** (docs.crewai.com) — role-based agents
- **OpenAI Agents SDK docs** — handoff patterns
- **AutoGen documentation** (microsoft.github.io/autogen/) — conversational agents
- **Book:** AI Engineering by Chip Huyen — agent architecture chapters
- **DeepLearning.AI short courses** — "AI Agents in LangGraph", "Multi AI Agent Systems with CrewAI", "AI Agentic Design Patterns with AutoGen" (all free, ~2 hours each)
- **Harrison Chase's talks** — YouTube, practical agent design philosophy
- **Anthropic Cookbook** — agent patterns with Claude

### Phase 5 Claude Integration

- Use Claude as the LLM inside agents across ALL 4 frameworks — prove it's not locked to any one vendor
- Claude's tool use capabilities work natively with LangGraph and can be adapted for CrewAI/AutoGen
- Experiment with Claude's extended thinking for the "reasoning" steps in ReAct and Plan-and-Execute patterns
- Use Claude (Haiku) for cheap sub-tasks and Claude (Sonnet) for complex reasoning — practice model routing within a single agent run
- Build at least one MCP server that your agents can connect to across frameworks

### Phase 5 Checkpoint

You're ready for Phase 6 when you can:

- Design a multi-step agent workflow on a whiteboard before writing any code
- Build the same agent in at least 2 different frameworks and explain the tradeoffs
- Implement ReAct, Plan-and-Execute, and Reflexion patterns and know when to use each
- Build an agent with persistent memory that remembers across sessions
- Handle agent failures gracefully: retry, fallback, circuit breaker, escalation to human
- Track and optimize the token cost of an agent run
- Articulate when an agent is the right solution vs. a simple prompt chain (hint: simple chain wins more often than people think)

---

## Phase 6: Production Agentic AI — Architecture, Safety & Deployment (Weeks 30–38)

> This phase transitions you from "I can build an agent" to "I can architect, deploy, and operate an agentic AI system in production." This is what separates a demo builder from a hire-worthy engineer.

### Concepts to Learn

**Architecture Patterns:**

- Monolithic agent vs. microservice agents: when to use a single powerful agent vs. multiple small ones
- Event-driven agent architectures: agents triggered by events (new data, user action, scheduled time) rather than direct requests
- Agent communication protocols: how agents pass context, results, and errors to each other
- State persistence and recovery: agent crashes mid-workflow — how to resume from the last checkpoint, not restart from scratch
- Idempotency in agent actions: an agent retries a tool call — will it create duplicate records? Send duplicate emails? How to prevent this.
- Agentic RAG: agents that decide what to retrieve, how to retrieve it, and whether the retrieval was good enough — combining Phase 4 and Phase 5 skills

**Agent-Specific Safety & Guardrails:**

- Autonomy limits: define what agents are ALLOWED to do vs. what requires human approval (e.g., "agent can query databases but cannot delete records without confirmation")
- Runaway loop detection: kill an agent if it exceeds N iterations or N tokens. Implementation: a wrapper that counts iterations and forces termination
- Escalation paths: when agent confidence is low, hand off to a human with full context. Don't just fail silently.
- Input sanitization for agents: users can try to manipulate agents via prompt injection. Validate inputs before they reach the agent.
- Output validation: does the agent's response conform to expected format, length, and content policies?
- Hallucination detection in agent chains: agent A hallucinates → agent B treats it as fact → cascade of wrong answers. How to add verification steps.
- Permission boundaries: agent can read from Database X but not Database Y. Agent can call API Z but with rate limits.
- Kill switch: ability to immediately stop all agent runs in production if something goes wrong

**Observability & Tracing (Hands-on):**

- LangSmith setup: connect your agent, trace every LLM call, view the execution graph
- What to log: inputs, outputs, tool calls, tool results, tokens used, latency per step, total cost, error messages
- Trace visualization: see exactly which path the agent took through the workflow, which tools it called, and where it spent the most time/tokens
- Alerting: set up alerts for cost spikes, latency spikes, error rate increases
- Langfuse as an alternative: open-source observability — set up locally, compare with LangSmith
- Cost dashboards: per-agent, per-user, per-day cost tracking
- Debugging with traces: "The agent gave a wrong answer" → look at the trace → identify that the retrieval step returned irrelevant documents → fix the retrieval prompt

**Evaluation & Testing:**

- LLM-as-judge: using one model to evaluate another's output (e.g., Claude Opus evaluates whether Sonnet's answer is correct)
- Automated evaluation pipelines: run 50 test queries nightly, score results, flag regressions
- Regression testing for prompts: "I changed the system prompt — did it break any of the 50 test cases?"
- Behavioral testing: does the agent refuse to do things it shouldn't? Does it ask for help when it's uncertain?
- A/B testing for AI features: serve two versions of an agent to different users, measure which performs better
- Evaluation metrics: task completion rate, answer accuracy, cost per successful task, user satisfaction

**Deployment:**

- FastAPI: serve your agent as an API endpoint
- Docker: containerize your agent application
- Streaming responses: SSE (Server-Sent Events) for real-time agent output to the user
- Caching: cache frequent tool results, cache LLM responses for identical inputs
- Scaling considerations: async request handling, queue-based processing for long-running agent tasks
- CI/CD for AI applications: prompt versioning in Git, evaluation suite runs in CI pipeline, automated deployment
- Environment management: dev/staging/prod with different model configs (use cheap models in dev, production models in prod)

### Hands-on Project

**Build a production-grade "AI Assistant for Data Teams":**

This is your capstone project — it combines everything from all 6 phases:

1. **Multi-agent architecture (use LangGraph — your strongest framework):**

   - SQL Agent: takes natural language → generates SQL → runs against a database → returns results
   - Analysis Agent: takes data results → produces insights and visualizations
   - Report Agent: takes insights → generates a formatted report
   - Orchestrator: routes user requests to the right agent(s), handles errors, enforces budget
2. **RAG integration:** The agents can search a knowledge base of documentation, past reports, and business context
3. **Tool use with MCP:** Database querying, chart generation (matplotlib), file creation, web search — at least one tool exposed as an MCP server
4. **Agent memory:** Save completed analyses to a persistent store. When a user asks "Compare this quarter to what we analyzed last month," the agent can retrieve past results.
5. **Guardrails — all of these must be implemented:**

   - SQL injection prevention (validate generated SQL before execution)
   - Output validation (agent responses must be valid JSON or markdown)
   - Cost limit per request ($0.50 max per user query)
   - Iteration limit (max 5 loop iterations before escalating to human)
   - Permission boundaries (read-only database access, no DELETE/UPDATE)
6. **Observability — mandatory:**

   - LangSmith or Langfuse integration — every agent run is traced
   - Cost dashboard: track spend per day, per user, per agent
   - Latency tracking: identify which agent step is the bottleneck
   - Error logging: every failure is captured with full context
7. **Error recovery — all of these must work:**

   - If SQL generation fails → retry with a simplified prompt
   - If database query times out → return partial results with a warning
   - If the Analysis agent produces an empty result → escalate to human with context
   - If total cost exceeds budget → terminate gracefully and explain to user
8. **Simple web interface:** Streamlit or Gradio frontend
9. **Evaluation suite:** 30+ test queries with expected outputs, automated scoring, run as part of CI
10. **Deployment:** Dockerized, served via FastAPI, with a README that explains how to deploy

This project is directly relevant to your MAA team and could become a real tool. It's also your primary portfolio piece for interviews.

### Resources

- **Book:** AI Engineering by Chip Huyen — production chapters (evaluation, deployment, guardrails)
- **Book:** DDIA by Kleppmann — now this becomes relevant for understanding the infrastructure layer
- **LangSmith documentation** (docs.smith.langchain.com) — setup, tracing, evaluation
- **Langfuse documentation** (langfuse.com/docs) — open-source alternative
- **FastAPI documentation** — serving ML/AI applications
- **Docker documentation** — containerizing Python applications
- **Anthropic's production best practices** — docs.anthropic.com
- **Hamel Husain's blog** — practical AI engineering, evaluation-focused

### Claude Integration

- Use Claude as the backbone model for all agents
- Implement model routing: Haiku for SQL generation and simple classification, Sonnet for complex analysis and report writing
- Use Claude's extended thinking for the Analysis agent's reasoning steps
- Use Claude's native tool use (no wrapper needed) for direct tool calls
- Explore Claude's vision capabilities: the Analysis agent can process uploaded charts/images
- Use Claude (Opus via API) as the LLM-as-judge in your evaluation pipeline

### Checkpoint

You've completed the roadmap when you can:

- Design a multi-agent system architecture on a whiteboard and defend every decision (framework choice, model routing, error handling, cost management)
- Set up LangSmith/Langfuse observability and use traces to debug agent issues
- Build an evaluation suite that catches regressions before deployment
- Implement agent safety: autonomy limits, runaway detection, escalation, kill switch
- Deploy a Dockerized agent application with FastAPI
- Track and optimize the cost of your agent system
- Build with at least 2 different agent frameworks and explain when to use each
- Have a portfolio project that demonstrates production-level thinking — not just "it works" but "it works reliably, safely, and cost-effectively"

---

## Where the Books Fit

| Book                                  | When to Read                               | How to Use It                                                       |
| ------------------------------------- | ------------------------------------------ | ------------------------------------------------------------------- |
| **AI Engineering (Chip Huyen)** | Start in Phase 1, continue through Phase 6 | Primary reference throughout — read chapters as you hit each topic |
| **NLP Cookbook**                | Dip into during Phase 4 (RAG)              | Text preprocessing recipes for document ingestion pipelines         |
| **NLP with Transformers**       | After Phase 6, if you want to go deeper    | Understanding model internals, fine-tuning, advanced optimization   |
| **DDIA (Kleppmann)**            | Phase 6 and beyond, ongoing                | Architecture thinking for production systems                        |

### Does the NLP Cookbook get covered by this roadmap?

**Partially.** The cookbook covers classical NLP tasks (tokenization, NER, sentiment analysis, etc.). This roadmap covers the LLM-native way of doing those same tasks (via prompting and tool use), which has largely replaced the classical approach for most applications. You'll pick up the cookbook-relevant skills in Phases 2 and 4, but from an LLM-first perspective rather than a spaCy/NLTK perspective.

**When the cookbook still adds value:** When you need to preprocess documents for RAG (Phase 4), clean text at scale, or understand what NLP tasks exist. It's a reference, not a prerequisite.

### Does this roadmap cover prompt engineering and contextual engineering?

**Yes, deeply.** Phase 2 is entirely dedicated to this, and the skills get reinforced in every subsequent phase. By Phase 6, you'll be doing contextual engineering naturally — assembling system prompts, tool definitions, retrieved documents, and conversation history into optimized context windows.

---

## Claude-Specific Skills Woven Throughout

Since you specifically want Claude proficiency, here's what you'll build across the phases:

- **Phase 1:** Claude API basics, model selection (Opus/Sonnet/Haiku)
- **Phase 2:** Claude's XML-tag structured prompting, extended thinking
- **Phase 3:** Claude's native tool use, MCP server building
- **Phase 4:** Claude as RAG generation model, leveraging 200K context
- **Phase 5B:** Claude inside LangGraph agents with model routing (Haiku for cheap tasks, Sonnet for complex reasoning)
- **Phase 5C-E:** Claude as a drop-in LLM across CrewAI, OpenAI Agents SDK, and AutoGen — proving vendor independence
- **Phase 6:** Claude in production — cost optimization, observability, evaluation, Opus as LLM-as-judge
- **Throughout:** Using Claude (the chat interface) as a learning partner, code reviewer, and prompt critic

---

## Weekly Schedule Template (10–15 hrs/week)

| Day       | Activity                                        | Hours   |
| --------- | ----------------------------------------------- | ------- |
| Monday    | Read/study concepts for current phase           | 2 hrs   |
| Tuesday   | Hands-on coding — build project                | 2.5 hrs |
| Wednesday | Hands-on coding — continue project             | 2.5 hrs |
| Thursday  | Read book chapter (Chip Huyen or relevant)      | 1.5 hrs |
| Saturday  | Deep work — project push, debugging, iteration | 3 hrs   |
| Sunday    | Review, document learnings, plan next week      | 1.5 hrs |

**Total: ~13 hours/week**

---

## One Final Note

The biggest risk in a roadmap like this is **learning without building**. Your instinct to be hands-on is exactly right. Every concept should have a corresponding "thing I built that uses this concept." If you're reading about RAG but haven't built a RAG pipeline, you don't know RAG yet. The projects are not homework — they ARE the learning.

Your data engineering background (pipelines, data quality, architecture thinking, lakehouse design) is not a detour — it's a competitive advantage. Most LLM engineers can't think about data pipelines. You can. That's your edge.

---

## Appendix: Agentic AI Skills Coverage Audit

All 16 core agentic AI skills mapped to this roadmap:

**Fully covered (12/16):**

1. LLM API fluency → Phase 1
2. Prompt engineering (system-level) → Phase 2
3. Tool use / function calling → Phase 3
4. MCP (Model Context Protocol) → Phase 3, Phase 6
5. RAG pipelines → Phase 4
6. LangGraph agent workflows → Phase 5B
7. Multi-agent coordination → Phase 5B
8. Agent evaluation → Phase 6
9. Reasoning frameworks (ReAct, Plan-and-Execute, Reflexion, Tree-of-Thought) → Phase 5B
10. Agent memory systems (short-term, long-term, episodic, shared) → Phase 5B
11. Async Python for agents → Phase 5A
12. Multiple agent frameworks (LangGraph, CrewAI, OpenAI SDK, AutoGen) → Phase 5B-E

**Covered with production depth (4/16):**
13. Guardrails / agent safety (autonomy limits, runaway detection, escalation, kill switch) → Phase 6
14. Observability / tracing (LangSmith, Langfuse — hands-on) → Phase 6
15. Error cascading / recovery (retry, fallback, circuit breaker, rollback) → Phase 5B + Phase 6
16. Cost management (token budgets, model routing, caching, tracking) → Phase 5B + Phase 6

**Total: 16/16 agentic AI skills covered.**
