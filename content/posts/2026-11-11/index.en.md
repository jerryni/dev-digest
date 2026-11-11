---
title: "November 11 · Today's 9 Dev Picks"
date: 2026-11-11T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "ai", "agents", "cloud"]
categories: ["daily"]
summary: "Model releases are only half the story; today's picks focus on execution boundaries and operational handoff."
---

# November 11 · Today's 9 Dev Picks

## Today at a glance

Today is less about a single model benchmark than about the systems that make agentic work usable: controlled browser access, durable handoff, sandboxing, and production-safe change management. Faster implementation is valuable only when verification keeps pace.

## Picks

### 1. [Claude Fable 5.2 and Claude Mythos 5.2](https://www.anthropic.com/claude-fable-and-mythos-5-2)
`Anthropic News · Models`

Anthropic introduced Fable 5.2 and Mythos 5.2 as models for demanding technical work across coding, finance, and science. Treat a model switch as a dependency upgrade, not a checkbox: tool calls, latency, and failure behavior can all move. A fixed evaluation suite is the cheapest way to make that change visible.

### 2. [AlphaProof Code](https://deepmind.google/blog/introducing-alphaproof-code/)
`Hacker News · AI research`

DeepMind's AlphaProof Code is drawing attention for connecting formal mathematical proof work with code capability. It is not a drop-in application-development tool, but it sharpens a useful distinction: passing tests is not the same as establishing correctness. Teams in compilers, finance, or security-critical code should watch whether these techniques become operationally approachable.

### 3. [agent-browser on GitHub Trending](https://github.com/vercel-labs/agent-browser)
`GitHub Trending · Agent tooling`

agent-browser exposes browser automation through a CLI intended for AI agents. That is practical precisely because it touches real sessions, downloads, and navigation—also the parts that expand an agent's threat model. Start with isolated accounts, domain allowlists, and replayable audit logs.

### 4. [llm-gemini 0.36](https://simonwillison.net/2026/Nov/10/llm-gemini/)
`Simon Willison · Developer tools`

Simon Willison updated his Gemini plugin for the LLM command-line ecosystem. Small adapters matter because they turn a model announcement into commands, outputs, and logs that can be compared later. Pin the exact model and parameters in team scripts; a generic model label hides meaningful behavior changes.

### 5. [Will AI-written code eventually blow up?](https://www.v2ex.com/t/1255786)
`V2EX · Developer community`

This Chinese developer discussion keeps returning to the same operational question: can design, review, and acceptance still keep up with generated code? One useful practice is to attach a handoff note to every agent change—what changed, why, how it was checked, and what remains uncertain. Without that, acceleration simply relocates risk to QA and future maintainers.

### 6. [Recent Claude Code tips](https://zenn.dev/oikon/articles/claude-code-recipe)
`Zenn · AI development`

This popular Zenn post collects practical Claude Code techniques. The durable takeaway is not a particular prompt, but making environments and conventions reusable across people. Agents become team tools when context, permissions, and acceptance criteria are reproducible.

### 7. [A PostgreSQL migration blocked by a lock while only SELECT was running](https://zenn.dev/naokisuzuki27/articles/cb1a5ac0e23763)
`Zenn · Databases`

The incident is a good reminder that a migration's risk cannot be inferred from whether an application query is read-only. Transaction duration, lock compatibility, and deployment timing matter just as much. Timeouts, observability, and a rollback path should be prepared before the schema change is queued.

### 8. [.NET 11 is now generally available](https://www.publickey1.jp/blog/26/net_11cjitaot.html)
`Publickey · .NET`

Publickey reports that .NET 11 brings C# 15 union types plus JIT, AOT, and command-line tooling improvements. For established .NET estates, migration decisions will hinge on build time, image size, and native deployment behavior more than on new syntax. Pilot an isolated service and measure before moving a platform baseline.

### 9. [Google contributes Agent Substrate and gVisor-related work to CNCF](https://www.publickey1.jp/blog/26/googlekubernetes10aiagent_sustrategvisorcncf.html)
`Publickey · Kubernetes`

Google is advancing Agent Substrate and gVisor-related work for running agents more efficiently on Kubernetes, with a contribution to CNCF. Agent workloads spend substantial time on tools and network I/O, making isolation, scheduling density, and cost attribution architectural concerns. Platform teams should track the operational prerequisites once the projects settle into open governance.

## Editor's note

Read agent-browser next to the PostgreSQL lock post: one defines the boundary of what an agent may do, the other exposes the boundary conditions of a real production system. We published nine rather than padding to ten—other V2EX technical posts were promotional, and Anthropic had only one verifiable recent technical release.
