# RAG for Autonomous Scientific Agents

A literature-grounding framework for autonomous scientific agents that retrieves relevant scientific evidence and provides it to an AI agent during experimental data analysis and scientific reasoning.

This repository contains the Retrieval-Augmented Generation (RAG) component developed for the Agentic Scientific Data Assistant.

## Architecture

The framework separates experimental-data analysis from literature retrieval:

    Experimental Data
          |
        DataFed
          |
      MCP Tools
          |
    Scientific Agent
          |
          | search_scientific_literature()
          v
      RAG Service
          |
    SFR Embeddings
          |
     FAISS Search
          |
    MMR Reranking
          |
    Scientific Literature

The scientific agent accesses experimental data and executes analysis through MCP tools. The RAG service independently retrieves literature evidence relevant to the agent's scientific question and experimental context.

## Retrieval Pipeline

The literature retrieval pipeline uses:

- scientific-document ingestion and chunking
- SFR text embeddings
- FAISS vector similarity search
- Maximum Marginal Relevance (MMR) reranking
- Top-K evidence retrieval
- FastAPI service interface

`build_scientific_kb_sfr.py` constructs the searchable literature knowledge base.

`rag_service.py` provides the retrieval service used by the scientific agent.

## Installation

Create a Python environment:

    python -m venv rag_env
    source rag_env/bin/activate

Install the frozen dependencies:

    pip install -r requirements.txt

## Knowledge Base

The knowledge base is generated from a scientific literature corpus using:

    python build_scientific_kb_sfr.py

Generated FAISS indexes, serialized knowledge-base files, and source PDFs are intentionally excluded from this repository.

## Evaluation

The `evaluation/` directory contains the framework used to evaluate retrieval and literature-grounded question answering.

Evaluation includes:

- 50-question literature retrieval benchmark
- source-level retrieval evaluation
- chunk-level retrieval evaluation
- semantic relevance evaluation
- Gemma-only versus RAG+Gemma ablation
- blinded answer scoring
- bootstrap confidence intervals
- paired statistical testing
- manual audit

## Validation Results

Across the 50-question benchmark:

- originating paper retrieved within Top-3: 86%
- at least one semantically relevant passage within Top-3: 84%
- at least one semantically relevant passage within Top-5: 90%
- directly answering evidence within Top-3: 72%
- directly answering evidence within Top-5: 80%

In the literature question-answering ablation, RAG+Gemma outperformed Gemma alone on 37 of 50 questions (74%), with improvements in correctness, completeness, overall answer quality, and reduction of unsupported claims.

Detailed numerical results are provided in `results/`.

## Repository Structure

    .
    ├── build_scientific_kb_sfr.py
    ├── rag_service.py
    ├── requirements.txt
    ├── evaluation/
    │   ├── build_rag_benchmark.py
    │   ├── calculate_rag_metrics.py
    │   ├── evaluate_rag_semantic_relevance.py
    │   ├── calculate_semantic_metrics.py
    │   ├── run_rag_ablation.py
    │   ├── score_rag_ablation_blinded.py
    │   ├── calculate_ablation_statistics.py
    │   └── audit_ablation_sample.py
    └── results/

## Integration with the Scientific Data Agent

This RAG service is designed to operate as the literature-evidence layer of the Agentic Scientific Data Assistant.

The agent invokes literature retrieval through the MCP tool `search_scientific_literature`. This keeps experimental measurements, executable scientific analysis, and external literature evidence as distinct information sources while allowing the LLM to reason across them.

## Reproducibility

The Python environment is captured in `requirements.txt`.

Large generated artifacts and source literature are not stored in GitHub. They can be regenerated using the knowledge-base construction pipeline when an appropriate literature corpus and embedding service are available.
