# Information Retrieval Project

This repository contains the implementation and evaluation of various information retrieval methods, including traditional, neural, and generative approaches.

## Project Overview

The project is divided into two main tasks:

1. Comparing traditional and neural retrieval models
2. Exploring generative models for retrieval-augmented generation (RAG)

### Task 1: Traditional vs. Neural Models

- Implement and evaluate the following retrieval methods:
  - Pyserini BM25 (baseline)
  - Standard DPR Dense Retriever
  - TILDEv2

- Evaluation requirements:
  - Retrieve top-10 passages for each method
  - Compare neural models against the BM25 baseline
  - Conduct statistical significance tests
  - Create a summary table of results
  - Generate gain-loss plots at the query level

### Task 2: Exploring Generative Models

- Implement RAG using TinyLlama (or another LLM of choice)
- Design and implement two evaluation methods/measures for RAG-generated answers
- Analyze results for each query
- Create correlation plots for RAG evaluation measures

### Further Tasks

1. Implement point-wise and pair-wise reranking with an LLM
2. Design two additional methods to evaluate RAG-generated answers

## Implementation Details

- Dataset: Sampled from the MS-MARCO passage collection
- Evaluation Measure: NDCG@3 for traditional and neural methods
- Statistical Significance: Paired t-test (p < 0.05 and p < 0.01)

## Repository Structure

- `notebook.ipynb`: Jupyter notebook containing all implementations, evaluations, and discussions
- `project2-task.svg`: Illustration of the project tasks

## How to Use

1. Clone this repository
2. Ensure you have the required dependencies installed (list them here)
3. Run the Jupyter notebook to reproduce the results and analysis



## Contributors

Alvee Mir
