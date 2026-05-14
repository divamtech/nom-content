---
title: "Turning a Decade of Scanned Bills Into a Live, Queryable Dataset Across Twelve Countries"
date: "2026-05-07"
author: "mansiikumarii"
tags: ["AI Agents", "Fintech", "Document Extraction", "Cross-Border Payments", "Multilingual"]
status: published
industry: "FINTECH"
description: "A universal LLM-based invoice extractor that handles 11 languages and 30+ vendor formats with strict schema validation — replacing a graveyard of per-vendor parsers."
stat1_value: "99.4%"
stat1_label: "FIELD-LEVEL ACCURACY"
stat2_value: "GPT-4o"
stat2_label: "LLM USED"
stat3_value: "EASY-MEDIUM"
stat3_label: "TIME TO LAUNCH"
---

## Context

The client operated a cross-border B2B payments platform processing roughly $1.4B in annual transaction volume across twelve countries. Every new market arrived with its own invoice formats, tax regimes and — in three cases — new alphabets. Their engineering team had spent eighteen months building bespoke parsers per vendor and per market and was visibly losing the race. The product roadmap was being held hostage by parsing work the team did not want to be doing.

## The Problem

- Customers were uploading invoices in 11 languages and more than 30 distinct vendor formats.
- A 22% rejection rate at validation was blocking customer payments and triggering high-volume support escalations.
- Engineering was burning roughly 40 hours per week on vendor-specific parsers, unrecoverable time spent on work that delivered no compounding value.
- There was no reliable way to extract line items from low-quality scans or photo uploads taken on a phone.
- Each new market required up to three weeks of parser engineering before customers could be onboarded.

## Our Approach

We replaced the parser-per-vendor model with a single extraction system designed to generalise. The defining constraint was schema discipline: regardless of input language or layout, the output had to be a strict, validated JSON object that downstream services could trust without an additional cleaning step. We built the evaluation harness before we built the extractor.

## What We Engineered

- A universal LLM-based extractor that handles unstructured invoices in any of the supported languages without per-vendor templates.
- Auto-detection of language, currency, and tax regime before extraction begins, so the system applies the right validation rules from the first pass.
- Schema-validated JSON output with confidence scores on every field, ready for ERP and accounting integrations.
- A human-review queue for low-confidence cases, with structured feedback that improves the next extraction.
- Side-car evaluation harness that runs on every model or prompt change — no regression escapes to production.

## Architecture and Workflow

1. **Interface:** REST API for partner integrations plus a drag-and-drop upload widget for end customers.
2. **Models:** GPT-4o for extraction; a custom validator handles regime-specific tax math.
3. **Inputs:** PDF, JPG, PNG, and HEIC files in English, Hindi, Spanish, Arabic, Mandarin, plus six additional languages.
4. **Stack:** FastAPI, AWS Textract pre-pass for image normalisation, pgvector for vendor-template recall, Postgres for the canonical record store.
5. **Compliance:** GDPR-ready data retention, SSE-KMS at rest, TLS in transit, region-specific data residency where required.
6. **Time to launch:** Easy-to-Medium — four weeks from kickoff to first production traffic.

## Business Impact

- Field-level accuracy moved from 81% to 99.4% across the production dataset.
- Invoice rejection rate dropped from 22% to 1.6%.
- Engineering reclaimed more than 40 hours per week, which the leadership team redirected to product work that actually compounds.
- Time to support a new market fell from approximately three weeks to under 48 hours.
- Customer support tickets related to invoice rejection fell by 81% in the first quarter.

## Why It Worked

Scaling globally should not mean scaling parsers. We engineered an extraction system that generalises out of the box, with the evaluation discipline to keep it honest as new markets and new edge cases land.

## Risks Mitigated

- **Schema drift** — strict JSON validation enforced on every output.
- **Quality regression** — automated evaluation harness on every model change.
- **Data residency** — region-specific storage and processing where the contract demanded it.

## Client Voice

> *“We stopped maintaining a parser graveyard. The system now expands as fast as our commercial team does, which is the first time in years that has been true.”*
>
> — VP Engineering | Cross-border Payments Platform
