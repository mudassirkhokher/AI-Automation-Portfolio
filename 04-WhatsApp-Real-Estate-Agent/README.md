# WhatsApp Real Estate Lead-Gen AI Agent

## Overview

This project is an AI-powered WhatsApp lead-generation and qualification system built with **n8n, WhatsApp, OpenAI, Google Calendar, and workflow-based business logic**.

The system engages incoming leads through WhatsApp, collects and processes their requirements, uses an AI agent to qualify the lead, and routes qualified prospects toward appointment booking and broker notification.

It also provides a separate nurture path for leads that are not immediately qualified.

---

## Business Problem

Real estate businesses often receive leads through messaging channels but still rely on manual processes to:

* Collect lead information
* Understand buyer requirements
* Determine whether a lead is qualified
* Schedule appointments
* Notify brokers
* Handle leads that are not ready to book

Manual handling can result in delayed responses, inconsistent qualification, and missed opportunities.

---

## Solution

The workflow automates the initial lead-handling process through WhatsApp.

A typical flow is:

**WhatsApp Lead → Data Extraction → Conversation Memory → AI Qualification → Qualification Decision → Booking / Nurture → Broker Notification**

The AI handles conversational understanding while deterministic workflow logic controls important business decisions.

---

# Workflow Architecture

### 1. WhatsApp Webhook

The workflow receives incoming WhatsApp messages through a webhook.

The webhook acts as the entry point for the lead conversation.

---

### 2. Message Filtering & Acknowledgement

Incoming messages are filtered and processed before continuing through the workflow.

The system also provides a webhook acknowledgement so the incoming request can be handled correctly.

---

### 3. Lead Information Extraction

Relevant information is extracted from the incoming conversation.

This allows the workflow to build structured context that can be used by the AI agent and downstream business logic.

---

### 4. Conversation Memory

Conversation memory is used to maintain context across interactions.

This allows the AI agent to work with information collected during the conversation rather than treating every message as an isolated request.

---

### 5. AI Lead-Gen Agent

The workflow uses **OpenAI** together with an **n8n AI Agent** to understand the conversation and assist with lead qualification.

The AI can work with the collected lead context and determine the appropriate response and qualification information.

---

### 6. Structured AI Output

The AI response is parsed into structured information before the workflow continues.

This creates a controlled interface between the AI layer and the deterministic workflow logic.

---

### 7. Qualification Decision

After the AI processing, the workflow uses deterministic qualification logic to determine the next path.

This separates conversational AI from important workflow decisions.

The two main paths are:

**Qualified Lead → Appointment Booking**

**Not Immediately Qualified → Nurture Path**

---

### 8. Appointment Booking

Qualified leads can be directed toward **Google Calendar** appointment scheduling.

Once the booking process is completed, the workflow can send a confirmation message back through WhatsApp.

---

### 9. Broker Notification

When a qualified lead reaches the appropriate stage, the workflow notifies the broker.

This allows the human sales team to take over at the appropriate point in the process.

---

### 10. Nurture Path

Leads that are not immediately qualified are routed through a separate nurture response.

The workflow records the nurture result and can provide an appropriate response to the lead.

**Note:** The current workflow does not demonstrate a full external CRM tagging implementation for nurture leads.

---

# Key Engineering Features

### AI + Deterministic Logic

The project combines AI-based conversation handling with deterministic workflow decisions.

This reduces the dependency on the LLM for critical routing decisions.

### Conversational Memory

Conversation context is maintained so the AI can work with information gathered throughout the interaction.

### Structured AI Processing

AI output is parsed before downstream workflow execution, making the automation more predictable and easier to integrate with other nodes.

### Event-Driven Architecture

The workflow begins from an incoming WhatsApp webhook and processes the lead through a sequence of automated actions.

### Calendar Integration

Qualified leads can be routed into Google Calendar for appointment scheduling.

### Human Handoff

The workflow includes broker notification so qualified leads can transition from automated interaction to human sales handling.

### Conditional Routing

The workflow separates qualified and nurture leads using explicit workflow branches.

---

# Technology Stack

### Automation

* n8n
* Webhooks
* Conditional workflow logic
* Workflow branching
* Conversation memory

### AI

* OpenAI
* n8n AI Agent
* Structured AI output processing

### Communication

* WhatsApp

### Scheduling

* Google Calendar

### Development

* JavaScript / n8n Code nodes

---

# Project Structure

```text
04-WhatsApp-Real-Estate-Agent/
│
├── workflow/
│   └── whatsapp-real-estate-lead-agent.json
│
├── screenshots/
│   ├── workflow-overview.png
│   ├── ai-agent.png
│   ├── qualification-flow.png
│   └── calendar-booking.png
│
└── README.md
```

> Rename the workflow and screenshot filenames above if your actual files use different names.

---

# What This Project Demonstrates

This project demonstrates practical experience with:

* n8n workflow automation
* AI Agents
* OpenAI integration
* WhatsApp automation
* Webhook-based architectures
* Conversational AI
* Conversation memory
* Structured AI output
* Lead qualification
* Conditional business logic
* Google Calendar integration
* Automated customer communication
* Human-in-the-loop workflows
* Business process automation

---

# Project Status

**Completed Portfolio Project**

The workflow has been developed as an AI-powered real estate lead-generation and qualification automation system.

It demonstrates the architecture and implementation of an automated conversational lead-handling process from initial WhatsApp interaction through qualification, booking, and broker notification.

---

# Scope & Limitations

The current implementation demonstrates:

* WhatsApp message intake
* AI-powered conversational processing
* Lead qualification
* Appointment scheduling
* Broker notification
* Nurture routing

The current workflow does **not** demonstrate:

* Full CRM integration for nurture lead tagging
* Automated CRM pipeline management
* Advanced lead scoring beyond the implemented qualification logic
* Production-scale performance metrics

These capabilities could be added as future extensions.

---

# Screenshots

### Workflow Overview

![Workflow Overview](screenshots/workflow-overview.png)

### AI Agent

![AI Agent](screenshots/ai-agent.png)

### Qualification Flow

![Qualification Flow](screenshots/qualification-flow.png)

### Calendar Booking

![Calendar Booking](screenshots/calendar-booking.png)

---

# Related Skills

**AI Automation • n8n • AI Agents • OpenAI • WhatsApp Automation • Webhooks • Lead Qualification • Google Calendar • Conversational AI • Workflow Automation • Business Process Automation**
