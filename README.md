AI-Powered Financial Assistant

This is a financial assistant designed for spending analysis and financial education. It operates on a local-first architecture to ensure data privacy, utilizing LangGraph for orchestration and Ollama for local LLM inference.

Features:
- Local-First Execution: All data processing and LLM inference occur on the local machine. No external APIs or cloud services are used.

- Deterministic Analysis: Uses Pandas for financial calculations to ensure mathematical accuracy while leveraging LLMs for intent classification.

- Agentic Workflow: Implements a ReAct-loop state machine to route queries between data tools, educational knowledge bases, and persistent user profiles.

- Compliance Guardrails: Includes a safety node to filter speculative investment queries and provide strictly educational guidance.

- RAG Integration: Uses ChromaDB for local vector storage to retrieve context from financial education documents.

Technical Architecture

The system is built as a directed acyclic graph (DAG) using LangGraph:

Guardrail Node: Checks input for investment speculation or risky financial topics.

Router: Classifies intent into Data, Knowledge, Profile, or Plan categories.

Tools:
- Banking Tool: Executes pandas-based analysis on CSV transaction data.
- Knowledge Tool: Performs similarity searches in a local vector database.
- Profile Tool: Manages long-term goals and preferences in a SQLite database.

Summarizer: Aggregates tool outputs and conversation history for the final response.

Setup and Installation
Prerequisites
Install Ollama.

Pull the required models:

Bash

ollama pull qwen2.5:3b-instruct
ollama pull nomic-embed-text
Installation
Clone the repository and install the dependencies:

Bash

pip install -r requirements.txt
Initialization
Initialize the local SQLite database and ingest the educational PDF documents:

Bash

python init_db.py
python ingest_pdfs.py
Execution
Run the Streamlit dashboard:

Bash

streamlit run app.py
Usage
The application interface consists of two main sections:

Dashboard: For uploading transaction CSVs and viewing spending visualizations.

Coach: A chat interface for querying spending data, calculating savings timelines, or asking financial literacy questions.

Disclaimer
This software is for educational purposes only. It does not provide professional investment or financial advice. The authors are not responsible for any financial decisions made based on the output of this tool.
