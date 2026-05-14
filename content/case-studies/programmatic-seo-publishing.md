---
title: "Publishing 1,200 SEO Pages a Week Without a Content Team in Sight"
date: "2026-05-09"
author: "mansiikumarii"
tags: ["AI Agents", "Marketing", "Programmatic SEO", "Content Generation", "B2B SaaS"]
status: published
industry: "MARKETING"
description: "A programmatic SEO publishing pipeline with editorial gates that scaled output 40x while protecting domain authority and brand voice."
stat1_value: "+412%"
stat1_label: "ORGANIC TRAFFIC (6 MONTHS)"
stat2_value: "GPT-4o + CLAUDE"
stat2_label: "LLMS USED"
stat3_value: "EASY"
stat3_label: "TIME TO LAUNCH"
---

## Context

The client was a recently-funded B2B MarTech SaaS with 8,000+ keyword opportunities sitting in a research backlog and a four-person content team capping out at 30 pages a week. The leadership team had already burned themselves on a previous AI content vendor that produced thin, indistinguishable copy and triggered a de-indexing scare. They wanted leverage, but not at the cost of the domain authority they had built carefully over two years.

## The Problem

- The content team was bottlenecked at roughly 30 pages per week with no clear path to scale.
- More than 8,000 keyword opportunities were sitting untouched in the research backlog.
- Manual SEO operations were eating roughly 40% of the marketing budget on low-leverage work.
- An earlier AI experiment had produced thin content that hurt domain authority and triggered partial deindexing.
- The CMO had board-level pressure to show organic growth without expanding headcount.

## Our Approach

We built the system around editorial control, not volume. Every page passes through a brand-voice prompt, an editorial guardrail pass, and a banned-phrase filter before it reaches a Slack approval queue. The content team's job changed from writing first drafts to running the queue — which is the work they wanted to do all along.

## What We Engineered

- CSV-driven generation: keyword pairs in, full article plus meta tags, schema markup, and headings out.
- Brand-voice fine-tuned prompts with editorial guardrails and a banned-phrase list specific to the client's tone of voice.
- Automatic internal linking based on topical clusters and the existing site graph.
- One-click publishing into WordPress, Webflow, and Sanity, with rollback if a page underperforms after 30 days.
- An analytics layer that tracks per-page performance and feeds underperformers back into the editorial review loop.

## Architecture and Workflow

1. **Interface:** Internal admin tool plus a Slack approval queue.
2. **Models:** GPT-4o for drafting and Claude for the editorial pass — two voices catch more than one.
3. **Inputs:** Keyword research CSVs, brand guidelines, competitor content, internal product documentation.
4. **Stack:** Next.js, FastAPI, pgvector for content recall, scheduled CI publishing pipeline.
5. **Outputs:** Publish-ready HTML and JSON-LD schema, with tracking links auto-attached.
6. **Time to launch:** Easy — three weeks from kickoff.

## Business Impact

- Organic traffic increased by 412% over six months.
- Cost per published page fell from $48 to $7 — fully loaded.
- The content team was reallocated to brand strategy and thought leadership, work the CEO had wanted to invest in for over a year.
- Domain authority was preserved with zero deindexing events in the first nine months post-launch.
- Marketing-sourced pipeline grew by 31% in the same window.

## Why It Worked

We did not build a content firehose. We engineered a publishing pipeline with editorial gates that the brand team controls. Volume came as a side effect, not the objective.

## Risks Mitigated

- **Domain authority** — editorial gates and quality monitoring on every page.
- **Brand drift** — voice guardrails enforced at generation time, not at review time.
- **Search engine penalty** — schema markup, original research blocks, and human approval per page.

## Client Voice

> *“Our content team finally does the work they joined for. The pipeline handles the volume; they handle the brand. That is the right division of labour.”*
>
> — Head of Marketing | B2B MarTech SaaS
