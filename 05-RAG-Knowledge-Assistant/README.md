# RAG Knowledge Assistant

## Overview

This project is a Retrieval-Augmented Generation (RAG) knowledge assistant built with **n8n, Google Drive, Supabase Vector Store, Gemini, PostgreSQL, and an AI Agent**.

The system automatically processes knowledge documents, generates vector embeddings, stores them in a vector database, and allows an AI agent to retrieve relevant information when answering user questions.

The architecture combines automated document ingestion, vector search, conversational AI, and persistent chat memory.

---

## Business Problem

Organizations often store important information across documents and internal knowledge bases.

Finding the right information manually can be time-consuming, while a general-purpose AI model may not have access to an organization's private knowledge.

A RAG-based assistant can connect an AI agent to an organization's own document knowledge base.

---

## Solution

The system creates an automated knowledge pipeline:

**Google Drive Documents → Document Processing → Embeddings → Supabase Vector Store → AI Agent → Knowledge Retrieval → Answer**

The assistant can retrieve relevant information from the indexed knowledge base and use it as context when generating responses.

PostgreSQL is also used to maintain conversational memory.

---

# Workflow Architecture

### 1. Google Drive Knowledge Source

Google Drive acts as the source for knowledge documents.

The workflow monitors and processes documents that are added or updated in the connected knowledge source.

---

### 2. Document Ingestion

When a document enters the ingestion workflow, its content is prepared for processing.

The system separates the document-processing stage from the vector storage stage, creating a reusable knowledge ingestion pipeline.

---

### 3. Embedding Generation

The processed knowledge is converted into vector embeddings using **Gemini embeddings**.

These embeddings represent the document content in a format that can be searched using semantic similarity.

---

### 4. Supabase Vector Store

The generated embeddings are stored in **Supabase Vector Store**.

This provides the retrieval layer for the RAG system.

When the AI agent needs information, the vector store can be queried for relevant knowledge.

---

### 5. AI Agent

The system uses an **n8n AI Agent** together with a **Gemini LLM**.

The AI Agent can use the connected knowledge retrieval system as part of its response-generation process.

This allows the assistant to answer questions using information from the indexed knowledge base.

---

### 6. Retrieval-Augmented Generation

The core RAG process is:

**User Question → Relevant Knowledge Retrieval → Context → Gemini → Generated Answer**

Instead of relying only on the model's general knowledge, the workflow provides retrieved information from the organization's document collection.

---

### 7. PostgreSQL Chat Memory

PostgreSQL is used for persistent conversational memory.

This allows the assistant to maintain conversation context across interactions rather than treating every question as completely independent.

---

### 8. Knowledge Updates & Deletions

The workflow also includes vector-store update and deletion handling.

This allows the knowledge index to be maintained when source documents change or are removed.

---

### 9. Google Sheets Tracking

Google Sheets is used as part of the workflow for tracking relevant knowledge-processing information.

This provides an additional operational record around the document-processing workflow.

---

# Key Engineering Features

### Retrieval-Augmented Generation

The project connects an LLM to an external knowledge base through vector search.

### Automated Knowledge Ingestion

Google Drive provides an automated source for bringing organizational documents into the knowledge pipeline.

### Vector Database

Supabase Vector Store provides semantic retrieval capabilities for the RAG system.

### Gemini Integration

Gemini is used for both embedding generation and LLM-based response generation.

### AI Agent Architecture

The n8n AI Agent coordinates the conversational workflow and knowledge retrieval.

### Persistent Conversation Memory

PostgreSQL provides persistent storage for chat memory.

### Knowledge Synchronization

The workflow includes mechanisms for updating and deleting vectorized knowledge when source information changes.

### Modular Architecture

The ingestion and query sides of the system are separated into distinct workflow components, making the architecture easier to maintain and extend.

---

# Technology Stack

### Automation

* n8n
* Workflow triggers
* Workflow branching
* AI Agent
* Automation nodes

### AI / LLM

* Google Gemini
* Gemini Embeddings
* Retrieval-Augmented Generation
* AI Agent

### Data & Storage

* Supabase
* Supabase Vector Store
* PostgreSQL
* Google Sheets

### Knowledge Source

* Google Drive

---

# Project Structure

```text
05-RAG-Knowledge-Assistant/
│
├── workflows/
│   ├── rag-ingestion.json
│   └── rag-knowledge-assistant.json
│
├── screenshots/
│   ├── workflow-overview.png
│   ├── ingestion-workflow.png
│   ├── vector-store.png
│   ├── ai-agent.png
│   └── chat-memory.png
│
└── README.md
```

> Rename the workflow and screenshot filenames above if your actual files use different names.

---

# RAG Architecture

```text
                    KNOWLEDGE INGESTION
                           │
                           ▼
                    ┌──────────────┐
                    │  Google Drive │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │  Processing  │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │    Gemini    │
                    │  Embeddings  │
                    └──────┬───────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ Supabase Vector    │
                 │      Store         │
                 └─────────┬──────────┘
                           │
                           │ Retrieval
                           ▼
USER ───────────────► ┌──────────────┐
                     │   n8n AI      │
                     │    Agent      │
                     └──────┬───────┘
                            │
                    ┌───────┴────────┐
                    ▼                ▼
              ┌──────────┐    ┌────────────┐
              │  Gemini  │    │ PostgreSQL │
              │   LLM    │    │ Chat Memory│
              └────┬─────┘    └────────────┘
                   │
                   ▼
              AI Response
```

---

# What This Project Demonstrates

This project demonstrates practical experience with:

* RAG architecture
* n8n AI Agents
* Google Drive automation
* Vector databases
* Supabase Vector Store
* Gemini LLM integration
* Embedding generation
* Semantic retrieval
* PostgreSQL chat memory
* Knowledge-base automation
* Document ingestion
* Vector updates and deletion
* Conversational AI
* Business knowledge assistants

---

# Project Status

**Completed Portfolio Project**

The project demonstrates an end-to-end RAG knowledge assistant architecture combining automated document ingestion, vector storage, semantic retrieval, AI generation, and persistent conversation memory.

---

# Scope & Limitations

The current implementation demonstrates:

* Automated knowledge ingestion from Google Drive
* Gemini embedding generation
* Supabase vector storage
* AI Agent-based retrieval
* Gemini-powered responses
* PostgreSQL conversation memory
* Knowledge update and deletion handling
* Google Sheets tracking

The current implementation does **not** demonstrate:

* Formal RAG evaluation benchmarks
* Automated retrieval-quality scoring
* Source citation generation in responses
* Advanced document versioning
* Production-scale performance measurements
* A dedicated hallucination evaluation framework

These can be considered future enhancements.

---

# Screenshots

### Workflow Overview

![Workflow Overview](screenshots/workflow-overview.png)

### Knowledge Ingestion

![Knowledge Ingestion](screenshots/ingestion-workflow.png)

### Vector Store

![Vector Store](screenshots/vector-store.png)

### AI Agent

![AI Agent](screenshots/ai-agent.png)

### Chat Memory

![Chat Memory](screenshots/chat-memory.png)

---

# Related Skills

**RAG • AI Agents • n8n • Gemini • Vector Databases • Supabase • PostgreSQL • Embeddings • Semantic Search • Google Drive Automation • Conversational AI • Knowledge Base Automation • Workflow Automation**
