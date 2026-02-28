# AI Agent Using LangChain

> **Note:** This repository is used as a **Git submodule** inside the parent repository  
> 👉 [Sikandarh11/Generative-AI-using-LangChain](https://github.com/Sikandarh11/Generative-AI-using-LangChain)

---

## 📖 Overview

This repository demonstrates how to build a **ReAct (Reasoning + Acting) AI Agent** using [LangChain](https://www.langchain.com/) and OpenAI's GPT models. The agent can reason step-by-step about a task, decide which tool to call, observe the result, and continue reasoning until it reaches a final answer — all in a single automated loop.

The main notebook (`simple_ai_agent.ipynb`) walks through:
- Setting up LangChain tools (web search + weather API)
- Connecting to an OpenAI LLM
- Pulling a standard ReAct prompt from LangChain Hub
- Building and running an `AgentExecutor` that chains tool calls together autonomously

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔍 **Web Search** | Uses `DuckDuckGoSearchRun` to fetch up-to-date information from the web |
| 🌤️ **Live Weather** | Calls the [Weatherstack API](https://weatherstack.com/) to retrieve current weather for any city |
| 🤖 **ReAct Agent** | Implements the ReAct prompting strategy — the agent reasons, acts, observes, and iterates |
| 🔗 **LangChain Hub** | Pulls the standard `hwchase17/react` prompt directly from LangChain Hub |
| 📝 **Verbose Logging** | `AgentExecutor` runs with `verbose=True` so every reasoning step is printed |

---

## 🗂️ Repository Structure

```
AI-Agent-Using-Langchain/
├── simple_ai_agent.ipynb   # Main Jupyter notebook — full agent implementation
├── Submodule.txt           # Notes on Git submodules concept and workflow
├── notes.pdf               # Supporting reference notes (PDF)
└── README.md               # This file
```

---

## 🛠️ Tech Stack

- **Python 3.10+**
- [LangChain](https://python.langchain.com/) — agent framework and tool abstraction
- [langchain-openai](https://pypi.org/project/langchain-openai/) — OpenAI LLM integration
- [langchain-community](https://pypi.org/project/langchain-community/) — community tools (DuckDuckGo)
- [OpenAI GPT-3.5-turbo](https://platform.openai.com/docs/models) — underlying language model
- [Weatherstack API](https://weatherstack.com/) — real-time weather data
- [python-dotenv](https://pypi.org/project/python-dotenv/) — environment variable management
- [Jupyter Notebook](https://jupyter.org/) — interactive development environment

---

## ⚙️ Setup & Installation

### 1. Clone the repository

```bash
git clone https://github.com/Sikandarh11/AI-Agent-Using-Langchain.git
cd AI-Agent-Using-Langchain
```

> If you are cloning the **parent** repository (`Generative-AI-using-LangChain`) which uses this repo as a submodule, run:
> ```bash
> git clone --recurse-submodules https://github.com/Sikandarh11/Generative-AI-using-LangChain.git
> ```
> Or, if you already cloned the parent without submodules:
> ```bash
> git submodule update --init --recursive
> ```

### 2. Create and activate a virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate        # Linux / macOS
venv\Scripts\activate           # Windows
```

### 3. Install dependencies

```bash
pip install langchain langchain-openai langchain-community python-dotenv openai requests
```

### 4. Configure environment variables

Create a `.env` file in the project root:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

> The Weatherstack API key is referenced directly in the notebook. Replace the value of `api_key` in Cell 3 with your own key from [weatherstack.com](https://weatherstack.com/).

---

## 🚀 Usage

Launch the Jupyter notebook:

```bash
jupyter notebook simple_ai_agent.ipynb
```

Then run the cells in order. The final cell sends the following query to the agent:

```
"Find capital of Pakistan, then find the current weather in that city"
```

The agent will:
1. **Reason** — decide it needs to find the capital first.
2. **Act** — call the DuckDuckGo search tool.
3. **Observe** — read the search result (e.g., "Islamabad").
4. **Act again** — call the weather tool with "Islamabad".
5. **Observe** — read the weather data.
6. **Answer** — return the final combined response.

---

## 🧠 How the ReAct Agent Works

```
User Input
    │
    ▼
┌─────────────────────────────────┐
│  LLM (GPT-3.5-turbo)            │
│  + ReAct Prompt (hwchase17)     │
│                                 │
│  Thought → Action → Observation │
│  (repeated until final answer)  │
└─────────────────────────────────┘
    │              │
    ▼              ▼
DuckDuckGo     Weatherstack
 Search          API Tool
```

The **ReAct** pattern interleaves reasoning traces (`Thought:`) with tool invocations (`Action:`) so the agent can ground its answers in real-world data rather than relying solely on its training knowledge.

---

## 🔗 Submodule Relationship

This repository serves as a **Git submodule** of:

> **[Sikandarh11/Generative-AI-using-LangChain](https://github.com/Sikandarh11/Generative-AI-using-LangChain)**

The parent repository is a comprehensive collection of Generative AI projects built with LangChain. This submodule contributes the AI-agent component to that larger learning repository. Using a submodule keeps the agent code independently versioned and reusable while still being accessible as part of the broader project.

For a deep-dive on Git submodules — including how to add, clone, and update them — see [`Submodule.txt`](./Submodule.txt) included in this repo.

---

## 📄 License

This project is open-source and available for educational purposes.