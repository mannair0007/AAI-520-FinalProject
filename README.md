# Multi-Agent Financial Analysis System

This project is a part of the AAI-520 course in the Applied Artificial Intelligence Program at the University of San Diego (USD).

**Project Status:** [Completed]

**Final Notebook:** AAI_220_Final_Project_Group8.ipynb

---

## Installation

To use this project, first clone the repo on your device.

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/mannair0007/AAI-520-FinalProject.git
    ```

2.  **Install the required packages:**
    The project requires several Python libraries. You can install them using pip:
    ```bash
    pip install groq yfinance newsapi-python matplotlib
    ```

3.  **Set up API Keys:**
    This system relies on external APIs for its tools. You will need to acquire:
    * A **Groq API key** for LLM access.
    * A **NewsAPI key** for fetching financial news.

    The notebook will prompt you to enter these keys securely using `getpass` when you run the setup cells.

---

## Project Intro/Objective

The main purpose of this project is to implement and demonstrate a fully autonomous, agentic AI financial analyst system. The system is designed to research a given stock symbol by planning its own actions, using external tools to gather real-time data, analyzing and synthesizing that data, and iteratively refining its own output to produce a high-quality, comprehensive investment report.

This project showcases several advanced AI workflow patterns, including self-reflection, routing, and prompt chaining, to create a robust and intelligent agent.

---

## Contributor(s)

* Group 8
  - Manoj Nair
  - Lokesh Upputri
  - Yogesh Sangwikar

---

## Methods Used

* **AI Agent Design:** Planning, Tool Use, Self-reflection (Evaluator-Optimizer Loop), and Learning.
* **Workflow Patterns:** Prompt Chaining, Routing, and State Management.
* **NLP** (Sentiment Analysis, Summarization, Key Point Extraction)
* **Data Visualization**
* **Data Manipulation**

---

## Technologies

* **Python**
* **Groq API** (using Llama 3.3)
* **Jupyter Notebook**
* **APIs:** `yfinance`, `newsapi-python`
* **Data Visualization:** `matplotlib`
* **Utilities:** `json`, `requests`, `textwrap`

---

## Project Description

This project orchestrates a financial analysis by deploying a central agent (`AgenticFinancialAnalyst`) that manages a series of tasks to generate a report on a stock symbol (e.g., "NVDA").

### Datasets
The agent utilizes two external, real-time data sources:
1.  **yfinance:** Provides quantitative financial data, including historical stock prices and company financial statements (Income Statement, Balance Sheet).
2.  **NewsAPI:** Provides qualitative data in the form of recent news articles related to the company, used for sentiment analysis.

### Analysis and Modeling Workflow
The core of the project is its agentic workflow, which dynamically solves the problem of "how to research this stock."

1.  **Planning:** The agent first generates a high-level plan (e.g., `['analyze_news', 'analyze_market_data', 'analyze_financials']`).
2.  **Routing & Tool Use:** A **Router** function continuously decides the next step based on what data is missing. It directs the agent to use the correct tool (`get_financial_news`, `get_stock_price_data`, etc.) to gather data.
3.  **Prompt Chaining:** For news analysis, the agent uses a **Prompt Chain** to sequentially ingest news, classify sentiment, extract key points, and write a summary.
4.  **Synthesis & Self-Reflection:** Once all data is gathered, a "Synthesizer" agent writes an initial draft report. This draft is then passed to an **Evaluator-Optimizer** loop.
    * An "Evaluator" agent (with a "skeptical" persona) critiques the draft.
    * A "Refiner" agent rewrites the report to address the critique, resulting in a higher-quality final output.
5.  **Learning:** The agent stores a brief summary of its final analysis in memory, which it can recall if asked to research the same stock again.

This entire process is visualized for the user through console outputs detailing the agent's thoughts and actions, and a final price trend chart is generated using `matplotlib`.

---

## License

This project is licensed under the MIT License.

---
