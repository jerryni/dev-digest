---
title: "June 25 · Today's 10 Dev Picks"
date: 2026-06-25T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "ai", "agents", "cloudflare", "github", "ruby", "aws", "codex"]
categories: ["daily"]
summary: "Today is about the infrastructure around AI work: computer use, OAuth, PR spam controls, Mac containers, browser compatibility data, and isolated serverless execution."
---

## Today at a glance

The interesting work today is happening around the model, not just inside it. Gemini gets computer use, Cloudflare opens self-managed OAuth, Apple has a serious Mac container tool, and AWS is putting MicroVM-style execution into Lambda. The throughline: AI agents need safer ways to touch real systems.

---

### 1. Gemini 3.5 Flash gets computer use — `[Google · Hacker News]`
<https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-computer-use-gemini-3-5-flash/>

Google introduced a built-in computer use tool for Gemini 3.5 Flash. That matters for workflows where the interface is the integration surface: admin consoles, legacy enterprise apps, QA tools, and browser-based operations. The hard part will be permissioning, logging, and stopping conditions; a model that can click things needs guardrails that are more concrete than policy text.

### 2. Cloudflare opens Self-Managed OAuth to all developers — `[Cloudflare · Hacker News]`
<https://blog.cloudflare.com/oauth-for-all/>

Cloudflare made Self-Managed OAuth available to all developers and described the zero-downtime migration behind its core OAuth engine. OAuth is unglamorous infrastructure, but it is what turns isolated apps into an ecosystem. For Cloudflare-based tools, this should make third-party app authorization and enterprise integrations easier to build and govern.

### 3. RubyLLM gives Ruby a unified AI provider layer — `[Hacker News]`
<https://rubyllm.com/>

RubyLLM is a Ruby framework for working across major AI providers. The AI tooling conversation is heavily Python and TypeScript, but there are still many Rails systems where the business logic already lives. A clean Ruby-native abstraction can help those teams add model calls, streaming, and provider switching without moving core workflows out of their stack.

### 4. PR spam now looks like early-2000s email spam — `[Hacker News]`
<https://www.greptile.com/blog/prs-on-openclaw>

Greptile compares today's low-effort AI-generated pull requests to early email spam. The analogy works: creating submissions has become cheap, while review attention remains scarce. Together with GitHub's new PR limits, this points toward a new maintainer playbook: contribution queues, quality gates, bot fingerprints, and automatic closure rules.

### 5. apple/container is a serious Mac-native container signal — `[GitHub Trending]`
<https://github.com/apple/container>

Apple's `container` creates and runs Linux containers on macOS using lightweight virtual machines, written in Swift and optimized for Apple silicon. Local container experience remains one of the biggest productivity variables for Mac developers. This project is worth tracking alongside Docker Desktop, Colima, and OrbStack because it may change what the default Mac container stack looks like.

### 6. browser-compat-db turns MDN compatibility data into SQLite — `[Simon Willison]`
<https://simonwillison.net/2026/Jun/24/browser-compat-db/#atom-everything>

Simon Willison published `browser-compat-db`, a repo that converts MDN's browser compatibility data into SQLite. It is a small but useful pattern: take a trusted structured source, make it queryable locally, then let scripts and agents use it reliably. Front-end teams could use this style for compatibility checks, documentation assistants, and CI-time policy checks.

### 7. Rebuilding a company workflow with AI after years away from coding — `[V2EX]`
<https://www.v2ex.com/t/1222667>

A V2EX post describes someone returning from product and operations work to rebuild company workflows with AI assistance. The lesson is not that AI writes perfect code; it is that domain owners can now automate more of the messy internal glue themselves. For small businesses, that may be the highest-leverage AI coding use case: reports, inventory, customer ops, and process dashboards.

### 8. Community notes on Codex disk-write behavior — `[V2EX]`
<https://www.v2ex.com/t/1222665>

Another V2EX thread collects reports and suggested mitigations for Codex writing frequently to disk during long-running or streaming tasks. Treat the claims as community reports that still need verification, but the operational concern is real. Agent tools need resource monitoring for disk I/O, logs, caches, watchers, and workspace isolation, not just tokens and CPU.

### 9. Code review in the AI era should target systems, not people — `[Zenn]`
<https://zenn.dev/manalink_dev/articles/ai-coding-era-review-to-dev-process-not-human>

This Zenn article argues that AI-era code review should focus less on blaming the human author and more on inspecting the system that produced the code. That means prompts, context files, test design, CI, review checklists, and rollback paths become part of the review surface. It is a practical framing for teams trying to make AI coding repeatable rather than personality-driven.

### 10. AWS Lambda MicroVMs bring temporary stateful isolation to serverless — `[Publickey]`
<https://www.publickey1.jp/blog/26/aws_lambda_microvms.html>

Publickey reports on AWS Lambda MicroVMs, a new way to provide temporary stateful execution environments isolated by MicroVMs on Lambda. The pitch combines serverless convenience with stronger execution boundaries and short-lived state. That is especially relevant for code execution, sandboxed data processing, and agent tool runtimes.

---

## Editor's note

Today's mix is 6 English-source items, 2 Chinese-source items, and 2 Japanese-source items; all target sources were reachable. Anthropic News was available, but its latest technical release was already covered in yesterday's digest, so Dev Digest editor skipped it to avoid duplication. Start with Gemini computer use, Cloudflare OAuth, and Lambda MicroVMs; they show the infrastructure layer agents need next.
