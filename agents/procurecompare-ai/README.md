# ProcureCompare AI

**Intelligent Product Sourcing and Price Comparison Agent**

A multi-stage AI agent that searches for e-commerce products, extracts their specifications, compares prices, and generates an HTML procurement recommendation report.

The project is implemented in the [`ProcureCompare_AI.ipynb`](ProcureCompare_AI.ipynb) notebook and configured for a local VS Code/Jupyter environment on macOS.

## How It Works

The CrewAI workflow runs sequentially:

1. Generate targeted search queries based on the product, websites, and country.
2. Search the web with Tavily and filter out low-relevance results.
3. Extract product information from e-commerce pages with ScrapeGraphAI.
4. Generate an HTML comparison and recommendation report.

Generated files are saved in `procurecompare-output/`:

| File | Contents |
| --- | --- |
| `step_1_suggested_search_queries.json` | Suggested search queries |
| `step_2_search_results.json` | Filtered search results |
| `step_3_search_results.json` | Extracted products and specifications |
| `step_4_procurement_report.html` | Final procurement report |

## Requirements

- Python 3.10 through 3.12 (`crewai==0.114.0` is not compatible with Python 3.13 or 3.14)
- API keys for OpenAI, Tavily, and ScrapeGraphAI
- An optional AgentOps API key for observability

## Local Installation

From the repository root, enter this project directory:

```bash
cd agents/procurecompare-ai
```

Using Conda (recommended for Miniconda users):

```bash
conda create --name ai-agent python=3.12
conda activate ai-agent
python -m pip install -r requirements.txt
```

Using `venv`, explicitly select an installed Python 3.12 interpreter:

```bash
python3.12 -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

Create your local environment file:

```bash
cp .env.example .env
```

Open `.env` and replace the example values with your API keys. This file is excluded from Git. The notebook reports any missing required key clearly; AgentOps is skipped when its key is absent.

When using VS Code, select the **Python 3.12 (ai-agent)** kernel before running the notebook.

## Configuration

The final notebook cell contains the workflow inputs:

```python
{
    "product_name": "coffee machine for the office",
    "websites_list": ["www.amazon.eg", "www.jumia.com.eg", "www.noon.com/egypt-en"],
    "country_name": "Egypt",
    "language": "English",
    "score_th": 0.10,
    "top_recommendations_no": 10,
}
```

Adjust these values to match your procurement needs. Never commit API keys or output files containing sensitive data.

## Project Structure

```text
.
├── ProcureCompare_AI.ipynb # CrewAI workflow and orchestration
├── requirements.txt        # Python dependencies
├── .env.example            # Environment variable template
└── README.md               # Project documentation
```

## Planned Improvements

- Extract the notebook code into a testable Python package.
- Rename the third output file to `step_3_extracted_products.json` for consistency.
- Add tests for the Pydantic schemas and search/extraction tools.
