# Multi-Document Question Answering with Retrieval-Augmented Generation (RAG)

## Description

This project implements a sophisticated question-answering system utilizing Retrieval-Augmented Generation (RAG) technology to extract and synthesize information from multiple documents, including PDF, PPT, and DOCX formats. The system is designed to understand context and nuances within these documents and generate precise, informative answers to user queries by performing real-time information retrieval and fusing it with a Large Language Model (LLM).

## Table of Contents

- [Objective](#objective)
- [What is RAG?](#what-is-rag)
- [RAG Architecture](#rag-architecture)
- [Indexing](#indexing)
  - [Data Loading](#data-loading)
  - [Data Extraction](#data-extraction)
  - [Chunking](#chunking)
  - [Embeddings Creation](#embeddings-creation)
  - [Indexing (FAISS)](#indexing-faiss)
- [Retrieval and Generation](#retrieval-and-generation)
  - [Retriever](#retriever)
  - [LLM Model](#llm-model)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Libraries Used](#libraries-used)
- [How to Run](#how-to-run)

## Objective

The primary objective is to design, implement, and demonstrate a RAG-based question-answering system capable of ingesting multiple documents, understanding their content, and generating accurate, contextually enriched answers to user queries.

## What is RAG?

RAG is a technique for augmenting LLM knowledge with additional data. It allows AI applications to reason about private or recently introduced data by retrieving relevant information and inserting it into the model prompt.

## RAG Architecture

A typical RAG application has two main components:

1.  **Indexing:** A pipeline for ingesting and indexing data from a source (usually offline).
2.  **Retrieval and Generation:** The RAG chain that takes a user query, retrieves relevant data from the index, and passes it to the model for generating an answer.

## Indexing

### Data Loading

Data is loaded from various sources (PDF, PPT, DOCX) using appropriate libraries.

### Data Extraction

Text is extracted from the loaded documents and combined into a single string for processing.

### Chunking

Large documents are split into smaller chunks using `RecursiveCharacterTextSplitter` to facilitate efficient searching and fit within the LLM's context window.

### Embeddings Creation

Text chunks are converted into dense, high-dimensional vectors (embeddings) using a pre-trained model like `sentence-transformers/all-MiniLM-L6-v2` to capture semantic meaning.

### Indexing (FAISS)

The embeddings are indexed using Facebook AI Similarity Search (FAISS) for efficient similarity search during the retrieval phase.

## Retrieval and Generation

### Retriever

A retriever is created from the FAISS index to find the most relevant document chunks based on a user query using similarity search.

### LLM Model

A Large Language Model (LLM), specifically a Cohere model, is used to generate an answer based on the user's question and the retrieved relevant document chunks.

## Installation

The required libraries can be installed using pip:
