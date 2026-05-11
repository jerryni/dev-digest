---
title: "May 11 · Today's 10 Dev Picks"
date: 2026-05-11T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Claude", "browser", "security", "supply-chain", "agents", "Anthropic"]
categories: ["daily"]
summary: "Mozilla draws a hard line on Chrome's Prompt API, Mozilla itself uses Claude Mythos to fix 423 Firefox security bugs in a single month, LinkedIn is caught fingerprinting browser extensions on every request, Shai-Hulud lands in PyTorch Lightning, and Anthropic teams up with Blackstone, Hellman & Friedman, and Goldman to spin up an enterprise AI services company. Meanwhile V2EX is having a Claude-Code-fatigue moment."
---

## Today at a glance

Today's thread is about who gets to define the next interface. Mozilla and Google are fighting in the open about whether the browser should ship a built-in LLM prompt API. Mozilla's own engineering team, simultaneously, used the Claude Mythos preview to push Firefox security bug fixes from ~20/month to 423 in April. LinkedIn — surprise — is enumerating every Chrome extension you have installed and shipping the result back encrypted on every request. And on the AI-vendor side, Anthropic is moving up the stack with a new enterprise services JV alongside Blackstone, Hellman & Friedman, and Goldman Sachs. If you only read three: items 1, 2 and 8.

---

## 1. Mozilla's opposition to Chrome's Prompt API

Tag: [EN · HN Top]
Link: <https://github.com/mozilla/standards-positions/issues/1213#issuecomment-4347988313>

564 points on HN. Mozilla has formally moved its standards-positions issue on the Web Prompt API from "neutral" to "negative." The objection isn't to AI in browsers per se — it's that bundling a model-driven prompt API into the web platform de facto privileges whoever's model the browser ships, hands the platform-vendor a content-moderation lever over the open web, and creates a new fingerprinting surface. The thread is the cleanest articulation yet of why "just add a built-in `window.ai`" looks like a feature and acts like a moat. If you're building anything that depends on Chrome's on-device prompt path, read this before your roadmap meeting.

## 2. Behind the scenes hardening Firefox with Claude Mythos Preview

Tag: [EN · Simon Willison / Mozilla Hacks]
Link: <https://hacks.mozilla.org/2026/05/behind-the-scenes-hardening-firefox/>

Mozilla's writeup of how privileged access to Anthropic's Mythos preview transformed their security pipeline. Two things flipped: the models got materially better at finding real bugs (including a 20-year-old XSLT issue and a 15-year-old `<legend>` bug), and Mozilla's harness for steering / stacking / filtering models matured enough to keep false-positive load down. The numbers tell the story: Firefox went from 20-30 security fixes per month through 2025 to 423 in April 2026. Pair with item 1: the same week Mozilla publicly objects to Chrome shipping AI in the browser, they're publicly evangelising AI as a security weapon. Both stances are defensible; the contrast is worth noticing.

## 3. LinkedIn scans for 6,278 extensions and ships the result encrypted in every request

Tag: [EN · HN Top]
Link: <https://404privacy.com/blog/linkedin-is-scanning-your-browser-extensions-this-is-how-they-use-the-data/>

299 points and climbing. The 404privacy team reverse-engineered LinkedIn's web client and found it probes for the presence of 6,278 named extensions on every page load, then ships the encoded fingerprint inside an encrypted blob attached to each API request. The likely use is anti-automation / scraping detection, but the side effect is one of the most aggressive browser fingerprinting surfaces in production today, and the encryption is a clear attempt to hide the practice from network inspection. If you do anti-bot work this is interesting; if you care about privacy it's grim. Expect a regulatory ping from EU DPAs.

## 4. V2EX: "After half a year of heavy Claude Code use, I can't take it anymore"

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1211200>

102 replies in 4 hours. The OP — a high-intensity Claude Code user — lists their accumulated grievances: model regressions after every update, rate-limit cliff edges, the agent re-introducing bugs that were fixed the previous week, an opaque "context compaction" that quietly drops the parts you needed. The replies divide into "yes, I switched to Codex / Cursor / Aider" and "the alternatives have the same problems, you're just past the honeymoon." Useful as a temperature check on where AI-coding-tool sentiment is, in the Chinese-developer community specifically, six months into the agentic-engineering era.

## 5. V2EX: "AI is devaluing things — at every layer"

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1211027>

A short, well-argued thread where the OP names the deflationary effect of generative AI across categories that used to signal effort: a polished README, a clean blog post, a thorough PR description, a 100-commit GitHub repo. None of these any longer carry the signal they used to. Simon Willison made the same point this week (item 2 in our May 8 issue if you want the EN angle). The Chinese-language version is sharper and gloomier — closer to a labour-market argument than an aesthetic complaint, and worth reading alongside the agent-tool-fatigue thread above.

## 6. Zenn: Turso is rewriting database design for the agent era

Tag: [JA · Zenn]
Link: <https://zenn.dev/emuni/articles/6eef9f97f564b4>

A thoughtful piece by an engineer at エムニ (Emuni) arguing that AI-agent workloads — many short-lived workers spawning per-task databases — are exactly what Turso's "millions of cheap SQLite databases" model was built for. The article walks through the cost math (a database-per-agent in Turso is cents/month vs. dollars on Postgres-per-tenant), the operational simplifications, and the patterns that fall out when each agent has its own private store. If you're building anything multi-tenant for agents, this is the architectural posture worth evaluating.

## 7. Publickey: enterprise storage vendor's silicon costs jumped 4-10x, prices up 70%

Tag: [JA · Publickey]
Link: <https://www.publickey1.jp/blog/26/ceo41070.html>

Everpure (formerly Pure Storage) chair/CEO Charles Giancarlo published a customer note saying procurement costs for their critical semiconductor components have risen 4x to 10x over the past year, and as a result the company is raising product prices ~70%, with further increases possible. The macro context: AI training and inference demand is consuming HBM and high-density flash supply, squeezing the enterprise-storage tier whose margins were never designed for that input curve. Translation for anyone planning a 2026 hardware refresh: the budget you wrote last quarter is already wrong.

## 8. Anthropic + Blackstone + Hellman & Friedman + Goldman: new enterprise AI services company

Tag: [EN · Anthropic]
Link: <https://www.anthropic.com/news/enterprise-ai-services-company>

Anthropic announced a joint venture with Blackstone, Hellman & Friedman and Goldman Sachs to launch a new enterprise AI services company. The shape: PE-backed services arm that helps large enterprises adopt Claude across complex internal workflows — heavily implementation- and integration-led, not a model business. The strategic read is that Anthropic is hedging against the Accenture/Deloitte stack capturing all the enterprise-AI services margin and would rather participate in it directly. Pair with last week's compute deal (item 8 in our May 8 digest) and the picture is consistent: Anthropic is buying optionality everywhere in the value chain.

## 9. GitHub Trending: ByteDance UI-TARS-desktop

Tag: [EN · GitHub Trending]
Link: <https://github.com/bytedance/UI-TARS-desktop>

Top of the trending board today: ByteDance's open-source desktop computer-use agent. UI-TARS uses a vision-language model fine-tuned specifically on GUI interaction trajectories — click coordinates, keyboard input, screen state. The desktop variant ships a local app that can drive your real machine, which means it walks into the same workflows Claude for Chrome and OpenAI Operator are targeting, but from the open-weights direction. Worth a real evaluation if you've been waiting for an OSS alternative before letting an agent touch your desktop.

## 10. Shai-Hulud-themed malware found in PyTorch Lightning AI training library

Tag: [EN · HN]
Link: <https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/>

299 points on HN. Semgrep's research team found a malicious dependency embedded in the PyTorch Lightning supply chain, branded internally with Frank Herbert's Shai-Hulud worm motif. The payload targets developer credentials and any AI-training pipeline that pulls the package. The interesting thing isn't the payload — it's that this is the second high-profile attack this quarter aimed specifically at the ML training stack, where one compromised wheel can poison every downstream model. If your CI runs PyTorch Lightning, lock the version and audit your lockfiles today.

---

## Editor's note

The meta-theme is platform power, and who's allowed to draw the lines. Items 1 and 2 are the same company taking opposite-feeling stances in the same week — both internally coherent if you read them carefully, but the contrast is the story. Item 8 is the structural one: Anthropic is positioning to capture services revenue, not just API revenue. And item 10 is the boring-but-urgent one: please go check your PyTorch Lightning lockfile.
