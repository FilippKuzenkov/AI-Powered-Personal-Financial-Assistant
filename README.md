AI-Powered Financial Assistant

# Overview

This is a local-first financial assistant focused on
spending analysis and financial literacy. The system is designed to
operate entirely on the user’s machine, ensuring that sensitive
financial data is not transmitted to external services.

The application uses LangGraph for orchestration and Ollama for local
language model inference. All data processing and storage remain local.

------------------------------------------------------------------------

# Features

-   Local inference using Ollama without external APIs
-   Deterministic financial analysis using Pandas
-   Agent-based routing between specialized tools
-   Guardrails to redirect speculative investment requests toward
    educational content
-   Persistent local storage using SQLite and ChromaDB

------------------------------------------------------------------------

# Technical Architecture

The assistant is implemented as a Directed Acyclic Graph (DAG) using
LangGraph.

## Flow

1.  Guardrail Node
    Filters speculative investment intent and risky financial topics.

2.  Router Node
    Classifies user intent into:

    -   DATA (spending analysis)
    -   KNOWLEDGE (financial literacy)
    -   PROFILE (user goals)
    -   PLAN (projections)

3.  Tool Execution

    -   Banking Tool: Processes CSV transaction data using Pandas
    -   Knowledge Tool: Performs retrieval-augmented generation using
        ChromaDB
    -   Profile Tool: Manages long-term user data in SQLite

4.  Summarizer Node
    Aggregates tool outputs into a single response.

------------------------------------------------------------------------

# Setup and Installation

## Prerequisites

Install Ollama and pull the required models:

    ollama pull qwen2.5:3b-instruct
    ollama pull nomic-embed-text

## Installation

Clone the repository and install dependencies:

    pip install -r requirements.txt

## Initialization

Initialize the local database and ingest PDF documents from
rag_docs/pdfs/:

    python init_db.py
    python ingest_pdfs.py

## Execution

Run the Streamlit application:

    streamlit run app.py

------------------------------------------------------------------------

## Usage

-   Dashboard: Upload transaction CSV files and view analysis.
-   Coach: Query spending data, calculate savings timelines, or ask
    financial literacy questions.

------------------------------------------------------------------------

 # Disclaimer

This software is intended for educational purposes only. It provides
financial education and data visualization based on user-provided inputs
and does not constitute professional financial or investment advice.
