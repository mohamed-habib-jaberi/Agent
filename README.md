# Agent

A hands-on repository for learning, building, and comparing different AI agent architectures.

Each project is self-contained in the `agents/` directory with its own documentation, dependencies, configuration example, and runnable code.

## Agent Projects

| Project | Description | Technologies |
| --- | --- | --- |
| [ProcureCompare AI](agents/procurecompare-ai/) | Sources products, compares prices, and generates a procurement recommendation report. | CrewAI, OpenAI, Tavily, ScrapeGraphAI, AgentOps |

## Repository Structure

```text
Agent/
├── agents/
│   └── procurecompare-ai/
│       ├── ProcureCompare_AI.ipynb
│       ├── requirements.txt
│       ├── .env.example
│       └── README.md
├── .gitignore
└── README.md
```

## Getting Started

Choose a project from the table above, open its directory, and follow its README. Each agent project keeps its own dependencies and environment-variable template so projects can evolve independently.

## Goals

- Practice multiple agent frameworks and orchestration patterns.
- Build agents for different real-world use cases.
- Compare tools, memory strategies, observability, and evaluation methods.
- Keep every example reproducible and documented.

## Security

Never commit API keys, local `.env` files, generated outputs, or observability logs.
