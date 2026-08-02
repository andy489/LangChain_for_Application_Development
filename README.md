# LangChain for LLM Application Development

Jupyter notebooks covering the core building blocks of LangChain, updated to use **modern APIs** (LangChain ≥ 1.3, LangGraph ≥ 1.0).

---

## Notebooks

| # | Topic | Key Concepts |
|---|-------|-------------|
| [01](01-LC-models-prompts-and-parsers.ipynb) | Models, Prompts & Output Parsers | `ChatOpenAI`, `ChatPromptTemplate`, structured output with Pydantic |
| [02](02-LC-memory.ipynb) | Memory | `ConversationBufferMemory`, window memory, token buffer, summary memory |
| [03](03-LC-chains.ipynb) | Chains | Sequential chains, router chains, LCEL pipe syntax |
| [04](04-LC-questions-and-answers.ipynb) | Questions & Answers | CSV loader, vector store, retrieval-augmented generation (RAG) |
| [05](05-LC-evaluation.ipynb) | Evaluation | LLM-generated test examples, LLM-as-judge grading, batch scoring |
| [06](06-LC-agents.ipynb) | Agents | `create_react_agent`, custom `@tool` decorator, Python executor, Wikipedia & calculator tools |

---

## Setup

### Prerequisites

- Python 3.11+
- An [OpenAI API key](https://platform.openai.com/account/api-keys)

### Install

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install langchain langchain-openai langchain-community langchain-classic \
            langchain-core langchain-text-splitters langgraph langgraph-prebuilt \
            openai python-dotenv jupyter wikipedia docarray
```

### Configure

Create a `.env` file in the project root:

```
OPENAI_API_KEY=sk-...
```

### Run

```bash
jupyter lab
```

---

## API Versions

All notebooks use the current LangChain 1.x / LangGraph 1.x APIs:

| Old (removed) | Replacement used in these notebooks |
|---|---|
| `from langchain.chains import RetrievalQA` | LCEL: `retriever \| prompt \| llm \| parser` |
| `from langchain.chat_models import ChatOpenAI` | `from langchain_openai import ChatOpenAI` |
| `from langchain.agents import initialize_agent, AgentType` | `from langgraph.prebuilt import create_react_agent` |
| `from langchain.agents import load_tools` | `WikipediaQueryRun`, custom `@tool` functions |
| `from langchain.evaluation.qa import QAEvalChain` | Custom LCEL grading chain |
| `from langchain.indexes import VectorstoreIndexCreator` | `DocArrayInMemorySearch.from_documents()` |

---

## Assets

The `assets/` folder contains:
- Diagram images embedded in the notebooks
- `OutdoorClothingCatalog_1000.csv` — product catalogue used by notebooks 04 and 05
