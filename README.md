# 🛡️ SpendGuard AI
### Intelligent Expense Auditing & Document Processing Automation

**Turn unstructured receipts into structured, validated, audit-ready expense records.**

SpendGuard AI is an AI-powered expense processing and compliance automation project designed to streamline how businesses capture, validate, audit, and synchronize expense data.

Built around **n8n workflow orchestration, Gemini Vision AI, deterministic validation, and business integrations**, the system connects document ingestion with structured data extraction, policy checks, exception handling, and downstream ledger synchronization.

Rather than relying on AI extraction alone, SpendGuard AI combines AI-assisted document understanding with rule-based validation and review workflows to support a more controlled, traceable expense-processing pipeline.

> **Project Focus:** AI Automation · Expense Management · Compliance Workflows · Document Intelligence

---

## 🎯 The Problem

Businesses process receipts and invoices from multiple sources, often relying on repetitive manual work to transfer information into spreadsheets or financial systems.

This creates several operational challenges:

- **Manual data entry:** Employees spend time transferring receipt information into expense records.
- **Inconsistent data:** Different document formats can produce incomplete or inconsistently structured records.
- **Limited policy enforcement:** Expenses may require checks against company rules before approval.
- **Exception handling:** Missing information, unreadable receipts, and suspicious entries need additional review.
- **Fragmented workflows:** Expense records, notifications, and accounting data may be distributed across different tools.

These challenges can increase processing time, introduce avoidable errors, and make expense oversight more difficult.

---

## 💡 The Solution

SpendGuard AI introduces an automated workflow that processes expense documents through a series of controlled stages.

The pipeline is designed to:

1. **Capture** receipts and invoices through a web form.
2. **Normalize** uploaded images for downstream processing.
3. **Check document quality** before attempting extraction.
4. **Extract expense information** using Gemini Vision AI.
5. **Validate and normalize** the extracted data against a defined schema.
6. **Audit expenses** against configured business policies.
7. **Route exceptions** for human review when necessary.
8. **Synchronize approved records** with connected business tools.
9. **Notify relevant stakeholders** through configured communication channels.

The goal is to reduce repetitive administrative work while maintaining validation, review, and control throughout the expense-processing lifecycle.

---

## 🏗️ System Architecture

The workflow follows a staged processing model, separating document intake, AI extraction, deterministic validation, policy auditing, and downstream integrations.

```text
                  ┌──────────────────────┐
                  │   Receipt / Invoice  │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │    Web Form Ingest   │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │  Image Normalization │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │   Quality Control    │
                  │        Gate          │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │  Gemini Vision AI   │
                  │  Data Extraction    │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │ Schema Validation   │
                  │ & Normalization     │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │ Policy Compliance   │
                  │       Audit         │
                  └──────────┬───────────┘
                             │
                     ┌───────┴────────┐
                     │                │
                     ▼                ▼
              ┌────────────┐   ┌──────────────┐
              │  APPROVED  │   │    FLAGGED   │
              └─────┬──────┘   └──────┬───────┘
                    │                 │
                    ▼                 ▼
              ┌────────────┐   ┌──────────────┐
              │ Ledger Sync│   │ Human Review │
              └─────┬──────┘   │ / Escalation │
                    │           └──────────────┘
             ┌──────┼─────────┐
             │      │         │
             ▼      ▼         ▼
          Sheets   Slack     Gmail
```

**Architecture principle:** AI extracts information; deterministic rules validate it; policy checks determine routing; human review handles exceptions that should not be processed automatically.

---

## ✨ Core Capabilities

### 📥 1. Automated Document Ingestion
Provides an entry point for submitting receipts and invoices to the processing pipeline.

**Designed to support:**
- Web-based document submission.
- Receipt and invoice intake.
- A consistent entry point for downstream processing.

### 🖼️ 2. Image Normalization & Quality Control
Prepares submitted documents for processing and introduces an early quality checkpoint.

**Processing objectives:**
- Normalize images before extraction.
- Identify documents that do not meet configured quality requirements.
- Prevent unsuitable inputs from proceeding unchecked.

### 🤖 3. AI-Powered Data Extraction
Uses Gemini Vision AI to interpret receipt and invoice content and extract relevant expense information.

**Intended extraction fields may include:**
- Merchant or vendor name.
- Transaction date.
- Total amount.
- Currency.
- Tax information.
- Invoice or receipt reference.

The extracted fields should be defined by the project's output schema and validated before use.

### ✅ 4. Deterministic Data Validation
Introduces predictable validation rules after AI extraction.

**Validation objectives:**
- Check required fields.
- Enforce expected data types and formats.
- Normalize values into a consistent structure.
- Detect incomplete or malformed records.
- Route invalid records away from automatic synchronization.

### 🔍 5. Policy-Based Expense Auditing
Evaluates structured expense records against configurable business rules.

Potential audit rules include:
- Expense amount thresholds.
- Missing or invalid transaction dates.
- Required receipt information.
- Unsupported expense categories.
- Duplicate transaction indicators.

Actual audit rules depend on the policies configured in the implementation.

### 🚦 6. Exception Handling & Human Review
Separates approved records from flagged or incomplete submissions.

This design supports:
- Review of failed validation checks.
- Escalation of policy exceptions.
- Investigation of potentially duplicated records.
- Reduced reliance on unchecked AI output.

### 🔄 7. Business Tool Synchronization
Provides a downstream integration stage for approved expense records.

The proposed integration destinations are:

| Integration | Intended Role |
|---|---|
| **Google Sheets** | Structured expense records and ledger-style tracking |
| **Slack** | Operational notifications and exception alerts |
| **Gmail** | Email notifications and review communications |

Availability and behavior depend on the configured n8n nodes, credentials, and workflow connections.

---

## ⚙️ Technology Stack

| Technology | Role |
|---|---|
| **n8n** | Workflow orchestration and integration automation |
| **Gemini Vision AI** | Receipt and invoice content extraction |
| **HTTP APIs** | Communication with supported external services |
| **Schema Validation** | Structural and field-level data validation |
| **Business Rules** | Deterministic expense and compliance checks |
| **Google Sheets** | Proposed expense ledger integration |
| **Slack** | Proposed operational notification integration |
| **Gmail** | Proposed email notification integration |

---

## 🔐 Reliability, Validation & Control

Expense automation requires more than extracting text from documents. Financial records should pass explicit checks before being written to downstream systems.

SpendGuard AI is designed around several important controls.

| Control | Purpose |
|---|---|
| **Input Quality Checks** | Identify unsuitable documents before extraction |
| **Schema Validation** | Ensure extracted information follows the expected structure |
| **Deterministic Rules** | Apply predictable validation and policy checks |
| **Exception Routing** | Send problematic records for additional review |
| **Controlled Synchronization** | Restrict automatic ledger updates to eligible records |
| **Integration Error Handling** | Provide a basis for handling failed downstream operations |

**Important:** These are architectural goals. Their effectiveness depends on the actual workflow implementation, configuration, testing, and error-handling behavior.

---

## 🔄 End-to-End Processing Lifecycle

The system can be understood as a sequence of distinct processing stages.

**Stage 1 — Intake**  
A user submits a receipt or invoice.

**Stage 2 — Preparation**  
The document passes through image normalization and quality checks.

**Stage 3 — Extraction**  
Gemini Vision AI converts document content into structured expense data.

**Stage 4 — Validation**  
The extracted information is checked against the expected schema and deterministic validation rules.

**Stage 5 — Audit**  
The expense is evaluated against configured business policies.

**Stage 6 — Decision**  
The workflow routes the record to an approved or flagged path.

**Stage 7 — Synchronization**  
Eligible records proceed to configured ledger integrations.

**Stage 8 — Notification or Review**  
Relevant stakeholders can be notified, and exceptions can be directed to human review.

---

## 🚀 Setup & Configuration

The following is a general setup outline. Exact steps depend on the workflow files and integrations included in the repository.

### Prerequisites

- An accessible n8n instance.
- A Gemini API credential with access to the required model.
- Credentials for any integrations you intend to enable.
- The SpendGuard AI workflow configuration or export.

### 1. Obtain the Project

Clone the repository:

```bash
git clone <YOUR-REPOSITORY-URL>
```

Navigate into the project directory:

```bash
cd <YOUR-PROJECT-DIRECTORY>
```

Replace the placeholders with your actual repository URL and directory name.

### 2. Configure Credentials

Set up the required credentials in n8n for Gemini and any enabled integrations.

**Security recommendations:**
- Store credentials in the appropriate secret or credential manager.
- Never commit API keys, access tokens, or passwords.
- Use separate development and production credentials where practical.
- Grant integrations only the permissions they require.

### 3. Import the Workflow

If your repository contains an n8n workflow export:

1. Open your n8n instance.
2. Import the workflow.
3. Configure the required credentials.
4. Verify node connections and input/output mappings.
5. Review the validation and exception-routing logic.

### 4. Test Before Deployment

Begin with sample receipts and invoices that contain no sensitive personal or financial information.

Test:
- Valid documents.
- Unreadable or incomplete images.
- Missing required fields.
- Invalid amounts or dates.
- Expenses that violate configured policies.
- Duplicate transaction scenarios.
- Failed integration requests.

Confirm that each scenario follows the expected workflow path before enabling production processing.

---

## 🧪 Testing & Evaluation

A reliable expense pipeline should be evaluated on more than whether AI can extract text.

Recommended test categories include:

| Test Category | What to Verify |
|---|---|
| **Extraction Quality** | Correctness of extracted merchant, date, amount, and other required fields |
| **Schema Validation** | Rejection or routing of malformed records |
| **Policy Enforcement** | Correct handling of expenses that violate configured rules |
| **Exception Routing** | Flagged records reach the appropriate review path |
| **Integration Reliability** | Successful writes and appropriate handling of failed requests |
| **Duplicate Detection** | Repeated submissions are identified according to the configured rules |
| **Data Integrity** | Approved records retain their validated values during synchronization |

For stronger evaluation, measure extraction accuracy, validation failure rates, exception frequency, integration success rates, and average processing time using a representative test dataset.

---

## 🗺️ Roadmap

Potential future improvements include:

- [ ] Confidence-based routing for uncertain AI extractions.
- [ ] Duplicate detection using transaction attributes and document fingerprints.
- [ ] Configurable expense policies by department or expense category.
- [ ] Retry mechanisms for transient API and integration failures.
- [ ] Audit trails recording validation outcomes and routing decisions.
- [ ] Review queues for flagged expenses.
- [ ] Processing metrics and operational dashboards.
- [ ] Automated regression tests using sample documents.
- [ ] Role-based access controls for review and administration.
- [ ] Integration with an accounting platform or expense management system.

---

## ⚠️ Project Scope

SpendGuard AI focuses on AI-assisted document processing, expense validation, policy-based auditing, and workflow automation.

It should not be treated as a replacement for professional financial review, a complete accounting platform, or a guarantee of regulatory compliance.

AI extraction can produce incorrect or incomplete information. Validation, testing, access controls, auditability, and appropriate human review remain essential, particularly when processing financial records.

---

## 👨‍💻 About the Project

SpendGuard AI explores how AI and workflow automation can be combined to address a practical business problem: the time and effort required to transform unstructured expense documents into validated, usable records.

The project emphasizes the separation of AI extraction from deterministic validation, controlled decision-making, exception handling, and downstream integration.

**Core principle:** Automate repetitive work without removing the controls that make financial workflows dependable.

---

## 📄 License

Add a `LICENSE` file to the repository and update this section to reflect the license you choose.

---

<p align="center">
  <strong>SpendGuard AI</strong><br>
  Intelligent document processing. Controlled automation. Better expense oversight.
</p>
