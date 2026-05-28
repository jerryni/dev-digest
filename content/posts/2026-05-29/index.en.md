---
title: "May 29 · Today's 10 Dev Picks"
date: 2026-05-29T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "anthropic", "claude", "postgres", "agents"]
categories: ["daily"]
summary: "Anthropic ships Opus 4.8 and closes a $65B Series H on the same day. DBOS argues Postgres is enough for durable workflows. SQLite quietly added an AGENTS.md for the agents pointed at it."
---

## Today at a glance

The agentic-coding cycle keeps tightening: Anthropic shipped Claude Opus 4.8 and announced a $65B Series H at a $965B post-money valuation in the same news cycle, while Claude Code picked up Dynamic Workflows. On the infra side, DBOS is making the unsexy-but-useful case that durable workflows are a Postgres feature, not a separate product. And upstream maintainers are starting to write READMEs for agents — see SQLite's new AGENTS.md. Everything is moving toward thinner orchestration and richer model context.

## Today's 10

### 1. Claude Opus 4.8
**Source: Anthropic Product**
<https://www.anthropic.com/news/claude-opus-4-8>

A point upgrade to the Opus class, with claimed gains on coding, agentic tasks, and consistency over long-running work. Topped HN at 1000+ points, with most discussion around whether long-horizon sessions actually hold together better in practice. Worth a regression pass on any agent harness you're shipping this week.

### 2. Anthropic raises $65B Series H at a $965B post-money valuation
**Source: Anthropic Announcements**
<https://www.anthropic.com/news/series-h>

The number is eye-catching, but the operational read is simpler: compute, enterprise, and government remain Anthropic's three investment vectors. Combine this with the recent KPMG and PwC deals and the takeaway for builders is that Claude's enterprise footprint is going to keep widening — which mostly affects which AI your customer's procurement team will already have a contract with.

### 3. Dynamic Workflows in Claude Code
**Source: Claude blog (via HN #26)**
<https://claude.com/blog/introducing-dynamic-workflows-in-claude-code>

Claude Code is moving from static slash-commands and skills to workflows the agent can compose on the fly. This is the kind of release that looks like a UX tweak and is actually an architectural turn — from "agent runs a fixed pipeline" to "agent assembles a pipeline as conditions change." Expect copycats in Cursor, Windsurf, and the various open-source harnesses within weeks.

### 4. Just Use Postgres for Durable Workflows
**Source: DBOS Blog (via HN #3)**
<https://www.dbos.dev/blog/postgres-is-all-you-need-for-durable-execution>

The argument: you don't need Temporal, Airflow, or a bespoke engine — one Postgres table plus a transaction gets you exactly-once durable execution. The HN thread predictably picks at concurrency edges, but the underlying point survives the critique. If you're already paying for Postgres operationally, this is worth a weekend prototype.

### 5. Various LLM Smells
**Source: shvbsle.in (via HN #4)**
<https://shvbsle.in/various-llm-smells/>

Code-smell taxonomy applied to LLM interactions. The author catalogs the patterns that keep recurring across agents — fake-grepping, premature apology loops, context bleed across turns — and pairs each with a mitigation. Useful for sharpening internal style guides on how your team prompts agents in CI.

### 6. SQLite's repo now has an AGENTS.md
**Source: Simon Willison's Weblog**
<https://github.com/sqlite/sqlite/blob/master/AGENTS.md>

Not written for the SQLite team's own agents — it's a notice to people pointing agents at the SQLite codebase. The first line says they don't accept GitHub pull requests. It's a small but interesting move: upstream projects are starting to write docs aimed specifically at coding agents to shape how they behave.

### 7. AWS launches Kiro Web, a browser-based coding agent
**Source: Publickey (JP)**
<https://www.publickey1.jp/blog/26/awswebaikiro_web.html>

A coding agent that runs entirely in the browser, no local install. The strategic angle: AWS just removed the local-install friction that has kept tools like Cursor and Claude Code out of regulated environments. Expect Kiro Web to spread quickly inside enterprises where security review is the actual bottleneck.

### 8. VS Code's Agent Window preview
**Source: Publickey (JP, 5/15)**
<https://www.publickey1.jp/blog/26/vs_codeaiagent_window.html>

A native UI for running multiple agents in parallel inside one VS Code window. Trending writeups across the JP dev blog scene this week ("Cursor 3's Agent Window after two weeks" is on Zenn) suggest this multi-agent pattern is becoming the default mental model for IDE-side agentic work.

### 9. .NET MAUI is finally leaving Mono for CoreCLR
**Source: Publickey (JP)**
<https://www.publickey1.jp/blog/26/mononet_mauixamarinmonocoreclr.html>

The Mono runtime that has powered Xamarin and .NET MAUI is being replaced by CoreCLR. Not flashy, but the move should clear up a long list of debugging and performance pain points that .NET mobile devs have lived with. If you maintain a MAUI codebase, schedule the migration runbook.

### 10. Docker's official AI agent "Gordon" is now GA
**Source: Publickey (JP)**
<https://www.publickey1.jp/blog/26/dockeraigordondocker.html>

Docker shipped a GA release of an AI agent specifically for Docker problems — Dockerfile authoring, build failures, image debugging — available even on the free tier. Narrow scope is the appealing part: it's an agent that knows it's only supposed to know one thing, which is the opposite of where most general-purpose agents drift.

## Editor's note

Two must-reads today: **#4 (Postgres for durable workflows)** and **#3 (Dynamic Workflows in Claude Code)**. They sit at opposite ends of the stack but tell the same story — complexity is migrating out of bespoke runtimes and into model context. GitHub Trending exceeded the single-response size limit today and Zenn's daily trending API returned older snapshots, so the JP slots leaned on Publickey instead.
