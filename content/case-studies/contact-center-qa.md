---
title: "Auditing 100% of Support Calls Instead of 2%, in Minutes Rather Than Months"
date: "2026-05-14"
author: "mansiikumarii"
tags: ["AI Agents", "Customer Experience", "Contact Center", "Quality Assurance", "Speech-to-Text"]
status: published
industry: "CUSTOMER EXPERIENCE"
description: "An always-on contact-centre QA agent that transcribes, scores and risk-flags every call across a 120-agent floor — moving the QA team from sampling to curation."
stat1_value: "100%"
stat1_label: "CALL COVERAGE"
stat2_value: "GPT-4o + WHISPER"
stat2_label: "MODELS USED"
stat3_value: "MEDIUM"
stat3_label: "TIME TO LAUNCH"
---

## Context

The client ran a SaaS support organisation with 120 agents handling roughly 70,000 calls a month. The QA team — with four analysts — was reviewing 2% of calls and quietly missing every systemic issue inside the other 98%. Coaching feedback to agents was running three weeks behind the conversations it described, which meant it had effectively no impact on behaviour. Compliance violations were only being caught after a customer escalation made them impossible to ignore.

## The Problem

- The QA team was manually reviewing only 2% of calls and missing the systemic issues hiding in the remaining 98%.
- Coaching feedback to agents was arriving three or more weeks after the call, by which point the lesson had no real impact on behaviour.
- Compliance violations were only surfacing after customer escalation — with the regulatory and reputational risk that implies.
- There was no reliable signal to spot recurring product issues from support call volume.
- Onboarding new agents was slow because there were no good real-call examples to learn from.

## Our Approach

We did not replace the QA team. We made them omniscient. Every call gets transcribed, scored against a configurable rubric, and routed for human review only when something interesting happens. The QA team's role shifted from sampling to curating — which is where their judgement actually adds value.

## What We Engineered

- Auto-transcription and structured scoring of every call, every day, across the entire 120-agent floor.
- A custom rubric per program (sales, support, retention, compliance), configurable without engineering involvement.
- Auto-flagging of compliance, sentiment, and escalation risks with confidence scores.
- A weekly coaching summary auto-delivered to each team lead, with example clips embedded.
- A monthly product-feedback digest sent to the engineering team, surfacing the issues customers were calling about.

## Architecture and Workflow

1. **Interface:** Web QA dashboard for analysts plus an agent self-review portal so reps see their own scoring rationale.
2. **Models:** GPT-4o for analysis and scoring; Whisper for transcription.
3. **Inputs:** Call recordings (mp3, wav), CRM context, scorecard rubric, agent metadata.
4. **Stack:** AWS S3, FastAPI, async queue for high-volume processing, Next.js dashboard, dedicated PII redaction layer.
5. **Outputs:** Per-call scorecard, risk flags, weekly team brief, monthly product-feedback digest.
6. **Time to launch:** Medium — five weeks from kickoff.

## Business Impact

- Call coverage moved from 2% to 100%.
- QA throughput per analyst increased by 14x.
- Compliance violations caught early increased by 91%.
- Agent ramp time fell by 27%, helped by curated real-call examples.
- The product-feedback loop from support to engineering shortened from monthly to weekly, and three high-impact fixes shipped in the first quarter as a direct result.

## Why It Worked

The best QA team in the world can only watch 2% of calls. We engineered their coverage of the other 98% without asking anyone to work harder — and we moved the team from sampling to curation, which is the work that actually builds a better support floor.

## Risks Mitigated

- **Compliance exposure** — 100% coverage and early flagging.
- **PII leakage** — redaction layer applied at transcription time.
- **Analyst burnout** — the team curates instead of reviewing in volume.

## Client Voice

> *“Our QA team finally does the strategic work they were hired for. The volume problem solved itself the moment the agent went live.”*
>
> — VP Customer Experience | SaaS Support Organisation
