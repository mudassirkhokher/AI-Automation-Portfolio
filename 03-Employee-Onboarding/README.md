# Employee Onboarding & IT Provisioning Automation

An automated employee onboarding workflow designed to coordinate HR and IT onboarding activities using **n8n, Google Sheets, Google Calendar, Slack, email, and JavaScript**.

The workflow manages employee onboarding from initial data intake through validation, department-specific processing, communication, scheduling, notifications, and completion tracking.

---

## Overview

The automation follows a structured onboarding process:

```text
New Employee
     ↓
Data Normalization
     ↓
Duplicate Check
     ↓
Validation
     ↓
Department Routing
     ↓
Department-Specific Actions
     ↓
Welcome Communication
     ↓
Calendar Scheduling
     ↓
Manager Notification
     ↓
Onboarding Tracking
     ↓
HR Completion Report
```

The workflow is designed as a centralized onboarding process while allowing different departments to receive department-specific information and actions.

---

## Business Problem

Employee onboarding often requires coordination between HR, IT, managers, and different departments.

Common manual tasks include:

* Checking employee information
* Detecting duplicate records
* Validating onboarding data
* Sending welcome emails
* Preparing department-specific information
* Scheduling orientation activities
* Notifying managers
* Tracking onboarding progress
* Preparing completion reports

This project demonstrates how these activities can be coordinated through a centralized automation workflow.

---

## Solution

The workflow automates the onboarding process from employee intake through completion tracking.

It provides:

1. Employee data intake
2. Data normalization
3. Duplicate checking
4. New employee validation
5. HR validation notification
6. Department-based routing
7. Department-specific email information
8. Welcome communication
9. Email status tracking
10. Day 1 orientation scheduling
11. Week 1 check-in scheduling
12. Calendar status tracking
13. Manager Slack notification
14. Onboarding tracker updates
15. HR completion reporting

---

# Workflow Architecture

## 1. Employee Intake

The workflow starts from employee information maintained in Google Sheets.

The incoming data is normalized and prepared for processing.

---

## 2. Validation & Duplicate Checking

Before onboarding actions are performed, the workflow checks the employee information.

The process includes:

* Data normalization
* Required-field validation
* Duplicate checking
* New employee verification
* Validation status handling

If validation requires HR attention, the workflow can send a validation notification rather than continuing blindly.

---

## 3. Department Routing

The workflow routes employees according to their department.

Department-specific processing is included for areas such as:

* Sales
* Engineering / Product
* HR
* Finance / Accounting

This allows different departments to receive relevant onboarding information without creating completely separate onboarding systems.

---

## 4. Welcome Communication

After the employee passes the required validation stages, the workflow prepares and sends onboarding communication.

The workflow also records the email processing status.

---

## 5. Calendar Scheduling

The automation creates onboarding-related calendar events, including:

### Day 1 Orientation

A calendar event is created for the employee's initial orientation.

### Week 1 Check-In

A follow-up event is scheduled for the employee's first-week check-in.

Calendar processing status is tracked within the workflow.

---

## 6. Manager Notification

The workflow sends a Slack notification to the relevant manager after the appropriate onboarding actions have been processed.

This reduces the need for manual coordination between HR and management.

---

## 7. Onboarding Tracking

The workflow updates the onboarding tracker with processing information.

The system also generates an HR completion report containing the onboarding status.

---

# Key Engineering Features

### Centralized Workflow

The workflow coordinates multiple onboarding activities from a single automation process.

### Validation Before Processing

Employee information is checked before downstream actions are performed.

### Duplicate Detection

The workflow checks for existing employee records to help prevent duplicate onboarding processes.

### Conditional Department Routing

Different departments follow their own processing paths while remaining part of the same onboarding system.

### Automated Scheduling

Google Calendar is used to automate Day 1 orientation and Week 1 check-in activities.

### Cross-Platform Notifications

The workflow connects HR processes with communication platforms such as email and Slack.

### Status Tracking

Processing statuses are maintained for communication, calendar actions, and onboarding completion.

### Automated Reporting

The workflow provides an HR completion report after onboarding processing.

---

# Technology Stack

| Technology          | Purpose                                |
| ------------------- | -------------------------------------- |
| **n8n**             | Workflow orchestration                 |
| **Google Sheets**   | Employee data and onboarding tracker   |
| **Google Calendar** | Orientation and check-in scheduling    |
| **Slack**           | Manager notifications                  |
| **Email**           | HR and employee communication          |
| **JavaScript**      | Data transformation and workflow logic |

---

# Project Structure

```text
03-Employee-Onboarding/
│
├── workflows/
│   └── Employee Onboarding & IT Provisioning - Production Ready
│
├── screenshots/
│
└── README.md
```

---

# What This Project Demonstrates

This project demonstrates practical experience with:

* n8n workflow automation
* Business process automation
* HR workflow automation
* IT onboarding coordination
* Google Sheets integration
* Google Calendar integration
* Slack integration
* Email automation
* Data validation
* Duplicate detection
* Conditional routing
* JavaScript data processing
* Workflow status tracking
* Automated reporting
* Multi-step workflow orchestration

---

# Project Status

**Status:** Completed Portfolio Project

The workflow represents a production-oriented employee onboarding automation design.

---

# Scope & Limitations

This workflow coordinates onboarding activities, communication, scheduling, notifications, and tracking.

The implementation does **not** by itself demonstrate direct creation of Active Directory accounts, Microsoft 365 accounts, physical device provisioning, or application-access provisioning.

External services require their own accounts, permissions, credentials, and environment-specific configuration.

---

# Screenshots

Selected workflow screenshots are available in the [`screenshots`](./screenshots) directory.

---

# Related Skills

**AI Automation · n8n · Business Process Automation · HR Automation · IT Operations · Google Sheets · Google Calendar · Slack · Email Automation · JavaScript · Workflow Orchestration · Data Validation**
