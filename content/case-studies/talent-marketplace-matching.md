---
title: "How a Talent Marketplace Matched 50,000 Candidates to Live Roles in Real Time"
date: "2026-05-08"
author: "mansiikumarii"
tags: ["AI Agents", "HR Tech", "Talent Matching", "Recruiting", "Vector Search"]
status: published
industry: "HR TECH"
description: "A retrieve-rerank-explain pipeline that turned a keyword-driven talent marketplace into a live, contextual matching engine recruiters and candidates both trust."
stat1_value: "3.2x"
stat1_label: "INTERVIEW CONVERSION"
stat2_value: "GPT-4o"
stat2_label: "LLM USED"
stat3_value: "MEDIUM"
stat3_label: "TIME TO LAUNCH"
---

## Context

The client ran a tech-focused talent marketplace with two real assets: a deep candidate pool and a live job board refreshed by hiring partners every few minutes. The matching layer in between, however, was keyword-driven and showing its age. Recruiters were drowning in noisy shortlists, candidates were ghosting after slow first responses, and the leadership team had a clear thesis: the business was a search problem dressed up as an HR problem.

## The Problem

- Recruiters were manually reviewing 200+ resumes per open role with no reliable ranking signal.
- 67% of candidates ghosted after their first week because of slow, generic outreach.
- Keyword search missed contextual fit — a ‘platform engineer’ and a ‘devops engineer’ might be the same person, and the system did not know it.
- There was no way to explain to either side why a match surfaced, which hurt trust in the platform itself.
- Hiring partners were starting to question the platform's value vs. doing direct sourcing on LinkedIn.

## Our Approach

We built the system as a classic three-stage retrieval pipeline — retrieve, rerank, explain — because search problems benefit from boring, well-understood architecture. Hybrid retrieval handles recall, the reranker handles precision, and the rationale layer handles trust. We then wired in a feedback loop so that every recruiter ‘yes’ or ‘no’ trains the next set of recommendations.

## What We Engineered

- Resume parsing into structured skills, experience, seniority and domain signals that normalised across industries and titles.
- Hybrid retrieval (pgvector plus BM25) over the live job pool, refreshed every 15 minutes.
- A cross-encoder reranker for top-K refinement that improves ordering measurably above pure vector recall.
- A rationale layer that surfaces the why behind each match — visible to the recruiter and the candidate alike.
- Auto-generated outreach copy tuned to each candidate's background and the role they are being matched to.

## Architecture and Workflow

1. **Interface:** Recruiter dashboard plus a candidate self-serve portal.
2. **Models:** GPT-4o for resume extraction; bge-reranker-large for ranking refinement.
3. **Inputs:** Resumes (PDF, DOCX, LinkedIn imports) and the live job pool from the partner network.
4. **Stack:** pgvector with HNSW indexing, FastAPI backend, Redis cache for hot queries, Next.js front-end.
5. **Outputs:** Ranked candidate lists with rationale, suggested outreach copy, and a feedback capture loop on every recruiter action.
6. **Time to launch:** Medium — five weeks including calibration on three months of historical data.

## Business Impact

- Interview conversion rate improved by 3.2x.
- Time-to-shortlist fell from four days to twelve minutes.
- Recruiter NPS increased by 38 points within the first quarter.
- Candidate response rate improved by 44%, driven by tighter targeting and personalised outreach.
- Hiring partner churn fell to its lowest level in two years.

## Why It Worked

We treated hiring as the search problem it actually is. Retrieval, ranking, and explainability are well-understood engineering disciplines — we just applied them with the rigour the domain deserves.

## Risks Mitigated

- **Bias** — explicit fairness checks on shortlist composition before delivery.
- **Cold start** — hybrid retrieval performs well even on thin candidate profiles.
- **Trust** — every match is explainable to both sides of the marketplace.

## Client Voice

> *“Recruiters stopped fighting the platform and started trusting it. That single change — trust — is what moved every other number.”*
>
> — Head of Product | Tech Talent Marketplace
