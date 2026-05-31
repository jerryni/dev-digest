---
title: "May 31 · Today's 10 Dev Picks"
date: 2026-05-31T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "anthropic", "sqlite", "zig", "ai-agent", "mcp", "dotnet"]
categories: ["daily"]
summary: "Anthropic closes a $65B Series H at $965B post-money and ships Opus 4.8. SQLite-as-workflow-engine and the MCP-is-dead thesis dominate HN. AWS Kiro Web, .NET MAUI on CoreCLR, and a Zig build system rewrite round out the day."
---

## Today at a glance

A weekend that didn't act like one. Anthropic raised $65B at a $965B post-money valuation and shipped Opus 4.8 the same day. Hacker News is split between two arguments that both matter for anyone building agent systems: is MCP already past its peak, and is SQLite actually enough to replace heavyweight durable-workflow engines like Temporal? Meanwhile AWS pushes a browser-only coding agent, .NET MAUI finally drops Mono, and Zig reworks its build system. Infrastructure layer, shuffled.

## The 10

### 1. Anthropic raises $65B Series H at $965B post-money

Source: Anthropic Newsroom · [link](https://www.anthropic.com/news/series-h)

A valuation that approaches the trillion-dollar mark for an AI-only company. The interesting question isn't the number itself but what it unlocks: more aggressive compute purchases, more enterprise sales muscle (KPMG and PwC partnerships landed in the last two weeks), and probably a deferred price war on the API side. If you're a startup pricing against Claude today, expect that pricing to hold longer than you assumed.

### 2. Claude Opus 4.8

Source: Anthropic Newsroom · [link](https://www.anthropic.com/news/claude-opus-4-8)

Same-day release with the Series H announcement. Anthropic is pitching consistency on long-running agentic work as the main upgrade. If you run Claude Code in production, this is worth a real benchmark on Monday — particularly for multi-step tool-use chains, where Opus 4.6 was already strong but inconsistent on the 30+ minute tasks.

### 3. SQLite is all you need for durable workflows

Source: obeli.sk via Hacker News · [link](https://obeli.sk/blog/sqlite-is-all-you-need-for-durable-workflows/)

630 points on HN today. The argument: stop reaching for Temporal, Cadence, or Inngest by default. For most teams, a single SQLite file as the event log gives you durability, replay, and crash recovery with one binary and zero ops. The pushback in the comments centers on multi-machine coordination and failover — both legitimate, both not your problem until you're well past PMF. Read this before your next workflow-engine procurement meeting.

### 4. Zig: Build System Reworked

Source: ziglang.org via Hacker News · [link](https://ziglang.org/devlog/2026/#2026-05-26)

Zig's build system has always been one of the more opinionated parts of the language, and the rework makes the buildable graph a first-class concept with rewritten dependency and caching models. If you're evaluating Zig as a C/C++ replacement, the engineering ergonomics — not just the language — are quickly catching up to the rhetoric.

### 5. The Last Technical Interview

Source: Steve Yegge on Medium via Hacker News · [link](https://steve-yegge.medium.com/the-last-technical-interview-bc13ddcf4564)

Yegge argues whiteboard algorithm interviews are now a dead format and companies should evaluate candidates on AI-assisted pair coding instead. 190 points, 176 comments, predictably polarized. Whether you agree or not, this is the version of the post most of your hiring committee will read this week — better to engage with the actual argument than the strawman version.

### 6. MCP is dead?

Source: quandri.io via Hacker News · [link](https://www.quandri.io/engineering-blog/mcp-is-dead)

A pointed take that the Model Context Protocol is being routed around by Agent Skills, native function-calling extensions, and vendor-specific tool-use APIs faster than the spec itself can evolve. 340 points, 327 comments. If your team is mid-investment in an MCP server fleet, this is the contrarian read to balance the official narrative.

### 7. AWS Kiro Web: browser-based coding AI agent

Source: Publickey (JA) · [link](https://www.publickey1.jp/blog/26/awswebaikiro_web.html)

No client install required — open the browser, sign in with your AWS account, code. AWS is aiming straight at the Cursor / Claude Code segment, with the strongest pitch being the zero-friction onboarding for enterprise environments where engineers can't install desktop tools. Worth a try if you're already an AWS shop.

### 8. .NET MAUI escapes Mono, moves to CoreCLR

Source: Publickey (JA) · [link](https://www.publickey1.jp/blog/26/mononet_mauixamarinmonocoreclr.html)

The Mono runtime inherited from the Xamarin era is finally retired in favor of CoreCLR. For teams shipping cross-platform mobile on .NET MAUI, expect changes in cold-start time, GC behavior, and AOT semantics. Plan a compat pass against the dev branch before this lands stable.

### 9. Browser-running Android system (V2EX self-promotion)

Source: V2EX (ZH) · [link](https://www.v2ex.com/t/1216344)

A solo developer in China claims to have burned "tens of billions of tokens" building an Android system that runs in a browser. Take the technical claims with a grain of salt and read the thread, but the meta-pattern — individual developers attempting projects that previously required engineering teams — is one of the more interesting 2026 trends to watch.

### 10. From $0 to $170/month: an AI spend escalation diary

Source: V2EX (ZH) · [link](https://www.v2ex.com/t/1216578)

A Chinese developer's candid log of how their AI subscription spend climbed from zero to 1200 RMB (~$170) per month. The thread is more interesting than the number — commenters compare which manual tasks each dollar replaced. A useful ground-truth datapoint if you're trying to size the willingness-to-pay curve in non-US markets.

## Editor's note

The thread running through today is infrastructure-layer reshuffling: SQLite eating workflow engines, MCP getting questioned, Zig rewriting builds, .NET MAUI dropping Mono. The Anthropic Series H just accelerates the surrounding capital cycle. One must-read: **SQLite is all you need for durable workflows** — not because it's necessarily right, but because it forces an honest audit of whether your current workflow stack is over-engineered. Runner-up: **MCP is dead?**.
