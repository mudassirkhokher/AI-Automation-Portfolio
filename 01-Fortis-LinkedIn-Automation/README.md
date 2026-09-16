# AI-Powered LinkedIn Outreach Automation

An automated LinkedIn lead research, personalization, and outreach workflow built with **n8n, OpenAI, PhantomBuster, Google Sheets, and webhooks**.

The system is designed to take qualified leads from a structured lead list, research their LinkedIn profiles, generate personalized messaging using verified information, and manage the outreach workflow through separate processing stages.

---

## Overview

The automation manages the LinkedIn outreach process through a modular workflow architecture:

```text
Lead Intake
    ↓
Validation & Qualification
    ↓
Queue Management
    ↓
Research Preparation
    ↓
LinkedIn Research
    ↓
AI Personalization
    ↓
Campaign Processing
    ↓
Status & Audit Tracking
```

Instead of placing the entire process into one large workflow, the system separates lead management, research, AI personalization, and campaign processing into dedicated workflows.

---

## Business Problem

Manual LinkedIn outreach can require significant time for:

* Reviewing and qualifying leads
* Checking decision-maker seniority
* Researching LinkedIn profiles
* Preparing personalized messages
* Tracking outreach status
* Managing follow-ups
* Maintaining lead and campaign records

This project demonstrates how these processes can be coordinated through an automated workflow system.

---

## Solution

The system uses a multi-workflow n8n architecture to:

1. Import leads from Google Sheets
2. Normalize and validate lead information
3. Check for duplicates
4. Filter leads based on configured seniority criteria
5. Add qualified leads to a processing queue
6. Prepare leads for LinkedIn research
7. Launch external LinkedIn research through PhantomBuster
8. Monitor research completion
9. Normalize and store research results
10. Generate personalized messaging using OpenAI
11. Process campaign results
12. Update lead and campaign statuses
13. Maintain workflow and campaign logs

---

## Workflow Architecture

### 1. Lead Intake & Queue Manager

**Workflow:** `WF01 Lead Intake & Queue Manager`

The intake workflow manages the initial lead-processing stage.

Key functions include:

* Google Sheets lead ingestion
* Data normalization
* Input validation
* Duplicate checking
* Lead ID generation
* Seniority normalization
* Allowed seniority filtering
* Queue management
* Lead status updates
* Audit logging

---

### 2. Research Preparation

**Workflow:** `WF02 Research Preparation`

Prepares qualified leads for the research stage and passes the required information to the research dispatcher.

---

### 3. Research Dispatcher

**Workflow:** `WF02A Research Dispatcher`

Connects the n8n workflow with PhantomBuster to initiate LinkedIn profile research.

The workflow:

* Prepares the research request
* Launches the PhantomBuster process
* Captures the resulting container/job ID
* Stores the processing state for later retrieval

---

### 4. LinkedIn Research

**Workflow:** `WF02B Research`

Handles the asynchronous research process.

The workflow:

* Polls the PhantomBuster process
* Detects completion
* Processes the returned research data
* Normalizes the research output
* Updates the lead queue
* Passes completed research to the AI personalization stage

---

### 5. AI Personalization

**Workflow:** `WF03 AI Personalization`

Uses an AI Agent with an OpenAI model and structured output parsing to generate personalization data.

The workflow validates the input research before sending it to the AI system.

The AI output is designed around structured personalization fields such as:

* Greeting
* Connection reference sentence
* Personalized opening sentence
* Confidence
* Fallback
* Reason

The prompt is designed to use **verified information only** and avoid inventing personal or professional details.

---

### 6. Campaign Input

**Workflow:** `WF04 Campaign Input`

Prepares campaign information for the outreach process and provides the required input for campaign execution.

---

### 7. Campaign Result Processing

**Workflow:** `WF05 Read Phantom Results`

Processes campaign results received through a webhook.

The workflow:

* Receives PhantomBuster results
* Normalizes the returned payload
* Matches results to leads and queue records
* Maps campaign statuses
* Updates lead and queue information
* Records campaign activity

---

## Key Engineering Features

### Modular Workflow Architecture

The system separates major business functions into independent workflows rather than implementing everything inside one workflow.

This makes the system easier to maintain, troubleshoot, and extend.

### Queue-Based Processing

Leads are placed into a processing queue with status information, allowing different stages of the automation to process leads independently.

### Asynchronous Processing

PhantomBuster research can take time to complete. The system therefore launches the research process and subsequently polls for completion rather than assuming an immediate response.

### Input Validation

Lead data is validated and normalized before progressing through the system.

### Structured AI Output

The AI personalization stage uses structured output parsing instead of relying on an unrestricted text response.

### Verified-Information Personalization

The personalization prompt is designed to use available verified information and avoid fabricated facts or generic personalization.

### Status Tracking & Audit Logging

The system maintains processing statuses and campaign records across the workflow stages.

---

## Technology Stack

| Technology        | Purpose                                    |
| ----------------- | ------------------------------------------ |
| **n8n**           | Workflow orchestration                     |
| **OpenAI**        | AI-powered personalization                 |
| **PhantomBuster** | LinkedIn research and campaign integration |
| **Google Sheets** | Lead data and workflow records             |
| **Webhooks**      | Event and campaign result handling         |
| **JavaScript**    | Data transformation and workflow logic     |

---

## Project Structure

```text
01-Fortis-LinkedIn-Automation/
│
├── workflows/
│   ├── WF01 Lead Intake & Queue Manager
│   ├── WF02 Research Preparation
│   ├── WF02A Research Dispatcher
│   ├── WF02B Research
│   ├── WF03 AI Personalization
│   ├── WF04 Campaign Input
│   └── WF05 Read Phantom Results
│
├── screenshots/
│
└── README.md
```

---

## What This Project Demonstrates

This project demonstrates practical experience with:

* n8n workflow architecture
* Multi-workflow orchestration
* AI Agent workflows
* OpenAI integration
* Structured LLM outputs
* LinkedIn automation workflows
* PhantomBuster integration
* Webhooks
* Google Sheets integration
* Queue-based processing
* Data validation and normalization
* Asynchronous workflow processing
* Status management
* Audit logging
* AI-assisted personalization

---

## Project Status

**Status:** Completed Client Project

The workflow architecture and automation components documented here represent the project implementation and portfolio demonstration.

---

## Important Notes

This repository contains a sanitized portfolio representation of the automation system.

Actual credentials, authentication tokens, private client information, and sensitive configuration are not included.

External services such as PhantomBuster, OpenAI, Google Sheets, and LinkedIn-related integrations require their own accounts, credentials, permissions, and configuration.

The workflow demonstrates the automation architecture and implementation; actual execution depends on the configured external services and environment.

---

## Screenshots

Selected screenshots are available in the [`screenshots`](./screenshots) directory.

---

## Related Skills

**AI Automation · n8n · AI Agents · OpenAI · LinkedIn Automation · Lead Generation · Lead Research · Workflow Orchestration · API Integration · Webhooks · Google Sheets · PhantomBuster · Structured AI Output · Business Process Automation**
