---
title: "Giving Clinical Investigators Their Time Back, One Protocol at a Time"
date: "2026-05-13"
author: "mansiikumarii"
tags: ["AI Agents", "Healthcare", "Clinical Research", "HIPAA", "RAG"]
status: published
industry: "HEALTHCARE"
description: "A HIPAA-compliant protocol summarisation and Q&A agent — every answer cited, every retrieval logged, deployed inside the client's own VPC."
stat1_value: "78%"
stat1_label: "PROTOCOL READ-TIME REDUCTION"
stat2_value: "GPT-4o (AZURE)"
stat2_label: "LLM USED"
stat3_value: "MEDIUM"
stat3_label: "TIME TO LAUNCH"
---

## Context

The client was a multi-site clinical research organisation running fourteen active studies, governed by HIPAA, and supported by a small clinical operations team. Every new protocol — typically an 80-page PDF — was eating eight or more hours of investigator time before any patient could be enrolled. Site coordinators were answering the same handful of protocol questions every week. Earlier AI tools had been blocked at procurement for failing the security review.

## The Problem

- Investigators were spending eight or more hours digesting each new protocol document.
- Critical inclusion and exclusion criteria were buried inside 80-page PDFs.
- Site coordinators were answering the same protocol questions repeatedly across weeks.
- Earlier AI tools had been blocked at procurement for failing the security review.
- Multi-language site teams had no consistent way to interpret the same protocol.

## Our Approach

We led with compliance, not capability. Before the first model call, we mapped the data flow, picked a deployment model the client's compliance team had already approved (Azure OpenAI under a BAA, inside the client's own VPC), and signed off on the audit logging approach. Only then did we build the agent. The result passed compliance review on the first attempt.

## What We Engineered

- A structured one-page summary per protocol — objectives, criteria, schedule, endpoints — produced from the source PDF.
- A Q&A agent grounded in the protocol PDF, with citation back to the page and line for every answer.
- A translation pass for multi-site, multi-language clinical teams.
- HIPAA-compliant deployment inside the client's own AWS VPC, with full audit logging on every retrieval and answer.
- A site brief generator that produces downloadable summaries tailored to each location's role in the study.

## Architecture and Workflow

1. **Interface:** Web reader for investigators plus a clinician chat for ad-hoc questions.
2. **Models:** GPT-4o deployed via Azure OpenAI under a HIPAA Business Associate Agreement.
3. **Inputs:** Clinical protocol PDFs and site-specific addenda.
4. **Stack:** Private VPC deployment, encryption at rest and in transit, full audit logging on every retrieval and answer.
5. **Outputs:** Structured summary, cited Q&A, downloadable site briefs.
6. **Time to launch:** Medium — seven weeks including the security and compliance review.

## Business Impact

- Protocol read time fell from approximately eight hours to 1.7 hours — a 78% reduction.
- Site activation time decreased by 34%.
- Investigator NPS on protocol clarity improved by 44 points.
- The compliance review passed on the first attempt, with a full audit trail.
- Site coordinator workload around routine protocol questions dropped by approximately 70%.

## Why It Worked

In healthcare, ‘trust the AI’ is not a strategy. We engineered an agent that cites, logs, and proves every answer, in a deployment model the compliance team approved before the first line of code was written.

## Risks Mitigated

- **PHI exposure** — private VPC deployment, no data leaves the client's environment.
- **Hallucination** — every answer cited to page and line.
- **Compliance failure** — deployment model and audit logging approved by the security team before build.

## Client Voice

> *“It is the first AI system that has cleared our compliance review on the first round, and the first that our investigators trust enough to actually use.”*
>
> — Director of Clinical Operations | Clinical Research Organisation
