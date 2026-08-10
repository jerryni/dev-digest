---
title: >-
  August 10 · Today's 10 Dev Picks
date: 2026-08-10T07:00:00+09:00
draft: false
tags: ["digest", "2026-08", "ai", "agents", "devtools", "web", "database"]
categories: ["daily"]
summary: >-
  Today's picks center on AI agents moving into real engineering workflows: reusable skills, codebase graphs, review discipline, CI costs, plus evergreen lessons from stable URLs and SQLite history storage.
---

## Today at a glance

The strongest thread today is operational: once AI tools leave the demo and enter a codebase, teams need standards, budgets, review habits, and better context systems. The best reads are less about model spectacle and more about how developers keep these tools understandable, portable, and recoverable.

## Picks

1. [How I use LLMs to learn complex topics](https://laurentiugabriel.github.io/blog/articles/how-i-use-llms-to-learn/) · Hacker News

   This HN favorite lays out a practical way to use LLMs as an interactive learning partner for difficult subjects. The useful bit is not asking for a summary; it is building a map, drilling into weak concepts, and checking understanding with examples. For engineers moving across domains, prompt quality and follow-up discipline matter more than the model badge.

2. [Cool URIs Don't Change](https://www.w3.org/Provider/Style/URI) · Hacker News

   The 1998 W3C classic is back in circulation, and it still lands. Stable URLs are not nostalgia; they are infrastructure for citations, docs, search, package metadata, and now retrieval systems. If your framework migration breaks old links, your documentation just lost part of its memory.

3. [PrimeIntellect-ai/prime-agent](https://github.com/PrimeIntellect-ai/prime-agent) · GitHub Trending

   `prime-agent` is a self-improving RLM agent aimed at coding workflows and long-running autonomous tasks. It is another sign that open-source agent work is shifting from chat UX toward runnable systems with state and feedback loops. Before adopting anything like this, inspect task recovery, permissions, audit logs, and how it fails.

4. [vitali87/code-graph-rag](https://github.com/vitali87/code-graph-rag) · GitHub Trending

   `code-graph-rag` combines monorepo understanding with AI and knowledge graphs so agents can query, understand, and edit multi-language codebases. That is a more realistic direction than stuffing more files into a context window. In large repos, call graphs, ownership boundaries, and dependency edges are the context.

5. [GitHub Models is now retired](https://simonwillison.net/2026/Aug/9/github-models-is-now-retired/#atom-everything) · Simon Willison

   Simon Willison documents a GitHub Actions workflow that broke after GitHub Models retired, then moved the job to an OpenAI API key with a spending cap. It is a clean reminder that AI-in-CI depends on product lifecycle and token economics, not just API shape. Budget caps and provider exits should be first-class parts of any automation design.

6. [SQLite compressed text-history prototypes](https://simonwillison.net/2026/Aug/9/sqlite-text-history-prototype/#atom-everything) · Simon Willison

   This prototype stores prior text versions as a JSON array and compresses them with zlib or zstd inside SQLite. The idea works because revision history is packed with repeated text. It is the kind of simple storage experiment worth keeping around: not every history system needs event sourcing before it tries compression and chunking.

7. [你们是怎么一眼看出对方发的是 AI 写的？](https://www.v2ex.com/t/1233121) · V2EX

   A V2EX thread asks how people recognize AI-written text. The engineering angle is trust: generated prose often sounds certain even when the underlying evidence is thin. For design docs, PR descriptions, and incident reports, teams should care less about style fingerprints and more about evidence, reproduction steps, and explicit uncertainty.

8. [一个本地的 markdown 转 card 的应用，Tauri2 开发 支持多端，已开源](https://www.v2ex.com/t/1233113) · V2EX

   This is a small open-source Tauri 2 app for turning local Markdown into cards across platforms. It is not trying to be a giant content SaaS, and that is the point. Lightweight desktop tools that remove one repeated workflow snag are still a good indie-dev lane.

9. [Raspberry Pi 5でClaude Codeを動かす](https://zenn.dev/gsy0911/articles/a4dc76f0639576) · Zenn

   This Zenn post runs Claude Code on a Raspberry Pi 5. The interesting part is not novelty hardware; it is what agentic development feels like on a constrained, always-on, remote-friendly machine. Homelab and edge-device developers can use this kind of write-up to reason about CPU, memory, terminal, and network assumptions.

10. [Agent Plugins 1.0.0 announced](https://www.publickey1.jp/blog/26/agent_plugins_100aimcpopenaiawsgoogle.html) · Publickey

    Publickey reports on Agent Plugins 1.0.0, a specification for sharing AI agent skills and MCP server configuration across different agents. With Microsoft, OpenAI, AWS, Google, and others involved, this looks like an early standardization move around agent capabilities. If your team is already building prompts, scripts, and MCP configs, start treating them like versioned engineering assets.

## Editor's note

Today's 10 picks came from Hacker News 2, GitHub Trending 2, Simon Willison 2, V2EX 2, Zenn 1, and Publickey 1. Anthropic News was reachable, but I did not find a fresh official post from the last 24 hours worth forcing into the set. Dev Digest editor recommends starting with GitHub Models retirement, Agent Plugins 1.0.0, and code-graph-rag: together they show agent tooling becoming an engineering operations problem.
