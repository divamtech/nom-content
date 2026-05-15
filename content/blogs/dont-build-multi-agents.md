---
title: "Don't Build Multi-Agents: A Practical Case for Single-Threaded Context Engineering"
excerpt: "Multi-agent architectures look elegant on a whiteboard and break in production. The discipline that separates reliable agents from fragile ones is not architectural complexity. It is context engineering."
date: "2026-05-15"
author: "Newton on Mars"
tags: ["Engineering", "AI Agents"]
status: "published"
---

Multi-agent architectures look elegant on a whiteboard and break in production. The discipline that separates reliable agents from fragile ones is not architectural complexity. It is context engineering. After dozens of production deployments, the evidence is consistent: a single-threaded agent with disciplined context management outperforms an orchestra of subagents on almost every real-world task.

## Two Principles That Almost Always Hold

Two principles cover most agent design questions. Violate either one and reliability collapses regardless of how clever the architecture looks.

* **Share the full trace**, not just individual messages.
* **Actions carry implicit decisions**, and conflicting decisions lead to bad outcomes.

These two rules are so foundational that any architecture that violates them should be ruled out by default. The remainder of this article explains why.

## Why Multi-Agent Patterns Look Tempting

The shape is familiar. Break the work into parts. Spin up subagents to work in parallel. Combine the results at the end. It feels like good engineering. It is the same map-reduce instinct that made distributed computing work.

The instinct fails for agents because language tasks carry meaning that resists clean decomposition. Consider a simple example: build a Flappy Bird clone. Subtask one is the moving background with green pipes and hit boxes. Subtask two is a bird that moves up and down. Subagent one builds a Super Mario Bros background. Subagent two builds a bird that does not look like a game asset. The orchestrating agent is left trying to combine two miscommunications into a coherent product. Most real-world tasks have many more layers of nuance and many more places for subagents to drift.

## Principle 1: Share the Trace, Not the Message

Sending a subagent only the original task description is not enough. In a real system, the conversation is multi-turn, the agent has made tool calls, and any number of details could affect interpretation. The subagent without that history is solving a different problem. Share the full trace or accept that subagent outputs will not compose.

## Principle 2: Actions Carry Implicit Decisions

Even when each subagent has the original context, parallel subagents cannot see what the others are doing. Their work ends up inconsistent because they operate on conflicting unstated assumptions. Two designers working on the same screen without ever talking will produce two screens that almost, but never quite - fit together.

## Architectures That Comply

### Single-Threaded Linear Agent (Default Choice)
The simplest way to satisfy both principles. Context is continuous. Every action sees the trace of every other action. This pattern carries the vast majority of production agents further than people expect. The single hard limit is the context window for very long tasks.

### Context-Compression Agent (For Truly Long-Duration Work)
Introduce a dedicated model whose only job is to compress history into the key facts, events and decisions. Done well, this preserves the linear-agent property while fitting inside the window. Done poorly, it reintroduces the very problem the compression was meant to solve. This is hard to get right and worth investing in only when the task length truly demands it.

## Real-World Examples

### Claude Code's Subagent Pattern
As of mid-2025, Claude Code spawns subtasks but never runs work in parallel with those subtask agents. The subtask agent is usually only asked to answer a question, not to write code, because it lacks the main agent's context to do anything more. Running parallel subagents would produce conflicting responses. The designers of Claude Code chose simplicity on purpose.

### Edit-Apply Models
In 2024 it was common to use a small model to apply edits, rewriting an entire file given a markdown explanation of changes rather than have a large model output a properly formatted diff. These systems were faulty: the small model would misinterpret the instructions because of slight ambiguities. Today, edit decisions and edit applications are typically done by a single model in one action. The pattern is the same lesson at a smaller scale.

## What About Multi-Agent Collaboration?

True parallelism would require decision-making agents to talk to each other more than the way two engineers resolve a merge conflict. Today's models cannot sustain that style of long-context, proactive discourse with the reliability of a single agent. Humans communicate efficiently because of nontrivial intelligence about which information matters. Agents do not yet have that judgement. Until they do, multi-agent collaboration produces fragile systems. Decision-making becomes too dispersed and context cannot be shared thoroughly enough across boundaries.

## Applying the Principles

Ensure every action your agent takes is informed by the context of all relevant decisions made by other parts of the system. Ideally, every action would see everything else. When the context window or practical trade-offs make that impossible, decide explicitly how much complexity you are willing to take on for the level of reliability you are targeting. The default should be the simpler architecture, not the more elegant one.

## Toward a More General Theory

Context engineering will eventually be a standard discipline alongside prompt design and evaluation. The principles above are early outlines, not the final form. The field is moving quickly. Flexibility and humility are required. But the lesson from two years of production deployments is consistent: keep your agents single-threaded unless you have a compelling reason not to. Most teams do not.
