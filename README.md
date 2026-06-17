# 🤖 Agentic LangGraph Project

## Overview

**Agentic_LangGraph** is an educational project exploring the construction of agentic AI applications using **LangGraph**, a powerful framework for building stateful, multi-step AI workflows. This repository demonstrates how to create intelligent chatbots and multi-agent systems using graph-based state management and language models.

---

## 🎯 Project Goals

- **Understand LangGraph fundamentals** - Learn how to build applications using state graphs and workflow orchestration
- **Build AI agents** - Create intelligent agents that can reason, plan, and take actions
- **Explore LLM integration** - Integrate language models (via Groq) into agent workflows
- **Multi-agent patterns** - Experiment with multiple AI agents working together in coordinated graphs

---

## 📁 Project Structure

```
Agentic_langgraph/
├── main.py                          # Entry point for the project
├── pyproject.toml                   # Project configuration and dependencies
├── requirements.txt                 # Python dependencies
├── README.md                        # Project documentation
├── PROJECT_OVERVIEW.md             # This file
└── Basic_Chatbot/
    └── basic_chatbot.ipynb         # Interactive notebook: Building a basic chatbot with LangGraph
```

---

## 🔧 Core Dependencies

The project leverages cutting-edge libraries for AI and agentic applications:

| Package | Purpose |
|---------|---------|
| **langgraph** | Graph-based state machine for orchestrating AI workflows |
| **langchain** | LLM orchestration and chaining framework |
| **langchain-groq** | Integration with Groq's fast LLM API |
| **langchain-openai** | Support for OpenAI models (optional) |
| **langsmith** | Monitoring and debugging for LangChain applications |
| **python-dotenv** | Environment variable management for API keys |
| **ipykernel** | Jupyter notebook support |

---

## 📚 Basic Chatbot Module

### Location
[`Basic_Chatbot/basic_chatbot.ipynb`](Basic_Chatbot/basic_chatbot.ipynb)

### What It Does

This Jupyter notebook demonstrates creating a **simple conversational AI agent** using LangGraph's state graph architecture:

#### Key Components

1. **State Definition**
   ```python
   class State(TypedDict):
       messages: Annotated[list, add_messages]
   ```
   - Defines the data structure that flows through the graph
   - Uses `add_messages` utility for intelligent message accumulation

2. **LLM Integration**
   - Uses **Groq's Llama-3.1-8B** model for fast inference
   - Configured via environment variables (API key)
   - Two initialization methods shown:
     - Direct `ChatGroq` initialization
     - Generic `init_chat_model` approach

3. **Chatbot Node**
   ```python
   def chatbot_node(state: State):
       return {"messages": [llm2.invoke(state["messages"])]}
   ```
   - Core processing node that generates responses
   - Takes current message state and produces AI-generated replies

4. **Graph Construction**
   - **START** → **chatbot_node** → **END**
   - Simple linear flow for basic conversation
   - Graph is compiled to create an executable workflow

#### Usage Patterns Demonstrated

- **Single Invocation**: `graph.invoke({"messages": "Hi"})`
  - Direct input/output for single queries

- **Streaming**: `graph.stream({"messages": "How are you?"})`
  - Real-time event streaming for progressive message generation
  - Useful for displaying responses as they're generated

#### Example Features

✨ The notebook demonstrates:
- Loading environment variables safely
- Initializing language models
- Building state graphs programmatically
- Visualizing graph structure (Mermaid diagram)
- Invoking chatbot with single and streaming modes
- Extracting and displaying generated content

---

## 🚀 Getting Started

### Prerequisites
- Python 3.14 or higher
- API key for Groq (free tier available)

### Installation

1. **Clone/Navigate to the project**
   ```bash
   cd Agentic_langgraph
   ```

2. **Set up environment**
   ```bash
   # Create .env file
   echo "GROQ_API=your_groq_api_key" > .env
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   # OR using UV (faster package manager)
   uv pip install -r requirements.txt
   ```

4. **Run the chatbot notebook**
   - Open `Basic_Chatbot/basic_chatbot.ipynb` in Jupyter or VS Code
   - Execute cells sequentially to build and interact with the chatbot

---

## 🔄 How LangGraph Works (In This Project)

```
┌─────────────────────────────────────────┐
│          Input Message                  │
│      {"messages": "Hi, how are you?"}   │
└────────────────┬────────────────────────┘
                 │
                 ▼
          ┌──────────────┐
          │    START     │
          └──────┬───────┘
                 │
                 ▼
         ┌──────────────────┐
         │  chatbot_node()  │ ◄──── Calls LLM with messages
         │                  │
         │ Groq LLM responds │
         └──────┬───────────┘
                │
                ▼
           ┌─────────────┐
           │     END     │
           └─────┬───────┘
                 │
                 ▼
      ┌────────────────────────┐
      │  Output with Response  │
      │ {"messages": [user_msg,│
      │             bot_reply]}│
      └────────────────────────┘
```

---

## 💡 Next Steps & Extensions

This basic chatbot is a foundation for more advanced patterns:

- **Multi-turn conversation**: Maintain conversation history
- **Tool calling**: Enable agents to use external tools/APIs
- **Conditional routing**: Route to different nodes based on conditions
- **Parallel execution**: Run multiple agent paths concurrently
- **Human-in-the-loop**: Add approval steps before actions
- **Multiple agents**: Coordinate between specialized agents

---

## 📖 Learning Resources

- [LangGraph Documentation](https://python.langchain.com/docs/langgraph/)
- [LangChain Integration Guide](https://python.langchain.com/docs/)
- [Groq API Documentation](https://groq.com/)
- [Agent Design Patterns](https://python.langchain.com/docs/concepts/agents/)

---

## 🛠️ Development

The project is configured with:
- **Modern Python packaging** (pyproject.toml)
- **Environment variable management** (python-dotenv)
- **Interactive development** (Jupyter notebooks)
- **Type hints** for better code clarity

---

## 📝 License & Attribution

This is an educational project exploring LangGraph capabilities. It's perfect for learning modern AI application development patterns.

---

**Last Updated**: June 2026  
**Status**: Active Development & Learning
