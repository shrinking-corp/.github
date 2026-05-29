# 📐 Diagram Shrinking

Welcome to the **Shrinking Corp** organisation — a collection of open repositories for shrinking diagrams algorithmically, exposing those algorithms as tools for AI agents, and measuring their correctness.

---

## Repositories

### [`chat-app`](https://github.com/shrinking-corp/chat-app)
A minimal full-stack web application with a **FastAPI** backend and a **React + Vite** frontend. Handles the user interface, API communication, and database persistence for the core business logic. Shrinking algorithms are intentionally kept out of this layer — see `algorithms` below.

### [`shrinking-algorithms-library`](https://github.com/shrinking-corp/shrinking-algorithms-library)
A standalone **Python library published to PyPI**. This is the single source of truth for all shrinking algorithm implementations. Install it in any project:

```bash
pip install shrinking-algorithms
```

### [`mcp-server`](https://github.com/shrinking-corp/mcp_server)
An **MCP (Model Context Protocol) server** that exposes the shrinking algorithms from `algorithms` as callable tools. Any MCP-compatible client or agent can connect and invoke the algorithms without writing Python directly.

### [`example-agentic_ai`](https://github.com/shrinking-corp/example-agentic_ai)
A **general-purpose chat client** built on top of OpenAI and LangGraph. On startup it connects to our `mcp-server`, discovers available tools, and lets the language model decide autonomously when and how to apply shrinking algorithms during a conversation.

### [`dataset-with-iterator`](https://github.com/shrinking-corp/dataset-with-iterator)
A **dataset** for measuring the correctness of the shrinking algorithms.

### [`algorithms-benchmarking`](https://github.com/shrinking-corp/algorithms-benchmarking)
A benchmarking tool for evaluating PlantUML diagram shrinking algorithms using LLM-generated code quality as the metric.
---

## How the pieces fit together

```
┌─────────────────────────────────────────────────────────┐
│  chat-app  (full-stack UI + business logic)             │
│      │                                                  │
│      └── uses ──▶  algorithms  (PyPI library)           │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│  example-agentic-ai  (OpenAI + LangGraph chat agent)    │
│      │                                                  │
│      └── connects to ──▶  mcp-server  (MCP tools)       │
│                                │                        │
│                                ▼                        │
│                         algorithms  (PyPI library)      │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│  benchmarking (correctness evaluation + parameter tuning)│
│      │                                                  │
│      └── evaluates ──▶  algorithms  (PyPI library)      │
└─────────────────────────────────────────────────────────┘
```

---

## Getting started

| Goal | Where to start |
|---|---|
| Run the web application | [`app`](https://github.com/shrinking-corp/chat-app) |
| Use shrinking algorithms in your own code | [`algorithms`](https://github.com/shrinking-corp/shrinking-algorithms-library) |
| Connect an AI agent to the algorithms | [`agentic-ai`](https://github.com/shrinking-corp/example-agentic_ai) |
| Expose algorithms as MCP tools | [`mcp-server`](https://github.com/shrinking-corp/mcp_server) |
| Evaluate or tune the algorithms | [`benchmarks`](https://github.com/shrinking-corp/algorithms-benchmarking) |
