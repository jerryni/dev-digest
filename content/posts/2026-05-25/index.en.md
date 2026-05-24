---
title: "May 25 · Today's 10 Dev Picks"
date: 2026-05-25T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "privacy", "ai-agents", "supply-chain", "google", "anthropic", "browsers"]
categories: ["daily"]
summary: >-
  Rivian documents a one-click switch that fully severs the vehicle from the internet. LinkedIn is found probing 6,278 browser extensions and shipping an encrypted fingerprint with every request. honker.dev packs durable queues, streams, pub/sub, and cron into a single SQLite file. A Shai-Hulud-themed malicious dependency lands inside PyTorch Lightning — the AI training supply chain just took a direct hit. V2EX has parallel threads on shaky Chinese token plans and engineers paying out of pocket to use Claude at work. Google ships Managed Agent API and Antigravity 2.0 as the post-I/O second wave. SpaceX's S-1 reveals a $1.25B/month compute deal with Anthropic. Mozilla formally opposes Chrome's built-in Prompt API. Today's thread — the defaults for privacy, supply-chain trust, and compute economics are all being rewritten at once.
---

## Today at a glance

Three quiet through-lines tie today's items together. **Ownership of the default** — Rivian documents complete offline mode, LinkedIn quietly weaponizes extension fingerprints, and Mozilla blocks Chrome's Prompt API push. **Supply-chain trust at the AI training layer** — Shai-Hulud lands inside PyTorch Lightning while Google ships Managed Agent API and Antigravity 2.0 to take more of the runtime surface for itself. **Compute economics in the open** — SpaceX's S-1 names Anthropic in a $1.25B/month contract, while V2EX engineers discuss paying out of their own pocket to do their day jobs. The two most actionable items for engineering leaders today: audit your `uv.lock` / `poetry.lock` for the Shai-Hulud variant, and decide before summer ends whether you're building agents on managed runtimes or your own harness.

## 1. Rivian documents a full-disconnect switch for the vehicle

[Rivian allows you to disable all internet connectivity](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) · `Rivian / HN`

Rivian's support knowledge base now spells out a one-click setting that cuts all data flow between the vehicle and the internet — not just telemetry, but OTA updates, map refreshes, fleet diagnostics, all of it. In a world where most cars assume always-on connectivity, this resets the floor: a manufacturer treating "fully offline" as a documented product capability rather than a workaround. Worth bookmarking when the next vehicle-privacy debate flares — it shifts the burden of proof.

## 2. LinkedIn scans 6,278 browser extensions and encrypts the result into every request

[LinkedIn scans for 6,278 extensions and encrypts the results into every request](https://404privacy.com/blog/linkedin-is-scanning-your-browser-extensions-this-is-how-they-use-the-data/) · `404privacy.com / HN`

Researchers reverse-engineered LinkedIn's frontend and found it probing 6,278 browser extensions, then packaging the result as an encrypted fingerprint and shipping it with every backend call. The web platform assumes extension presence isn't observable; this is a side channel that works anyway. The interesting part isn't that it's possible — it's that a top-tier social network ships it to production. Expect regulators in EU and California to ask pointed questions; expect competitors to quietly adopt the same technique first.

## 3. honker.dev: durable queues, streams, pub/sub, and cron inside one SQLite file

[Durable queues, streams, pub/sub, and a cron scheduler – inside your SQLite file](https://honker.dev/) · `honker.dev / HN`

Another entry in the "SQLite as everything backend" genre, but more ambitious than usual: a single `.db` file holds a durable queue, streams, pub/sub topics, and a cron scheduler, with workers reading directly from the file. The pitch is the long tail of projects where Redis + RabbitMQ + a cron container is overkill but you still need something durable. The cron-in-a-DB part is the genuinely novel piece — most prior attempts kept scheduling external.

## 4. China's domestic token plans get a credibility check on V2EX

[阿里云 tokenplan 和 百度 codingplan 慎买 (Aliyun and Baidu token plans — buyer beware)](https://www.v2ex.com/t/1214866) · `V2EX`

A V2EX thread enumerates concrete mismatches between marketing copy and actual usage limits, expiry rules, and refund policies on Aliyun's tokenplan and Baidu's codingplan. The subtext: as Chinese developers find stable workflows for paying Claude and OpenAI directly with foreign-issued cards, domestic AI plans now compete on trust rather than access, and this kind of thread genuinely moves next quarter's conversions. Useful signal for anyone trying to read the temperature of China's frontier-model adoption.

## 5. "How many of you are paying for tokens out of pocket to do your day job?"

[你们多少人是自己付费买 token 干公司的工作任务了？](https://www.v2ex.com/t/1214981) · `V2EX`

A V2EX poster asks how many engineers are using personal credit cards to buy Claude or Cursor tokens because their employer hasn't approved a budget, but the work load now assumes AI in the loop. Replies split sharply between "tools are personal, like a mechanical keyboard" and "this is silent cost-shifting from employer to employee." Either reading, the de facto AI expense policy at most companies is now being written by individual engineers, not by Finance — and that gap will narrow noisily over the next year.

## 6. Google ships Managed Agent API: one HTTP call, hosted Linux-equipped AI agent

[Google announces Managed Agent API — one API call spins up a hosted AI agent with a Linux environment](https://www.publickey1.jp/blog/26/apigooglelinuxaimarkdownmanaged_agent_api.html) · `Publickey`

Following Google I/O, Managed Agent API lets developers fire a single HTTP request and get back an AI agent running inside a fully managed Linux sandbox, with behavior configured through Markdown. This productizes the "agent runtime" — no more rolling your own Docker, no more wrapping MCP yourself, you just pay GCP. The strategic question for anyone building agent products: do you compete by owning the execution environment, or by owning the workflow above it? Google just made the first option a lot less differentiated.

## 7. Antigravity 2.0: Google's agent IDE writes a Doom-capable OS from scratch

[Google announces Antigravity 2.0 — demo writes an OS from scratch, runs Doom](https://www.publickey1.jp/blog/26/googleantigravity_20osdoom.html) · `Publickey`

Antigravity 2.0 launched at I/O with an aggressively long-horizon demo: an agent writing a minimal OS that boots Doom from scratch. The point isn't the OS — it's the proof-of-stamina, aimed at the credibility gap Claude Code and Cursor still benefit from on multi-step tasks. Alongside it, formal Android support plus an Android Knowledge Base and Android Skills. For teams already comparing coding agents, this changes the evaluation from "which IDE plugin" to "which full-stack agent toolchain we standardize on."

## 8. Shai-Hulud-themed malware lands in PyTorch Lightning

[Shai-Hulud Themed Malware Found in the PyTorch Lightning AI Training Library](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · `semgrep.dev / HN`

Semgrep found a malicious dependency in the PyTorch Lightning supply chain, themed after the Dune sandworms and clearly part of the broader Shai-Hulud campaign. The target isn't your model weights — it's the SSH keys, cloud credentials, and wandb tokens sitting on your training boxes. The supply-chain conversation around AI has mostly been about model provenance; this drags it forward to the training layer. If you have anything running PyTorch Lightning today, audit your lockfile this morning, not Monday.

## 9. SpaceX S-1 reveals Anthropic on the hook for $1.25B/month in compute

[SpaceX S-1 — Anthropic Cloud Services Agreement for COLOSSUS / COLOSSUS II](https://www.sec.gov/Archives/edgar/data/1181412/000162828026036936/spaceexplorationtechnologi.htm) · `SEC / Simon Willison`

SpaceX's IPO filing names Anthropic by name: a Cloud Services Agreement covering compute on COLOSSUS and COLOSSUS II, $1.25 billion per month through May 2029, terminable by either party with 90 days' notice. This is one of the cleanest public numbers we've ever had on what frontier-model inference and training actually cost at scale. Read alongside Anthropic's AWS and Google Cloud deals, the picture is multi-vendor compute sourcing now codified in SEC filings — useful citation for any "is AI economically sustainable" argument going forward.

## 10. Mozilla formally opposes Chrome's built-in Prompt API

[Mozilla's opposition to Chrome's Prompt API](https://github.com/mozilla/standards-positions/issues/1213#issuecomment-4347988313) · `GitHub mozilla/standards-positions`

Mozilla posted a clear "harmful" position on Chrome's proposed Prompt API — the proposal to let webpages call a browser-embedded LLM directly. The objections cluster around three things: it makes browser fingerprinting much denser, it creates web fragmentation as each browser ships a different built-in model, and it sets a precedent of embedding vendor-specific AI capability into the web standard surface. If you were planning to lean on `await ai.prompt(...)` in production, the political timeline just slipped. Web platform AI is now in a standards-process fight, not an implementation race.

## Editor's note

Today's ten cohere around three quiet rewrites: who owns the default for privacy (Rivian, LinkedIn, Mozilla), how supply-chain trust extends backward into AI training (Shai-Hulud, Google's runtime grabs, China token plans), and how compute economics are finally getting numbers (SpaceX-Anthropic, out-of-pocket tokens). If you only read two: **Shai-Hulud in PyTorch Lightning** moves the AI supply-chain conversation from theory to lockfile, and **the $1.25B/month in SpaceX's S-1** gives the AI-cost debate its first hard, citable floor.
