---
title: "May 21 - Today's 10 Dev Picks"
date: 2026-05-21T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "ai-agents", "antigravity", "managed-agents", "sqlite"]
categories: ["daily"]
summary: >-
  LinkedIn is fingerprinting 6,278 browser extensions on every request. Belgium reverses course on its nuclear shutdown, citing AI datacenter load. honker.dev stuffs durable queues, streams, pub-sub and cron into a single SQLite file. Google ships Antigravity 2.0 (Agent writes an OS from scratch, runs Doom) plus a Managed Agent API; Dell puts GB10 / GB300 on the desktop; Linux Foundation books Tokyo for AGNTCon + MCPCon. The throughline is unmistakable - Agents are now eating infrastructure, not just IDEs.
---

## Today at a glance

The week's stories were Agents-in-the-IDE. Today's are Agents-as-infrastructure. Google's Managed Agent API spins up an Agent with a managed Linux sandbox in one POST. Dell ships a desktop with GB10 / GB300 aimed at running Agents locally. Antigravity 2.0 demo writes a minimal OS from scratch and boots Doom on it. Linux Foundation just placed AGNTCon and MCPCon in Tokyo - the first time a major Western Agent / MCP conference is held there, and a signal that Japan-market budgets are now real. Two adjacent stories sharpen the picture: Belgium pulling back from nuclear decommissioning explicitly because of datacenter electricity demand, and LinkedIn quietly scanning 6,278 browser extensions on every request. Power and surveillance, both downstream of the same Agent rush.

## 1. LinkedIn scans 6,278 browser extensions on every request

[LinkedIn scans for 6,278 extensions and encrypts the results into every request](https://404privacy.com/blog/linkedin-is-scanning-your-browser-extensions-this-is-how-they-use-the-data/) · `Hacker News`

A 404privacy researcher reverse-engineered LinkedIn's client JS and found it actively probes 6,278 known Chrome extensions and encrypts the result into every outbound API request. If you use Sales Navigator scrapers, automation extensions, or any third-party LinkedIn tooling, LinkedIn now knows which ones - on every page view. If your day job involves LinkedIn at all, the practical move is to isolate automation extensions into a separate browser profile.

## 2. Belgium reverses nuclear decommissioning

[Belgium stops decommissioning nuclear power plants](https://dpa-international.com/general-news/urn:newsml:dpa.com:20090101:260430-930-14717/) · `Hacker News`

Two reactors slated for shutdown will stay online, with the government citing AI datacenter and industrial electricity demand as the explicit reason. After the UK and Sweden, Belgium is the third historically anti-nuclear European country to reverse course in 18 months. The AI investment thesis is no longer mainly about GPUs - it's about the grid. Watch utility procurement and PPA structures, not silicon prices.

## 3. honker.dev: durable queues, streams, pub-sub, cron - all inside one SQLite file

[Durable queues, streams, pub/sub, and a cron scheduler – inside your SQLite file](https://honker.dev/) · `Hacker News`

A new embedded library packs Sidekiq / NATS / cron-equivalent functionality into a single SQLite file. Process-local, no separate broker, file-copy backup. If you've been over-provisioning Redis plus a queue service for an internal tool or small SaaS, this is the kind of dependency-removal worth a Friday afternoon. Claimed throughput is multi-thousand TPS on WAL mode, which is comfortably enough for most internal workloads.

## 4. V2EX: Among Chinese AI IDEs, TRAE is the least disappointing

[Among Chinese-built AI IDEs, TRAE is the only one barely usable (thread, ZH)](https://www.v2ex.com/t/1213384) · `V2EX`

The Chinese dev community ran a survey of local AI IDEs (Tongyi Lingma, CodeGeeX, Wenxin, TRAE). Consensus from 90+ replies: TRAE is the only one whose Agent mode reliably finishes tasks, but it's still a version behind Claude Code and Cursor. The interesting bit isn't the ranking - it's the unspoken question underneath: with Claude Code / Cursor unable to operate freely inside Chinese enterprises, how does the market split? If your company has a China engineering hub, this is the local-tooling reality you're actually buying into.

## 5. V2EX: China's national "compute grid" is coming

["算力网" is coming - China's national compute scheduling network (thread, ZH)](https://www.v2ex.com/t/1213402) · `V2EX`

Discussion of China's national compute-grid initiative - the v2 of "East Data, West Compute" - covering cross-province GPU scheduling, unified pricing, and centralised allocation for training workloads. The technical depth in the thread is light, but the signal is loud: China is operationalising sovereign-compute in a way the EU is still only debating. If you're modelling GPU supply for a multi-region AI product, the assumption that China-hosted training will route through a single national platform within 18-24 months is now closer to baseline than tail risk.

## 6. Publickey: Google ships Antigravity 2.0 - Agent writes an OS, boots Doom

[Google announces Antigravity 2.0; demo Agent builds an OS from scratch and runs Doom (JA)](https://www.publickey1.jp/blog/26/googleantigravity_20osdoom.html) · `Publickey`

The Antigravity Agent runtime jumps to 2.0, with stronger long-horizon planning and self-directed sub-task orchestration. Demo: given an empty repo, the Agent designs and implements a minimal OS and successfully boots Doom on it. That puts Google's coding Agent in roughly the same conversation as Anthropic's Claude Code and OpenAI's Codex on "ship a real project end-to-end." If you're benchmarking Agents internally, you now need all three on the bench, not just one.

## 7. Publickey: Dell Deskside Agentic AI - GB10 / GB300 in a workstation

[Dell announces Deskside Agentic AI with NVIDIA GB10 / GB300 for local Agents (JA)](https://www.publickey1.jp/blog/26/aipcdell_deskside_agentic_ainvidia_gb10gb300.html) · `Publickey`

Dell is positioning GB10 / GB300 desktops as workstations for running Agents locally. The play is squarely at compliance-heavy enterprises that won't ship code to the cloud - Japanese financials, government, manufacturing. Worth tracking: if Dell's pricing meaningfully undercuts cloud inference for steady-state workloads, the "everything goes to the cloud" assumption gets weaker in 2026, at least for high-confidentiality verticals.

## 8. Anthropic: widening the conversation on frontier AI

[Widening the conversation on frontier AI](https://www.anthropic.com/news/widening-conversation-ai) · `Anthropic News`

Anthropic published a policy-leaning post arguing that frontier-model evaluations shouldn't live only inside AI labs - governments, academia, and third parties should be in the loop. Concrete effect for engineers: expect Responsible Scaling Policy artefacts to start showing up as part of enterprise procurement checklists. If you're integrating Claude or any frontier model into production, the compliance section of your design doc is about to get longer.

## 9. Publickey: Google ships Managed Agent API - one POST, you get an Agent + Linux sandbox

[Google announces Managed Agent API - one API call spins up an Agent with a Linux sandbox (JA)](https://www.publickey1.jp/blog/26/apigooglelinuxaimarkdownmanaged_agent_api.html) · `Publickey`

Google Cloud's Managed Agent API gives you a fully hosted Agent plus a Linux sandbox in a single call, with Markdown for custom instructions. It's the Google answer to the Anthropic Agent SDK + code execution story, but priced and run as a fully managed service. If you're a SaaS building per-user Agent sandboxes, this is the first cloud-native alternative to standing up Firecracker / gVisor yourself.

## 10. Linux Foundation books Tokyo for AGNTCon + MCPCon, Sept 10-11

[Linux Foundation announces AGNTCon + MCPCon, Tokyo Shibuya, Sept 10-11 (JA)](https://www.publickey1.jp/blog/26/linux_foundationaiagntcon_mcpcon910112.html) · `Publickey`

LF is co-locating its AI Agent and MCP conferences in Tokyo Shibuya on Sept 10-11, 2026. First time a Western-led Agent / MCP conference of this scale has been placed in Japan. The signal: vendors are reading enough enterprise pipeline in the Japanese market to justify the venue. Worth getting CFP and sponsor decisions on the calendar now if your product touches MCP or Agent runtime.

## Editor's note

Today's meta-theme: Agents are no longer just SDK calls - they're starting to demand power grids, hardware, standards, and conference venues. Belgium keeping reactors online, Dell shipping desktop Agent boxes, Google running managed Agent sandboxes, LF holding court in Tokyo - it's the shape of an industry transitioning from "build demos" to "build infrastructure." Two must-reads: **LinkedIn extension scanning** (instant impact if your job touches LinkedIn) and **Google Managed Agent API** (architectural impact over the next 12 months for any team running per-user sandboxes). GitHub Trending rendered empty today, so the EN slate is HN-heavy; Zenn trending was also blank server-side, JA slate leans on Publickey.
