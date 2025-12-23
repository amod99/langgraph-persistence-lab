# 🤖 Agentic State Patterns: Robust Memory & Tool-Use

This repository contains research and implementation patterns for moving beyond stateless LLM prompts toward **Agentic AI Systems**. 

As we shift into 2026, the value of AI lies in **Agency**—the ability for a model to reason, use tools, and maintain a persistent state across sessions. This project demonstrates how to use **LangGraph** to build reliable, stateful workflows.



## 🎯 Key Patterns Implemented

### 1. Persistent Episodic Memory
- **Problem:** Stateless LLMs lose context as soon as the session ends.
- **Solution:** Implemented **SQLite Checkpointing** using `SqliteSaver`.
- **Outcome:** The agent retains a "long-term" conversation history linked to a specific `thread_id`, allowing it to resume complex tasks even after a complete system restart.

### 2. Cyclical Tool-Calling Loops
- **Problem:** Linear chains fail when the LLM makes a mistake or needs more information.
- **Solution:** A **Cyclic State Machine** that routes between an `agent` node and a `tool` node.
- **Senior-Level Robustness:** Includes explicit type-checking for `AIMessage` vs. `ToolMessage` to prevent common `AttributeError` crashes in long-running loops.

## 🛠️ Tech Stack
- **Orchestration:** LangGraph (v0.2.x / 2025 Standard)
- **Framework:** LangChain Community
- **LLM:** GPT-4o / Claude 3.5 Sonnet
- **Database:** SQLite (Durable Checkpointing)

## 🚀 Getting Started

### Prerequisites
```bash
pip install -U langgraph langchain-openai langgraph-checkpoint-sqlite
