# LedgerMCP

**LedgerMCP** is an open-source **Model Context Protocol (MCP) server** for financial modeling and analysis using **[Financial Modeling Prep](https://site.financialmodelingprep.com/)**.
It exposes **your own financial data**—structured, auditable, and reproducible—as model-ready context for LLMs and agentic systems.

Think of it as a **ledger for models**: a single source of financial truth they can reason over.

---

## Why LedgerMCP?

Modern LLMs are powerful, but they struggle with:

* Private or proprietary financial data
* Structured financial reasoning (statements, cash flows, forecasts)
* Reproducibility and auditability
* Separation between *data*, *logic*, and *models*

LedgerMCP solves this by acting as a **financial context layer** between your data and your models.

**Models don’t own your numbers.
LedgerMCP does.**

---

## What LedgerMCP Does

LedgerMCP implements the **Model Context Protocol (MCP)** to expose financial data and computations in a way that models can reliably consume.

It enables:

* 📊 Access to structured financial statements
* 💸 Cash flow and unit economics context
* 📈 Historical + projected financial data
* 🔍 Deterministic, auditable financial reasoning
* 🧠 Model-agnostic consumption (any MCP-compatible client)

---

## Core Use Cases

* Financial modeling prep for LLMs
* Agent-based financial analysis
* Internal finance copilots
* Scenario analysis and forecasting
* RAG-style financial context (without embedding everything)
* Private financial data access for AI systems

---

## Architecture Overview

```
Your Financial Data
    ├── CSV / Parquet / SQL
    ├── Accounting Systems
    ├── Spreadsheets
    └── Custom Pipelines
           ↓
       LedgerMCP
           ↓
    MCP-compatible Models
    (LLMs, Agents, Tools)
```

LedgerMCP **does not train models**.
It **serves context**—cleanly, deterministically, and transparently.

Read more [here](https://medium.datadriveninvestor.com/build-your-own-financial-data-mcp-server-that-chatgpt-can-talk-to-cec9b68d0b84).

[FMP MCP Server](https://github.com/damianboh/fmp_mcp_server)

---

## Key Features

```python
await company_profile("AAPL")
await income_statement("TSLA")
await financial_ratios("AMZN")
await historical_price_eod_full("MSFT")
await earnings_call_transcript("NVDA", 2025, "3")
await economic_calendar()
await economic_indicators("CPI")
await economic_indicators("unemploymentRate")
await stock_news_latest()
await stock_news_search("AAPL")
await insider_trading_latest()
await insider_trading_search("TSLA")
```

### 📚 Structured Financial Context

Expose:

* Income statements
* Balance sheets
* Cash flow statements
* Unit economics
* KPIs and metrics
* Custom financial schemas

### 🧮 Deterministic Computation

* Financial logic lives **outside** the model
* Calculations are reproducible
* No hallucinated math

### 🔐 Data Ownership & Privacy

* Your data stays local
* No external APIs required
* Fully self-hosted

### 🧠 Model-Agnostic

* Works with any MCP-compatible client
* Not tied to a specific LLM vendor

### 🧾 Auditable by Design

* Clear data lineage
* Explicit assumptions
* Transparent transformations

---

## Example Queries (Conceptual)

Models connected via MCP can ask things like:

* “What is the company’s gross margin trend over the last 8 quarters?”
* “Summarize operating cash flow drivers for FY2024.”
* “What assumptions are used in the current revenue forecast?”
* “Simulate a 10% drop in ARPU and show cash runway impact.”

LedgerMCP provides **the numbers and logic**, not vibes.

---

## Why MCP for Finance?

Finance is structured, deterministic, and assumption-driven—exactly the opposite of how LLMs naturally operate.

The **Model Context Protocol (MCP)** provides a clean separation between **models** and **financial truth**, which is critical for serious financial work.

### The Problem with Naive LLM Finance

Without MCP, models tend to:

* Hallucinate numbers or formulas
* Mix assumptions with conclusions
* Lose track of data lineage
* Recompute the same logic inconsistently
* Embed sensitive financial data directly into prompts or vectors

That’s unacceptable for financial modeling.

### What MCP Changes

MCP lets you expose **financial data, schemas, and computations as explicit context**, not free-form text.

With MCP:

* Numbers come from a trusted source
* Calculations are deterministic and auditable
* Assumptions are explicit
* Models reason *over* finance instead of inventing it
* Data ownership stays with you

### Why This Matters for Finance Specifically

Finance requires:

* Reproducibility
* Traceability
* Precision
* Clear separation of data, logic, and narrative

MCP enforces those boundaries by design.

### LedgerMCP’s Role

LedgerMCP uses MCP to act as a **financial system of record for models**:

* One ledger
* One set of assumptions
* Many models

Models change.
Your financial truth shouldn’t.

---

## Installation

> ⚠️ Early-stage project — APIs may change.

```bash
git clone https://github.com/your-org/ledgermcp
cd ledgermcp
```

```bash
# example (adjust to your stack)
pip install -e .
```

Or via container:

```bash
docker build -t ledgermcp .
docker run -p 3333:3333 ledgermcp
```

---

## Configuration

LedgerMCP is configured via a simple config file:

```yaml
data_sources:
  - type: csv
    path: ./data/financials/

schemas:
  - income_statement
  - balance_sheet
  - cash_flow

currency: USD
fiscal_calendar: calendar
```

You define:

* Where data lives
* How it’s structured
* What context is exposed

---

## MCP Integration

LedgerMCP implements the **Model Context Protocol** and exposes:

* Resources (financial datasets)
* Tools (financial computations)
* Context (metadata, assumptions, schemas)

Compatible with:

* MCP-enabled LLM runtimes
* Agent frameworks
* Custom MCP clients

---

## Philosophy

LedgerMCP follows a few core principles:

* **Models should reason, not invent**
* **Financial data must be auditable**
* **Context > embeddings for structured finance**
* **Open source first**
* **Your ledger, your rules**

---

## Non-Goals

LedgerMCP intentionally does **not**:

* Train or fine-tune models
* Provide investment advice
* Replace accounting systems
* Scrape external financial data by default

---

## Roadmap

* [ ] Financial schema library
* [ ] Scenario simulation tools
* [ ] Forecasting primitives
* [ ] Versioned financial snapshots
* [ ] Access control / permissions
* [ ] Plugin system for custom metrics

---

## Contributing

Contributions are welcome 🙌

Ways to help:

* Add financial schemas
* Improve MCP compatibility
* Write examples and docs
* Build adapters for data sources
* Stress-test with real financial models

See `CONTRIBUTING.md` for details.

---

## License

Apache 2.0
Free to use, modify, and distribute.

---

## Disclaimer

LedgerMCP is a **technical infrastructure project**.
It does **not** provide financial, legal, or investment advice.

---