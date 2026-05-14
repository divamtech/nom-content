---
title: "How a Mid-Market AP Team Cut Invoice Cycle Time by 85% Without Replacing Their ERP"
date: "2026-05-05"
author: "mansiikumarii"
tags: ["AI Agents", "Finance", "Accounts Payable", "Automation", "OCR"]
status: published
industry: "FINANCE"
description: "An agentic invoice processing system that ingests, extracts, three-way matches and routes invoices for human review — without touching the client's existing ERP."
stat1_value: "85%"
stat1_label: "FASTER CYCLE TIME"
stat2_value: "GPT-4.1"
stat2_label: "LLM USED"
stat3_value: "MEDIUM"
stat3_label: "TIME TO LAUNCH"
---

## Context

The client was a 600-person industrial manufacturer with a tightly-controlled, on-premise ERP installation that the finance team could not (and would not) replace. Their Accounts Payable function was healthy on paper but suffering in practice: six analysts processing more than 4,000 invoices a month, a CFO under board pressure to close the books faster, and a vendor base growing 18% year-over-year. Every conversation about ‘AI’ in finance had been dismissed because every previous proposal asked the team to migrate off the ERP they had just spent two years stabilising.

## The Problem

AP analysts were losing an average of six hours per person per day to manual data entry, three-way matching, and approval chasing. A 12% mismatch rate between invoices and purchase orders blocked downstream payment runs and forced finance to keep a manual exception queue.

Late-payment penalties were quietly draining roughly $15,000 per month off the bottom line, hidden inside vendor reconciliations. Quarterly audit prep was consuming three full weeks of finance bandwidth, including pulling source documents from four different storage systems. Earlier RPA attempts had broken whenever a vendor changed an invoice template, which happened constantly.

## Our Approach

We treated this as a workflow engineering problem first and an AI problem second. The first two weeks were spent instrumenting the existing AP process, mapping every exception type, and shadowing two analysts through a full month-end close. Only then did we design the agent. Our principle throughout: the ERP is sacred, the analysts are the customers, and the system has to fail safely. Nothing auto-posts without a human signing off above a configurable threshold.

## What We Engineered

- An agentic ingestion pipeline that pulls invoices from shared inboxes, scanned uploads, vendor portals, and EDI feeds, normalising all of them into a single queue.
- LLM-powered field extraction (vendor, line items, taxes, totals, GL hints) with measured field accuracy of 99.2% across the production dataset.
- Three-way matching against purchase orders and goods-receipt records, with a confidence score on every extracted field and structured rationale per match.
- Configurable human-in-the-loop routing: anything below a confidence threshold or above a value threshold goes to the analyst queue with the agent's reasoning attached.
- A side-car analytics layer that surfaces vendor-level trends — average dispute rate, payment timing, duplicate risk — to the controller and CFO weekly.

## Architecture and Workflow

1. **Interface:** Web dashboard for analysts and approvers, plus ERP-side webhooks; no replacement of the existing ERP UI.
2. **Models:** GPT-4.1 for primary extraction, GPT-4o-mini for validation re-checks and duplicate detection.
3. **Inputs:** PDFs, scanned TIFFs, EDI 810 documents, vendor portal exports, and email attachments.
4. **Stack:** FastAPI backend, pgvector for vendor-template recall, AWS Textract for pre-OCR, blue-green deployment on AWS ECS.
5. **Compliance and control:** SOX-ready audit log, role-based access, encryption at rest (SSE-KMS) and in transit, full version history on every extracted field.
6. **Time to launch:** Medium — six weeks, including two weeks of UAT with the existing AP team.

## Business Impact

- Invoice cycle time fell from 5.2 days to 0.8 days — an 85% reduction.
- Manual touches per invoice dropped from seven to 1.2.
- Late-payment penalties reduced by approximately $184,000 on an annualised basis.
- Audit prep time compressed from three weeks to four working days, with all source documents and reasoning traceable in one click.
- 60% of the analyst hours saved were redirected to vendor negotiation and cash-flow forecasting, work the team had wanted to own for years.

## Why It Worked

We did not ask the finance team to change the systems they trust. We engineered around them. The agent was treated as a colleague who handles the obvious, escalates the uncertain and leaves the auditable trail finance leaders actually need.

## Risks Mitigated

1. ERP integrity preserved; no data writes without explicit approval.
2. Audit defensibility — every field, every decision, every prompt logged and replayable.
3. Vendor-template drift — system generalises rather than relying on per-template parsers.

## Client Voice

> *“We expected an AI tool. We got an extension of the team. The agent does the work nobody on AP wanted to do and it does it in a way our auditors had no problem with.”*
>
> — Director of Finance Operations | Industrial Manufacturing
