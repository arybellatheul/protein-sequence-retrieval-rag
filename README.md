# protein-sequence-retrieval-rag
Protein sequence retrieval system using gLM2 embeddings and Chroma vector search to support protein annotation and biological similarity analysis.

# Protein Sequence Retrieval Using gLM2 Embeddings and Chroma

## Overview

This project explores how protein language model embeddings and vector
similarity search can support protein detection and annotation.

As part of research conducted in the University of Rhode Island AI Lab,
I developed and tested a prototype retrieval system that converts protein
sequences into vector embeddings, stores those embeddings in a Chroma
vector database, and retrieves similar protein sequences using
similarity-based search.

The prototype was developed as part of a larger research effort focused
on identifying and interpreting plastic-degrading proteins.

## Research Context

Identifying proteins capable of degrading plastics is an important
computational biology problem with potential environmental applications.

The larger research project compared two approaches to protein annotation:

- A pipeline-based reference dataset (PDG-Finder)
- A transformer-based protein language model (Gaia / gLM2)

The project later expanded toward a retrieval-based system designed to
store protein representations and retrieve biologically relevant matches
that could provide additional context for model predictions.

## My Contribution

As part of the University of Rhode Island AI Lab, I focused on developing
and testing the retrieval component of the larger protein detection and
annotation project.

My work included:

- Building a prototype vector database using Chroma in Google Colab
- Loading and preparing protein sequence data
- Generating protein sequence embeddings using gLM2
- Structuring an embedding → storage → retrieval workflow
- Performing similarity-based queries
- Validating nearest-neighbor retrieval behavior on smaller datasets
- Exploring FAISS and Qdrant as potential vector database alternatives
- Contributing to early database architecture and scalability discussions

## System Architecture

The prototype follows the general workflow:

Protein Sequence
        ↓
gLM2 Protein Language Model
        ↓
Vector Embedding
        ↓
Chroma Vector Database
        ↓
Cosine Similarity Search
        ↓
Top-K Similar Protein Sequences
        ↓
Metadata / Biological Context

This structure allows a target protein sequence to be represented
numerically and compared against previously embedded protein sequences.

## Technologies

- Python
- Google Colab
- gLM2 protein language model
- Chroma
- Vector embeddings
- Cosine similarity
- Pandas
- NumPy
- Hugging Face / Transformers

Additional vector database technologies explored:

- FAISS
- Qdrant

## Methodology

### 1. Protein Sequence Preparation

Protein sequence data was loaded and prepared for embedding. Sequence
identifiers and associated metadata were maintained so retrieved vectors
could be connected back to their biological records.

### 2. Embedding Generation

Protein sequences were passed through the gLM2 protein language model to
generate numerical vector representations.

These embeddings provide a representation that can be used to compare
protein sequences in vector space.

### 3. Vector Storage

Generated embeddings were stored in a Chroma collection along with
metadata identifying the corresponding protein records.

Cosine similarity was used as the distance metric for retrieval.

### 4. Similarity Retrieval

A query protein sequence was embedded using the same model and compared
against the vectors stored in Chroma.

The system returned the top matching sequences based on vector similarity.

### 5. Retrieval Validation

Similarity-based queries were tested on smaller datasets to confirm that
the embedding → storage → retrieval pipeline functioned correctly.

Retrieval behavior and returned metadata were inspected to validate that
nearest-neighbor search was working as expected.

## Retrieval Workflow

The basic retrieval process is:

1. Select a protein sequence.
2. Generate its gLM2 embedding.
3. Submit the embedding to the Chroma collection.
4. Calculate similarity against stored protein embeddings.
5. Retrieve the top-k nearest matches.
6. Return the associated protein metadata for interpretation.

This creates the retrieval foundation for a larger system that could use
relevant biological context to support protein annotation and model
interpretation.

## Results

The prototype successfully demonstrated an end-to-end protein retrieval
workflow:

- Protein sequences could be converted into embeddings.
- Embeddings could be stored and indexed using Chroma.
- Similarity queries successfully returned nearest-neighbor protein records.
- Retrieved records retained metadata that could be used for downstream
  biological interpretation.

The broader research also identified differences between model and
reference similarity results, reinforcing the importance of understanding
how embedding-generation and similarity methods affect retrieval.

## Repository Structure

```text
protein-sequence-retrieval-rag/
│
├── README.md
└── notebooks/
    └── protein_sequence_retrieval.ipynb
