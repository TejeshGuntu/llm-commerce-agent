# AI Commerce Analytics Agent
Natural Language → SQL for E-commerce Data using LLaMA 3

This repository contains an AI-powered analytics assistant designed for e-commerce datasets. The system allows users to ask business questions in plain English and automatically retrieves answers by generating and executing SQL queries on a local database.

The agent runs a locally hosted LLaMA 3 model through Ollama, converts user queries into SQL statements, executes them on an SQLite database, and returns the results through a FastAPI service.

The goal is to provide an easy interface for exploring marketing and sales metrics without writing SQL manually.

## Key Capabilities
- **Natural Language Querying** – Users ask questions in plain English, and the system translates them into SQL automatically.
- **Local LLM Inference** – LLaMA 3 runs locally through Ollama, providing private inference without external APIs.
- **API-Based Architecture** – A FastAPI backend exposes endpoints that convert requests to SQL, execute them, and stream results.
- **Streaming Responses** – Answers can stream progressively, producing a real-time typing experience.
- **Lightweight Database** – All product, marketing, and performance metrics live inside a local SQLite database.
- **Modular Design** – LLM generation, SQL execution, and API services are separated for easy customization.

## Repository Structure

```
E-commerce_ai_agent/
│
├── .venv/                     # Python virtual environment
├── .gitignore                 # Git ignore configuration
├── README.md                  # Project documentation
│
├── Product-Level *.xlsx       # Raw e-commerce datasets
│
├── load_data_to_db.py         # Converts Excel data to sqlite
├── ecommerce.db               # Generated SQLite database
│
├── llama_sql_generator.py     # Converts questions into SQL via LLaMA
├── llama_sql_executor.py      # Executes SQL queries in SQLite
│
├── api_server.py              # FastAPI application exposing the agent
│
└── test_database_queries.py   # Utility for manual SQL testing
```

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
   ```
2. **Create a virtual environment**
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```
3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
   If a `requirements.txt` is missing, install the essentials manually:
   ```bash
   pip install fastapi uvicorn requests
   ```

## Workflow

1. **Launch the local LLM**
   - Make sure Ollama is installed and running.
   - Start the model:
     ```bash
     ollama run llama3
     ```
2. **Build the database**
   ```bash
   python load_data_to_db.py
   ```
   This produces `ecommerce.db`.
3. **Start the FastAPI server**
   ```bash
   uvicorn api_server:app --reload
   ```
   Swagger UI becomes available once the server starts.

## Example Questions

- What are the total sales generated?
- Compute the return on ad spend (RoAS).
- Which product has the highest cost-per-click?
- Show advertising spend aggregated by month.
- Calculate the monthly average click-through rate.
- Identify the top five products by advertising revenue.
- Display the number of clicks received by each product.
- Find the product with the lowest RoAS.
- What is the total number of impressions?
- List the three best-performing products by sales.

## Technology Stack

| Layer          | Tools                        |
|----------------|------------------------------|
| Language Model | LLaMA 3 (Ollama)             |
| Backend API    | FastAPI                      |
| Database       | SQLite                       |
| Dataset Format | Excel (.xlsx)                |
| API Testing    | cURL / Swagger               |
| JSON Formatting| jq                           |

## Author

Tejesh Guntu
---
