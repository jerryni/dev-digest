---
title: "May 22 - Today's 10 Dev Picks"
date: 2026-05-22T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "privacy", "supply-chain", "ai-agents", "browser", "dev-tools"]
categories: ["daily"]
summary: >-
  Rivian quietly ships a real off-switch for vehicle telemetry. The Shai-Hulud worm lands in PyTorch Lightning. Mozilla tells Chrome to slow down on the Prompt API. Simon Willison summarizes six months of LLM motion in five minutes. Anthropic buys Stainless. A 400-line shell script wants to be your coding agent. Today's throughline is consolidation - of telemetry control, of supply chain attacks, and of the agent stack itself.
---

## Today at a glance

A quieter news day, but a useful one. Privacy and supply-chain stories dominate the top of HN, while the AI infrastructure layer keeps consolidating in the background. Rivian shows what a real opt-out looks like; the PyTorch Lightning ecosystem learns what a real supply-chain attack looks like; and Anthropic's Stainless acquisition tells you something about where the next layer of "boring" AI infra (SDKs, client generation) is heading. Worth reading end-to-end if you ship anything that talks to an LLM or a connected device.

## 1. Rivian lets you disable all internet connectivity

[Rivian allows you to disable all internet connectivity](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) - `Hacker News`

Rivian published a support article walking owners through a single toggle that severs all over-the-air, telemetry, and remote services. No degraded mode, no nagging warnings - just a vehicle that talks to nothing. Tesla, Ford, and GM still treat the data pipe as load-bearing for the driver experience; Rivian is the first major OEM to ship a clean off-switch and document it. Expect this to become a regulator-driven baseline within 24 months.

## 2. Shai-Hulud lands in PyTorch Lightning

[Shai-Hulud themed malware found in the PyTorch Lightning AI training library](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) - `Hacker News`

Semgrep researchers found a malicious package masquerading as a pinned dependency of pytorch-lightning, harvesting cloud credentials and HuggingFace tokens. Same family as the npm wave from last fall, now porting itself into the ML toolchain - which is exactly where credentials are richest. If you cache model weights or pull artifacts on CI, audit your lockfile this week, not next quarter.

## 3. Mozilla opposes Chrome's Prompt API

[Mozilla standards-position: opposition to the Prompt API](https://github.com/mozilla/standards-positions/issues/1213) - `Hacker News`

Mozilla logged a formal opposition to the Prompt API that ships in-browser LLM access. The objection is not anti-AI - it is that hardcoding model behavior into the platform freezes a quality bar that is still moving fast, and creates a fingerprinting surface nobody asked for. Chrome will ship it anyway, but the Standards Positions thread is the cleanest articulation yet of why "AI in the browser" is a harder design problem than it looks.

## 4. The last six months in LLMs in five minutes

[The last six months in LLMs in five minutes](https://simonwillison.net/2026/may/19/six-months-llms/) - `Simon Willison`

Simon's compressed recap of November through May - the death of small context windows, the consolidation around tool-use protocols, the rise of "agent" as load-bearing jargon, and where pricing has actually landed. If you have been heads-down on a single product and need to recalibrate in one sitting, this is the post.

## 5. V2EX: how do you pay down vibe-coded tech debt?

[如何消除 vibe code 产生的技术债？](https://www.v2ex.com/t/1214452) - `V2EX`

A working-engineer thread asking the question every team will face within the year: when a junior or PM ships an Agent-generated feature, what does the rewrite look like, and who owns it? Comments range from "treat it like contractor code" to "rewrite the whole thing in two days with the same agent." The Chinese-speaking dev community is having this conversation earlier and more openly than the English one - worth following.

## 6. V2EX: Antigravity triples its Gemini quota, permanently

[Antigravity: Gemini quota raised to 3x permanently](https://www.v2ex.com/t/1214387) - `V2EX`

Anecdote-driven thread confirming what Google announced quietly: free tier and pro tier on Antigravity both got 3x Gemini call budget, no announcement post, no asterisk. Mid-tier engineers on the ZH side are reading this as a deliberate price war ahead of the Anthropic-AWS rollout. Whether or not that read holds, the practical effect is that "default to Antigravity for side projects" is now an obvious move.

## 7. DuckDB gets a wire protocol: Quack

[DuckDBをクライアント／サーバ化する「Quack」プロトコルが登場](https://www.publickey1.jp/blog/26/duckdbquackduckdb.html) - `Publickey`

DuckDB has lived its life as an in-process analytical engine. Quack adds a wire protocol so multiple DuckDB instances can talk to each other - turning the embedded warehouse into something you can point a fleet at. Not ClickHouse-mature yet, but for analytical workloads the surface area suddenly looks a lot more like a real database, not just a notebook accelerator.

## 8. Bun ports itself from Zig to Rust, using Claude

[JavaScriptランタイムのBun、Claudeを使って開発言語をZigからRustへ移行中](https://www.publickey1.jp/blog/26/javascriptbunclaudezigrust.html) - `Publickey`

Jarred Sumner published a porting guide showing how the Bun team is using Claude to do the mechanical Zig-to-Rust translation, with humans reviewing the diffs. The interesting part is not the language choice - it is the public artifact of a runtime team running an AI-assisted migration on a million-line codebase, and the playbook they are sharing.

## 9. Anthropic acquires Stainless

[Anthropic acquires Stainless](https://www.anthropic.com/news/anthropic-acquires-stainless) - `Anthropic`

Stainless is the OpenAPI-to-typed-SDK generator behind several major AI provider clients, including Anthropic's own. The deal brings SDK generation in-house and signals that Anthropic intends to own the client surface end-to-end - the same playbook Stripe ran on payment APIs a decade ago. Watch for tighter Claude SDK release cadence, and probably a public Stainless successor product for everyone else.

## 10. Pu.sh - a coding-agent harness in 400 lines of shell

[Show HN: Pu.sh - a full coding-agent harness in 400 lines of shell](https://pu.dev/) - `Hacker News`

A counter-statement to the framework arms race. Pu.sh wires up tool-calling, file edits, and a basic plan/execute loop in 400 lines of POSIX shell - no Python, no Node. It is not a production replacement for Claude Code or Aider, but it is a forcing function for understanding what is actually happening under the hood. Worth reading even if you never run it.

## Editor's note

Today's meta-theme: the substrate is hardening. Postgres-shaped workflow engines, DuckDB-with-a-wire-protocol for analytics, Anthropic owning the SDK layer, Rust eating Zig inside a fast-growing runtime. Even the Rivian opt-out and the PyTorch Lightning attack are stories about consolidating control of the data path. If you only have time for two: **Simon Willison's six-month recap** for orientation, and the **Shai-Hulud / PyTorch Lightning** post if your CI ever touches a model artifact. Zenn's trending feed returned an empty SPA shell again today, so JA picks came entirely from Publickey.
