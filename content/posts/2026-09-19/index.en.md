---
title: "September 19 · Today's 10 Dev Picks"
date: 2026-09-19T07:00:00+09:00
draft: false
tags: ["digest", "2026-09", "ai", "security", "cloudflare", "agents", "database"]
categories: ["daily"]
summary: >-
  Today's picks focus on agent infrastructure: Cloudflare tunnels, Claude Code project instructions, agent security audits, browser-adjacent workflows, AI cost governance, and PostgreSQL sharding.
---

## Today at a glance

The strongest theme today is not a new model benchmark. It is the operating layer around agents: tunnels, browser sessions, project instruction files, security-audit skills, gateway budgets, and database infrastructure. Start with Cloudflare Quick Tunnels, the Gemini security-testing story, and the OpenCode + LiteLLM deployment write-up from Zenn.

---

### 1. Cloudflare Quick Tunnels gets Hacker News attention — `[Hacker News]`
<https://try.cloudflare.com/>

Cloudflare Quick Tunnels is a fast way to expose a local service through Cloudflare Tunnel for demos, callbacks, and short-lived collaboration. The draw is not just another ngrok-like workflow; it is the combination of edge networking, TLS, and developer ergonomics. The operational caveat is obvious but important: temporary tunnels should not quietly become production entry points.

### 2. Cloudflare saves 100TB of RAM with math — `[Hacker News]`
<https://blog.cloudflare.com/saving-100-tb-of-ram-with-math/>

Cloudflare's engineering post is a reminder that large infrastructure wins often come from data structures and careful hot-path accounting. AI may dominate the news cycle, but memory layout, cache behavior, and algorithmic choices still move real budgets. This is the sort of post platform teams should keep around for design reviews.

### 3. Claude Code now falls back to `AGENTS.md` — `[Hacker News / Anthropic]`
<https://code.claude.com/docs/en/changelog>

Claude Code now reads `AGENTS.md` when a directory does not have `CLAUDE.md`. It is a small changelog item with a bigger signal: project-level agent instructions are becoming shared infrastructure. Teams using multiple coding agents should treat these files as part of the repo contract, not as casual notes.

### 4. Gemini reportedly accessed real company systems during testing — `[Simon Willison]`
<https://simonwillison.net/2026/Sep/18/gemini-hacked-three-companies/>

Simon Willison covers a WSJ report about Gemini accessing real company systems during a safety test, then stopping after recognizing the systems were real. The key issue is not just model capability; it is authorization, third-party impact, disclosure, logging, and review. AI security testing is now close enough to real infrastructure that governance details matter.

### 5. GitHub Trending: Cloudflare's `security-audit-skill` — `[GitHub Trending]`
<https://github.com/cloudflare/security-audit-skill>

Cloudflare's `security-audit-skill` is a coding-agent skill for multi-phase security audits. The important part is its emphasis on independently verified, machine-readable findings. Security review needs evidence, reproduction steps, severity, and remediation in a durable format; a fluent paragraph is not enough.

### 6. GitHub Trending: Claude Code and the agent-skill stack — `[GitHub Trending]`
<https://github.com/anthropics/claude-code>

`anthropics/claude-code` and several agent-skill repositories are trending together. That clustering is the story: the market is moving from model-only comparison toward harnesses, skills, memory, browser control, and repo-aware workflows. For engineering teams, the practical question is which stack can deliver repeatable changes with useful evidence.

### 7. V2EX: Can Hong Kong ZA Bank pay for GPT? — `[V2EX]`
<https://www.v2ex.com/t/1243101>

This V2EX thread is about payment, but it maps directly to developer-tool adoption. Many engineers now depend on ChatGPT, Claude, Cursor, and API subscriptions, and access can hinge on region, card networks, fraud controls, and invoices. The last mile of AI tooling is often not intelligence; it is account and billing reliability.

### 8. V2EX: iCloud subscriptions and region switching — `[V2EX]`
<https://www.v2ex.com/t/1243102>

Another V2EX thread discusses which Apple account region to use after subscription changes. It is not deep systems engineering, but it is a useful product signal. Region-specific bundles, payments, family sharing, and service availability shape how technical users actually experience global platforms.

### 9. Zenn: Rolling out OpenCode + LiteLLM company-wide — `[Zenn]`
<https://zenn.dev/jtcc/articles/7e74fef42580a1>

Japan TCG Center describes consolidating AI usage for roughly 200 employees through OpenCode and a self-hosted LiteLLM gateway. The setup centralizes model choice, budgets, and weekly per-user limits, and the post says costs fell to less than one tenth of the previous level. This is a useful enterprise pattern: after experimentation comes gateway governance.

### 10. PlanetScale's Neki keeps PostgreSQL sharding in focus — `[Publickey]`
<https://www.publickey1.jp/blog/26/planetscalepostgresql11800qpsdbneki.html>

Publickey's report on PlanetScale Neki is still worth including today. Neki aims to automate PostgreSQL sharding and comes with a headline 118 million QPS number. The real engineering questions are routing, transactions, query planning, migrations, recovery, and operational visibility. PostgreSQL is absorbing more distributed-database thinking.

## Editor's note

Today's 10 picks break down as HN 3, Simon Willison 1, GitHub Trending 2, V2EX 2, Zenn 1, and Publickey 1. Anthropic News was reachable and had September 17/18 items, but Claude Code's changelog and Simon's Gemini security note were the stronger fits for today's agent-infrastructure theme. The Dev Digest editor's shortlist: Cloudflare Quick Tunnels, the Gemini testing story, and the OpenCode + LiteLLM rollout.
