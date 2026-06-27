# AI-Powered Customer Support Ticketing System

A scalable, maintainable, and automation-driven support solution built entirely using core Salesforce Administration and Flow features within a Developer Org. This system centralizes customer data, automates case lifecycles, enforces SLAs, and provides intelligent agent assistance to dramatically reduce support turnaround times.

---

## 🚀 Project Overview & Objectives
Managing rapid influxes of support queries while maintaining strict Service Level Agreements (SLAs) can strain customer service teams. This project addresses that problem by:
* **Centralizing CRM Data:** Linking tickets seamlessly to individual customer personas and enterprise records.
* **Intelligent Automation:** Eliminating manual triage by dynamically classifying, prioritizing, and assigning support tickets as they arrive.
* **Agent Productivity:** Empowering agents with quick actions and contextual UI highlights directly on the ticket canvas.
* **Continuous Improvement:** Capturing real-world agent feedback to track system accuracy and identify performance gaps.

---

## 📊 System Architecture & Data Schema
The platform builds on Salesforce standard CRM objects and extends functionality through a specialized custom relational schema:

### Core Salesforce Standard Objects
* **Account:** Represents the client organizations and enterprise accounts.
* **Contact:** Stores individual customer profiles tied to specific Accounts.
* **Case:** The central engine tracking customer support requests, communication history, and resolution details.

### Custom Metadata & Objects
* **Support Category:** A lookup directory that determines how specific inbound complaints should be routed (e.g., Billing, Technical Bug, Account Access).
* **SLA Policy:** Defines resolution milestones and maximum turnaround thresholds based on customer tiers (e.g., Platinum, Gold, Standard).
* **AI Feedback:** Stores explicit logs submitted by support agents regarding the accuracy of automated classifications and suggested resolution steps.

---

## ⚙️ Backend Configurations & Automations
The system operates completely hands-free from triage to routing using advanced **Record-Triggered Flows**:

* **Automated Case Classification:** Extracts key phrases from the incoming subject/description to automatically populate the `Support Category`.
* **Dynamic Priority Assignment:** Evaluates the severity of the issue against the customer's Account status to assign realistic urgency flags (`High`, `Medium`, `Low`).
* **SLA Due Date Calculation:** Whenever a new Case is created, a flow queries the corresponding `SLA Policy` record and computes the precise target date/time for resolution, populating a custom countdown field.
* **Email-to-Case Triage:** Automatically converts raw external customer emails directly into organized Case records linked to pre-existing Contacts.

---

## 🎨 UI/UX Design & Security Model

### Agent Productivity Console
* **Optimized Record Pages:** Custom Lightning Record Pages built to separate customer historical details, case activity streams, and processing metrics.
* **Suggested Actions Component:** Context-specific actions dynamically displayed on the Case layout to guide agents through resolution paths based on the case category.
* **Dashboards & Reports:** Embedded analytics components monitoring active queue volumes, SLA breach rates, and common high-frequency categories.

### Role-Based Access Control (RBAC)
To ensure system security, clear boundaries are implemented via profiles and permission sets:
* **Support Agent:** Read/Write access to assigned Cases, ability to log interactions and submit `AI Feedback`.
* **Support Manager:** Full CRUD access over cases, supervisor rights to override routing queues, and exclusive access to performance tracking dashboards.
* **System Administrator:** Complete oversight to modify flow criteria, adjust `SLA Policy` structures, and deploy schema adjustments.
