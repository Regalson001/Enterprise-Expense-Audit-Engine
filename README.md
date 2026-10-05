# SpendGuard AI — Enterprise Expense Audit & Ingestion Engine

> AI-powered expense document ingestion, validation, compliance auditing, and automated ledger synchronization built with n8n, Gemini Vision AI, APIs, and business automation systems.

## Overview

**SpendGuard AI** is an enterprise-oriented automation pipeline that transforms unstructured receipts and invoices into structured, validated, and audit-ready expense records.

The system combines **n8n workflow orchestration, Gemini Vision AI, deterministic validation, policy-based auditing, and multi-channel integrations** to automate the expense-processing lifecycle from document ingestion to final synchronization.

Instead of simply extracting data with AI, SpendGuard AI introduces validation, compliance controls, exception handling, and downstream system synchronization to create a more reliable production-style automation architecture.

---

## Architecture

```text
Receipt / Invoice
       │
       ▼
┌─────────────────────┐
│   Web Form Ingest   │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│  Image Normalizer   │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Quality Control     │
│       Gate          │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Gemini Vision AI    │
│ Document Extraction │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Schema Validation   │
│ & Data Normalization│
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Policy Compliance   │
│       Audit         │
└──────────┬──────────┘
           │
      ┌────┴────┐
      ▼         ▼
   APPROVED   FLAGGED
      │         │
      ▼         ▼
┌──────────┐ ┌─────────────┐
│ Ledger   │ │ Human Review│
│ Sync     │ │ / Escalation│
└────┬─────┘ └─────────────┘
     │
 ┌───┼───────────┐
 ▼   ▼           ▼
Sheets Slack     Gmail
