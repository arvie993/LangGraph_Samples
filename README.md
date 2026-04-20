# LangGraph Samples

A hands-on progression through [LangGraph](https://github.com/langchain-ai/langgraph) — from state graph fundamentals to building **Sidekick**, an autonomous AI co-worker with web browsing, search, code execution, and a self-evaluation feedback loop.

## Labs

| Lab | Topic | Description |
|-----|-------|-------------|
| [Lab 1](1_lab1.ipynb) | LangGraph Basics | `StateGraph`, `Annotated` types, tool definitions, simple function wrapping |
| [Lab 2](2_lab2.ipynb) | Tools & Search | Google Serper search, `ToolNode`, `tools_condition`, building a search agent |
| [Lab 3](3_lab3.ipynb) | Async & Web UI | Async/await patterns, Gradio integration, connecting LangGraph to a web interface |
| [Lab 4](4_lab4.ipynb) | The Sidekick Project | Structured outputs (Pydantic), multi-agent patterns, Playwright browser tools, full Sidekick system |

## Sidekick — AI Co-Worker

The Python modules implement an autonomous agent that takes user requests with success criteria, works through them using multiple tools, and evaluates its own output in a feedback loop:

- **sidekick.py** — Core LangGraph agent with worker and evaluator nodes, state management, and `MemorySaver` checkpoints
- **sidekick_tools.py** — Tool definitions: Playwright browser, Google Serper search, Wikipedia, Python REPL, file I/O, push notifications
- **app.py** — Gradio web UI for interacting with the Sidekick agent

### How It Works

1. User submits a request and success criteria via the Gradio UI
2. The **worker** node generates a response using GPT-4o-mini and available tools
3. The **evaluator** node checks if success criteria are met using structured output
4. If not satisfied, feedback is looped back to the worker for refinement

## Tech Stack

- **LangGraph** — State graph framework for multi-step agent workflows
- **LangChain** — LLM integration, tool utilities
- **OpenAI GPT-4o-mini** — Primary LLM
- **Gradio** — Web interface
- **Playwright** — Headful browser automation
- **Pydantic** — Structured outputs and validation
- **Google Serper API** — Web search

## Setup

```bash
pip install langgraph langchain-openai langchain-community gradio playwright
playwright install chromium
```

Create a `.env` file with your API keys:

```
OPENAI_API_KEY=your-key-here
SERPER_API_KEY=your-key-here
```

Run the web UI:

```bash
python app.py
```

## License

See the root repository for license details.
