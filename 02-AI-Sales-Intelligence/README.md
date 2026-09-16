# AI Sales Intelligence & CRM

An AI-powered sales intelligence and CRM enrichment system built with **n8n, Python, OpenAI, Tavily, Google Sheets, HTTP APIs, and structured data processing**.

The system automates company research, evidence collection, AI enrichment, and lead scoring through a modular multi-workflow architecture.

---

## Overview

The automation transforms raw lead information into a structured sales intelligence record.

```text
Lead Intake
    ↓
Validation & Normalization
    ↓
Company Research
    ↓
Web Search & Page Retrieval
    ↓
Evidence Extraction
    ↓
AI Enrichment
    ↓
Python Scoring
    ↓
Final Sales Intelligence Record
```

The system separates research, AI enrichment, and deterministic scoring into different processing stages.

---

## Business Problem

Sales teams often spend significant time manually researching companies and evaluating leads before beginning outreach.

Typical manual tasks include:

* Cleaning lead information
* Identifying the correct company
* Searching for company information
* Reviewing multiple sources
* Extracting relevant business information
* Enriching CRM records
* Evaluating lead quality
* Assigning qualification scores

This project demonstrates how these processes can be automated into a structured intelligence pipeline.

---

## Solution

The system consists of four primary workflows:

1. **Lead Intake & Normalization**
2. **Company Research Engine**
3. **AI Enrichment**
4. **Python Scoring Engine**

Together, these workflows create a structured pipeline from raw lead data to an enriched and scored sales record.

---

# Workflow Architecture

## 1. Lead Intake & Normalization

**Workflow:** `WF-01 Lead Intake & Normalization`

The workflow receives lead information and prepares it for downstream processing.

Key functions include:

* Lead ingestion
* Data normalization
* Input validation
* Company/lead information preparation
* Conditional routing
* Workflow handoff

The goal is to establish a clean and consistent data structure before research begins.

---

## 2. Company Research Engine

**Workflow:** `WF-02 Company Research Engine`

This is the primary research workflow.

It performs multi-stage company research using web search and page retrieval.

### Research Pipeline

```text
Research Configuration
        ↓
Query Generation
        ↓
Query Splitting
        ↓
Web Search
        ↓
Result Normalization
        ↓
URL Normalization
        ↓
Deduplication
        ↓
Source Classification
        ↓
Page Retrieval
        ↓
Retrieval Classification
        ↓
HTML Extraction
        ↓
Evidence Preparation
        ↓
Information Extraction
        ↓
Research Aggregation
        ↓
Research Consolidation
        ↓
Quality Check
```

The workflow is designed to separate **search discovery, retrieval, extraction, and consolidation** rather than relying on a single AI request.

---

## Research Configuration

The research engine uses configurable limits to control the research process, including:

* Maximum search queries
* Results per query
* Maximum pages to retrieve
* Content limits
* Request timeout
* Retry configuration

This helps control research depth and external API usage.

---

## Source & Retrieval Handling

The research workflow normalizes and classifies discovered sources before processing them.

It also handles retrieval conditions such as:

* CAPTCHA
* Cloudflare
* Access denied
* HTTP errors
* Empty responses
* Rate limiting

This allows downstream processing to distinguish usable research content from unsuccessful retrieval attempts.

---

## 3. AI Enrichment

**Workflow:** `WF-03 AI Enrichment`

The enrichment workflow receives the consolidated research information and uses an OpenAI model to produce structured business information.

The workflow includes:

* Input validation
* AI context preparation
* OpenAI processing
* Structured output parsing
* Enrichment status
* Company identity status
* Workflow handoff

Example processing states include:

```text
ENRICHED
PARTIAL
NEEDS_REVIEW
FAILED
```

Company identity confidence is also represented through structured status values.

---

## 4. Python Scoring Engine

**Workflow:** `WF-04 Python Scoring Engine`

The final stage uses Python for deterministic scoring rather than asking the LLM to make the final numerical decision.

The workflow:

1. Receives the enrichment handoff
2. Validates the scoring context
3. Prepares scoring inputs
4. Runs the Python scoring engine
5. Validates the resulting score
6. Builds the final handoff object

This separates:

**AI-based enrichment**

from

**deterministic business scoring logic.**

---

# Key Engineering Features

### Modular Architecture

Research, enrichment, and scoring are separated into dedicated workflows.

This makes the system easier to maintain and extend.

### Data Normalization

Raw lead and research data is normalized before downstream processing.

### Evidence-Oriented Research

Search results and retrieved pages are processed through multiple stages before being consolidated into the research object.

### Source Deduplication

URLs and research sources are normalized and deduplicated to reduce redundant processing.

### Structured AI Output

The enrichment workflow uses structured output rather than relying on unrestricted text responses.

### Validation

Validation stages are used throughout the workflow handoffs and scoring pipeline.

### Deterministic Scoring

Python is used for the scoring stage, keeping business scoring logic separate from probabilistic LLM output.

### Workflow Handoffs

The workflows exchange structured data between processing stages, allowing the system to operate as a modular pipeline.

---

# Technology Stack

| Technology        | Purpose                                      |
| ----------------- | -------------------------------------------- |
| **n8n**           | Workflow orchestration                       |
| **Python**        | Deterministic scoring                        |
| **OpenAI**        | AI enrichment and information extraction     |
| **Tavily**        | Web research                                 |
| **Google Sheets** | Lead data source                             |
| **HTTP APIs**     | Web page retrieval and external integrations |
| **JavaScript**    | Data transformation and workflow logic       |

---

# Project Structure

```text
02-AI-Sales-Intelligence/
│
├── workflows/
│   ├── WF-01 Lead Intake & Normalization
│   ├── WF-02 Company Research Engine
│   ├── WF-03 AI Enrichment
│   └── WF-04 Python Scoring Engine
│
├── screenshots/
│
└── README.md
```

---

# What This Project Demonstrates

This project demonstrates practical experience with:

* n8n workflow orchestration
* Modular automation architecture
* Python automation
* AI/LLM integration
* OpenAI
* Web research automation
* Tavily integration
* HTTP/API integration
* Data normalization
* URL normalization
* Source classification
* Deduplication
* Evidence extraction
* Structured AI output
* Validation
* Deterministic scoring
* Multi-workflow handoffs
* Sales intelligence automation

---

# Project Status

**Status:** Portfolio Project — Completed

The workflows demonstrate the architecture and implementation of an automated sales intelligence and lead enrichment pipeline.

---

# Limitations

This repository demonstrates the workflow architecture and implementation.

Actual research results and execution depend on:

* External API availability
* API credentials and configuration
* Target website accessibility
* Rate limits
* Runtime environment
* Data quality of the input leads

The workflow design should therefore be considered an automation implementation and portfolio demonstration rather than a guarantee of successful retrieval from every website.

---

# Screenshots

Selected workflow screenshots are available in the [`screenshots`](./screenshots) directory.

---

# Related Skills

**AI Automation · n8n · Python · OpenAI · Tavily · Web Research · Lead Enrichment · Sales Intelligence · Data Processing · Structured AI · Workflow Orchestration · API Integration · Business Process Automation**
