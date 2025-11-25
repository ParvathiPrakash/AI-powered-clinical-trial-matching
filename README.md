# AI-Powered Clinical Trial Matching System: 

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)]()
[![Hugging Face](https://img.shields.io/badge/HuggingFace-Transformers-yellow)]()
[![FAISS](https://img.shields.io/badge/VectorStore-FAISS-red)]()
[![License](https://img.shields.io/badge/License-MIT-green)]()

This project introduces an intelligent, transparent, and automated pipeline for **matching patients with suitable clinical trials**. By leveraging state-of-the-art **Large Language Models (LLMs)**, specialized semantic embeddings with **BioClinicalBERT**, and **retrieval-augmented generation (RAG)** techniques, we aim to accelerate clinical decision-making, boost patient recruitment efficiency, and provide crucial interpretability for complex healthcare decisions.

## Overview

The current process of matching patients to clinical trials is **labor-intensive**, relying heavily on manual review of complex inclusion/exclusion criteria. This often results in slow recruitment, missed patient opportunities, and a high administrative burden.

Our system automates the semantic comparison between a **patient's complex medical record** and the **trial's dense criteria**.

> **Goal:** To reduce trial screening time from hours or days down to seconds while providing a transparent rationale for the match.

## System Architecture & Core Pipeline

The matching system is a cohesive, multi-stage NLP pipeline:

### 1. Data Ingestion & Preprocessing
* **Input:** Structured clinical trial data (e.g., from ClinicalTrials.gov) and unstructured/semi-structured patient records.
* **Process:** Normalization, tokenization, and cleaning of complex medical terminologies to ensure high-quality input for the embedding model.

### 2. Semantic Encoding (Embedding Generation)
* **Model:** **BioClinicalBERT** (a BERT variant specifically pre-trained on biomedical and clinical notes).
* **Output:** High-dimensional, **dense vector representations** for each trial's key text (Title, Summary, Criteria). This ensures true semantic understanding beyond simple keyword matching.

### 3. High-Speed Indexing (Vector Store)
* **Index:** **FAISS (Facebook AI Similarity Search)**.
* **Function:** Stores the BioClinicalBERT embeddings, enabling lightning-fast **Approximate Nearest Neighbor (ANN)** search, which is essential for scaling to a large database of clinical trials.

### 4. Retrieval-Augmented Generation (RAG)
1.  **Query:** Accepts a patient profile as a natural language query or structured JSON.
2.  **Retrieval:** Retrieves the **top-k semantically similar trials** from the FAISS index.
3.  **Generation (LLM):** The retrieved context (trials) + the patient query are fed into **FLAN-T5-base**. The LLM generates a comprehensive **match report** and a natural language summary explaining the fit.

### 5. Explainability (The Trust Layer)
* **Tools:** **LIME** (Local Interpretable Model-agnostic Explanations) and **SHAP** (SHapley Additive exPlanations).
* **Function:** Provides **model transparency** by visualizing which specific tokens (e.g., "Stage II Melanoma," "Creatinine level $>1.5$") in the patient's record and trial criteria most influenced the final decision.

---

## Key Use Cases 

| Audience | Primary Use Case | Value Delivered |
| :--- | :--- | :--- |
| **Clinicians / Doctors** | Clinical Decision Support | Rapidly identify *all* fitting trials during an appointment. Reduces manual screening time significantly. |
| **Patients** | Patient Portals / Self-Search | Enables natural language searching for trials, democratizing access to clinical research. |
| **Researchers / Sponsors** | Recruitment Optimization | Analyze criteria-matching patterns to refine trial protocols and target recruitment strategies effectively. |

## Tech Stack


| **Language** | Python (3.9+) | Core development language. |

| **Embedding** | `BioClinicalBERT` | Domain-specific semantic vector generation. |

| **LLM** | `FLAN-T5-base` | Contextual generation and report summary. |

| **Vector Index** | `FAISS` | High-speed similarity search indexing. |

| **DL Framework** | PyTorch / Hugging Face | Deep Learning foundation. |

| **Explainability** | `LIME`, `SHAP` | Providing model transparency and trust. |



### Prerequisites

* Python 3.9+
* A Hugging Face API key (optional, depending on deployment setup)

## By :

PES2UG22CS384 - Parvathi P
PES2UG22CS416 - Princia DSouza
PES2UG22CS422 - Raashi Bafna
