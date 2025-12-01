# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

LangChain Essentials Python - A tutorial repository with nine Jupyter notebooks (L1-L9) teaching LangChain V1 features, including `create_agent`, messages, streaming, tools, MCP adapters, memory, structured output, and human-in-the-loop interactions.

## Commands

### Setup
```bash
cp example.env .env          # Then add OPENAI_API_KEY (required), LANGSMITH_API_KEY (optional)
uv sync                      # Install dependencies
```

### Run Notebooks
```bash
uv run jupyter lab
```

### Run LangGraph Studio (for L1 agent debugging)
```bash
cp .env ./studio/.
cd studio
uv run langgraph dev
```

### Linting
```bash
uv run ruff check .
uv run ruff format .
```

## Architecture

- **Notebooks (L1-L9)**: Sequential tutorial lessons in root directory
- **studio/**: Contains SQL agent examples for LangGraph Studio
  - `sql_agent1.py`: Full SQL agent with safety guards (read-only, LIMIT enforcement)
  - `sql_agent2.py`: Simplified SQL agent
  - `langgraph.json`: Studio configuration pointing to `sql_agent2.py:agent`
- **env_utils.py**: Utilities for checking environment variables (`doublecheck_env`) and package versions (`doublecheck_pkgs`)

## Key Dependencies

- `langchain>=1.0.0`, `langgraph>=1.0.0`, `langchain-openai>=1.0.0`
- `langchain-mcp-adapters` for MCP tool integration (L5)
- Requires Python 3.11-3.13
- Node.js/npx required for MCP server in L5
