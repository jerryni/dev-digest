---
title: "May 18 · Today's 10 Dev Picks"
date: 2026-05-18T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "SQLite", "supply-chain", "Anthropic", "Rivian", "infrastructure", "algorithms"]
categories: ["daily"]
summary: "honker.dev squeezes durable queues, streams, pub/sub, and cron into a single SQLite file. Simon Willison ships datasette-llm-limits to turn LLM bills into a first-class governance object. CopyFail re-opens the disclosure-ethics debate, and Belgium and Rivian both walk back things the industry treated as settled."
---

## Today at a glance

Monday clusters around two ideas. First, the backend stack is rediscovering restraint: honker.dev fits durable queues, pub/sub, and a cron scheduler inside one SQLite file, and Simon Willison's new `datasette-llm-limits` puts an LLM-spending cap into infrastructure rather than into a Slack reminder. Second, several "settled" decisions from the last two years are quietly being unsettled — Belgium has voted to stop decommissioning its nuclear plants, Rivian now ships a hard-off switch for every piece of telemetry, and Daniel Lemire is publishing benchmarks showing standard binary search isn't the right default for large arrays any more. The CopyFail / Forgejo disclosure thread tying them together is a reminder that "we already agreed on this" is rarely as durable as engineers assume.

## Today's 10

### 1. honker.dev — durable queues, streams, pub/sub, and a cron scheduler inside one SQLite file (HN · EN)

[Project: honker.dev](https://honker.dev/) · [HN thread](https://news.ycombinator.com/item?id=47963316)

Embed-it-and-go: an in-process library that gives you queues, streams, pub/sub, and a cron scheduler with SQLite as the storage layer. 158 points on HN; the comment thread is almost entirely "where's the seam vs. NATS / Redis Streams." The real pitch is for early-stage teams whose Kubernetes-and-Redis budget is one person's weekend — turning four moving parts into one file is the kind of consolidation that buys you another six months of focus on the product.

### 2. CopyFail disclosure bypassed Gentoo's maintainer; Forgejo follow-up keeps it going (HN · EN)

[openwall ML](https://www.openwall.com/lists/oss-security/2026/04/30/10) · [Forgejo follow-up](https://dustri.org/b/follow-up-to-carrot-disclosure-forgejo.html) · [HN thread](https://news.ycombinator.com/item?id=47965108)

A vulnerability was reported to an upstream but not to the downstreams that shipped the affected code. Gentoo users carried the unpatched bug for a window the reporter didn't realise they owned. 312 points, and the thread is the cleanest recent reminder that "disclosure" is a dependency-graph problem, not a one-to-one notification. Worth bookmarking next time you write the disclosure section of an open-source security policy.

### 3. Simon Willison ships `datasette-llm-limits` — LLM spend caps as infrastructure (Simon Willison · EN)

[Post: simonwillison.net](https://simonwillison.net/2026/May/15/)

A small plugin that pairs with `datasette-llm-accountant` to enforce hard per-user (or global) caps on LLM spending inside Datasette. Technically modest, conceptually pointed: rate-limiting and budget-limiting belong in the platform, not in monthly invoice surprises. If you're running an internal LLM gateway, this is a useful reference design even if you never deploy Datasette itself.

### 4. V2EX: an open letter from the Zig community on Bun's Rust migration (V2EX · ZH)

[Thread: v2ex.com/t/1213191](https://www.v2ex.com/t/1213191)

The Zig community responds to Bun's Zig-to-Rust move with a measured open letter: leaving is fine, but please don't frame "Zig isn't ready" in your launch materials when the specific issues you hit have known fixes the project can show. The Chinese-language thread tracks two ideas at once: Zig's lack of a corporate backer is itself a structural problem, and Bun's migration is also a real-world demonstration of agent-driven port work compressing engineer-months. Pairs naturally with Publickey's May 12 piece on Bun using Claude for the port.

### 5. V2EX: shipping iRight, a Finder right-click extension for macOS (V2EX · ZH)

[Thread: v2ex.com/t/1213192](https://www.v2ex.com/t/1213192)

An indie developer ships a Finder right-click utility (compress, bulk rename, copy path, etc.) and documents the pre-launch QA loop. The interesting part isn't the app — it's the comments, which turn into an informal census of which macOS Finder enhancements (PathFinder, Default Folder X, Forklift) are still actively maintained in 2026. Useful inventory if you spend your day in Finder.

### 6. Claude Platform on AWS reaches general availability — feature parity finally lands (Publickey · JA)

[Publickey post](https://www.publickey1.jp/blog/26/anthropicawsclaude_platform_on_awsclaudeaws.html)

AWS Bedrock Claude used to lag the direct Anthropic platform on new features by weeks. With Claude Platform on AWS now GA, that gap is closing — the "full set" ships through Bedrock at the same time. For teams whose procurement and audit functions require AWS as the contractual surface (common in Japanese enterprises, financial services anywhere), this removes a quarterly "what works on Bedrock this month" check. Useful context if you're rolling Claude Code out across a regulated enterprise.

### 7. Storage vendor CEO: semiconductor parts 4–10× more expensive, prices up 70% — and rising (Publickey · JA)

[Publickey post](https://www.publickey1.jp/blog/26/ceo41070.html)

Everpure's CEO told investors that component costs have run from 4× to 10× recent baselines, that the company is raising product prices by 70%, and that further increases are likely. The underlying driver is AI training: HBM and high-end NAND demand is consuming the cycle. Capex planning for next year's storage refresh — particularly anything regulated and on-prem — should be re-quoted with current numbers, not last quarter's.

### 8. Rivian adds an official kill-switch for all vehicle telemetry (HN · EN)

[Rivian support article](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) · [HN thread](https://news.ycombinator.com/item?id=47967786)

Owners can disable all data collection, OTA, and remote control from the app. 331 points on HN, with most of the discussion tying back to last week's story of a RAV4 owner physically removing the DCM and GPS module. Rivian is doing as a factory option what other owners are doing with a screwdriver — and the gap between those two postures is becoming a real purchasing axis for privacy-aware buyers.

### 9. Belgium reverses its nuclear decommissioning plan (HN · EN)

[dpa-international.com](https://dpa-international.com/general-news/urn:newsml:dpa.com:20090101:260430-930-14717/) · [HN thread](https://news.ycombinator.com/item?id=47961319)

712 points on HN. With electricity prices high, intermittent renewables under-delivering on baseload, and AI/EV loads pulling demand upward, the Belgian parliament voted to keep its remaining reactors. The infrastructure angle for engineers: hyperscaler siting math is being redone for Belgium and northern France, which had quietly fallen off the list. Worth tracking if your data-center capacity plan stretches past 2027.

### 10. Daniel Lemire: "You can beat the binary search" (HN · EN)

[lemire.me](https://lemire.me/blog/2026/04/27/you-can-beat-the-binary-search/) · [HN thread](https://news.ycombinator.com/item?id=47924912)

A clean benchmark showing that with branch-prediction-friendly probing, you can beat textbook binary search on large arrays in practice. 226 points. The post is most useful for the explicit crossover table: at which N does the predicted-probing approach win, and where does cache-line behaviour kick in. If you're writing custom KV or index code right now, this is worth a careful read before your next benchmark pass.

## Editor's note

Today's meta-theme is restraint and revisitation. The first three items — honker.dev, the CopyFail disclosure thread, `datasette-llm-limits` — argue that mature AI-era backends will lean toward fewer moving parts and explicit governance hooks, not more middleware. The last three — Rivian's kill-switch, Belgium's nuclear reversal, Lemire's binary-search benchmarks — show how recently-"settled" defaults are being reopened across very different layers of the stack. If you only have time for two, read **#1 (honker.dev)** for the tool-design point and **#2 (CopyFail disclosure)** for the security-process one. Zenn's trending page returned no rendered items and GitHub Trending was unreachable for us today; we substituted additional HN picks rather than pad with stale Japanese-language sources.
