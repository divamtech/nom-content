---
title: "Cutting NDA Turnaround From Six Days to Six Hours, With Counsel Still in Charge"
date: "2026-05-12"
author: "mansiikumarii"
tags: ["AI Agents", "Legal", "Contract Operations", "Compliance", "Document Review"]
status: published
industry: "LEGAL"
description: "A playbook-aware contract review agent that drafts the obvious and surfaces fallback positions — counsel always reviews, every suggestion is auditable."
stat1_value: "92%"
stat1_label: "TURNAROUND REDUCTION"
stat2_value: "GPT-4o + CLAUDE"
stat2_label: "LLMS USED"
stat3_value: "MEDIUM"
stat3_label: "TIME TO LAUNCH"
---

## Context

The client was the in-house legal function at a 1,200-person fintech, staffed by six attorneys and a general counsel who was tired of seeing routine NDAs and standard MSAs choke a queue meant for high-stakes work. The business teams were losing live deals to slow legal turnaround, and there was no central memory of which fallback positions had been negotiated successfully before. Every attorney was, in effect, redoing work the team had already done.

## The Problem

- The legal queue was choked by routine NDAs and standard MSAs that did not require senior judgement.
- Six attorneys were producing inconsistent redlines on the same templates, often disagreeing with one another.
- Business teams were losing live deals to slow legal turnaround — a problem visible in the CRM.
- There was no central memory of which fallback positions had been negotiated successfully before.
- Earlier AI tools had been blocked at the procurement review for failing audit and compliance checks.

## Our Approach

We did not build an AI lawyer. We built an agent that drafts the obvious so counsel can spend time on what matters. The system was designed around two non-negotiable principles: counsel always reviews before sending and every suggestion the agent makes can be traced to the playbook clause and historical precedent that informed it.

## What We Engineered

- Automated first-pass redline against the company's own playbook, with each suggestion tagged to its source clause.
- Suggested fallback positions with the negotiation rationale behind each one, drawn from historical agreements.
- A risk heatmap flagging unusual or off-playbook clauses for human attention.
- Counsel always reviews before send — nothing is auto-issued, ever.
- A searchable institutional memory of every clause negotiated, settled on, or rejected over the previous three years.

## Architecture and Workflow

1. **Interface:** Word add-in for in-document use plus a web review portal for triage.
2. **Models:** GPT-4o for drafting; Claude for cross-validation on high-stakes clauses (indemnity, IP, liability caps).
3. **Inputs:** 800+ historical contracts, the internal playbook, fallback clause library.
4. **Stack:** RAG with clause-level retrieval, version-controlled outputs, immutable audit log on every action.
5. **Outputs:** Redlined Word document, risk summary, and suggested edits with source citations.
6. **Time to launch:** Medium — six weeks including the compliance review.

## Business Impact

- NDA turnaround fell from six days to six hours.
- Contract throughput per attorney tripled.
- Deal velocity (measured at the GTM funnel) improved by 21%.
- Counsel time reallocated to negotiation and high-risk work increased by 60%.
- The institutional memory built during the engagement became the team's most-referenced internal resource.

## Why It Worked

We engineered around lawyers, not over them. The agent drafts; counsel decides. That is the only model regulated industries trust and it is the only one we ship into legal.

## Risks Mitigated

- **Liability** — nothing leaves the system without counsel review.
- **Audit** — every suggestion, edit, and approval is logged and replayable.
- **Knowledge loss** — institutional memory captured and searchable as attorneys join and leave.

## Client Voice

> *“We stopped being the bottleneck. The work that needs judgement still gets it. The work that does not, does not waste anyone's time.”*
>
> — General Counsel | Fintech
