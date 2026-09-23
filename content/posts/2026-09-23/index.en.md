---
title: "September 23 · Today's 10 Dev Picks"
date: 2026-09-23T07:00:00+09:00
draft: false
tags: ["digest", "2026-09", "ai", "agents", "security", "infrastructure"]
categories: ["daily"]
summary: >-
  Today's thread is the new cost curve for frontier AI, paired with the less glamorous infrastructure needed to run agents safely. Model launches matter, but so do identity protocols, security advisories, hardware hacks, and database scaling.
---

## Today at a glance

OpenAI and Anthropic both pushed the frontier model market toward cheaper daily use, which means engineering teams will run more agentic workloads rather than fewer. The rest of today's list is a useful counterweight: identity protocols remain brittle, WordPress-scale security still matters, and agent infrastructure is becoming its own layer.

## Picks

### 1. OpenAI introduces GPT-6 Sol and Luna

Source: OpenAI / HN  
Link: https://openai.com/index/introducing-gpt-6-sol-and-luna/

OpenAI expanded the GPT-6 family with Sol and Luna, positioning them as more cost-efficient options below Astra. The API model names are `gpt-6-sol` and `gpt-6-luna`, and the launch emphasizes lower token prices plus better cost-per-task performance. For teams running coding agents or high-volume automation, the interesting part is not just raw capability but how aggressively this changes routing and retry economics.

### 2. Anthropic launches Claude Opus 5.5

Source: Anthropic / HN  
Link: https://www.anthropic.com/claude-opus-5-5

Claude Opus 5.5 is framed as a stronger, cheaper successor path for complex work. Anthropic says it performs at the level of Claude Fable 5.1 on most work while costing less than Opus 5 to run. If you use Claude for migrations, research, or long-horizon coding, this is a re-benchmark-your-own-suite release.

### 3. Simon Willison tracks the new model price war

Source: Simon Willison  
Link: https://simonwillison.net/2026/Sep/22/opus-and-sol-and-luna/

Simon Willison's roundup is useful because it puts multiple model releases in the same market frame. The practical question is becoming less “which model is best” and more “which model should handle which task at which effort level.” Expect internal model-routing policies to age quickly over the next few weeks.

### 4. GitHub Trending: anthropics/financial-services

Source: GitHub Trending  
Link: https://github.com/anthropics/financial-services

`anthropics/financial-services` showed up on GitHub Trending today. Financial workflows are a good stress test for agent systems because they force teams to think about audit trails, permissions, deterministic checks, and explainability. Even if you are not building for finance, repos like this are useful references for constraint-heavy enterprise AI.

### 5. GitHub Trending: agent-substrate/substrate

Source: GitHub Trending  
Link: https://github.com/agent-substrate/substrate

`agent-substrate/substrate` points at a broader shift: agents are becoming runtime systems, not just chat prompts with tools attached. State, tool orchestration, authorization, logging, and recovery behavior are now product features. The winning agent stacks will probably look more like infrastructure than demos.

### 6. Trail of Bits calls SAML a fractal of bad design

Source: HN  
Link: https://blog.trailofbits.com/2026/09/21/saml-a-fractal-of-bad-design/

Trail of Bits published a sharp critique of SAML's accumulated complexity. Anyone shipping enterprise SSO knows the pain: XML signatures, IdP quirks, configuration drift, and ambiguous trust boundaries. This is a good reminder that authentication support is never just a checkbox in a sales deck.

### 7. WordPress advisory: unauthenticated path traversal to conditional RCE

Source: HN / GitHub Security Advisory  
Link: https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-7hp8-65ch-5whp

The WordPress advisory is worth attention because unauthenticated path traversal in software this widely deployed can turn into a fast-moving operations problem. The RCE is conditional, but that should not slow inventory and patch planning. Platform teams should check versions, plugin exposure, and whether caches or WAF rules obscure the real application state.

### 8. ReBarUEFI brings Resizable BAR to more UEFI systems

Source: HN  
Link: https://github.com/xCuri0/ReBarUEFI

`ReBarUEFI` is a hardware hacker's kind of project: bring a modern GPU feature to older UEFI systems. It is interesting for workstation reuse, graphics workloads, and people who enjoy the edge between firmware and performance tuning. It also sits firmly in the “know what you are flashing” category.

### 9. V2EX discusses Opus 5.5 default thinking level

Source: V2EX  
Link: https://www.v2ex.com/t/1244106

V2EX had a thread about Claude Opus 5.5's default thinking level. Community reactions like this are noisy, but they surface the felt changes that benchmarks often miss: latency, answer style, cost surprises, and how defaults affect day-to-day automation. After a model update, your own regression suite is still the best truth source.

### 10. Publickey: PlanetScale previews Neki for PostgreSQL sharding

Source: Publickey  
Link: https://www.publickey1.jp/blog/26/planetscalepostgresql11800qpsdbneki.html

Publickey covered PlanetScale's preview of Neki, a managed service for PostgreSQL sharding. The article is not from the last 24 hours, but it is still a relevant Japanese infrastructure story from the available feed. PostgreSQL scaling keeps attracting serious product work, and managed sharding changes the old build-vs-operate tradeoff.

## Editor's note

The two must-reads are OpenAI's Sol/Luna launch and the Trail of Bits SAML piece. One changes the cost curve for agent-heavy engineering; the other reminds us that enterprise software still runs on old, complicated trust machinery. Zenn Trending did not yield reliable items today, and Anthropic's RSS endpoint returned 404, so this edition uses Anthropic's official page instead.
