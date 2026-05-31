---
title: "June 1 · Today's 10 Dev Picks"
date: 2026-06-01T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "pyodide", "openbsd", "aws", "claude", "markitdown", "tts", "rsync"]
categories: ["daily"]
summary: "Pyodide moved into a Service Worker runs full ASGI apps in the browser. OpenBSD ships a clean openrsync. AWS Interconnect goes free up to 500 Mbps cross-cloud. markitdown and VoxCPM2 dominate GitHub Trending."
---

## Today at a glance

Monday opens quiet on AI-lab news — the Opus 4.8 / Series H wave already moved through Friday's edition — but several substantive engineering pieces landed over the weekend. Simon Willison cracked Datasette Lite's long-standing Web-Worker limitation by relocating Pyodide into a Service Worker. The OpenBSD team published a clean-room rsync implementation. AWS quietly made up to 500 Mbps of cross-cloud Interconnect bandwidth free. And Microsoft's markitdown plus OpenBMB's VoxCPM2 are both detonating on GitHub Trending, both pointing at the same underlying current: teams are operationalizing internal AI platforms and need better building blocks.

---

### 1. Simon Willison — Running Python ASGI apps in the browser via Pyodide + a Service Worker — `[Simon Willison]`
<https://simonwillison.net/2026/May/30/pyodide-asgi-browser/>

Datasette Lite has long carried a sharp edge: `<script>`-tag Python doesn't execute because Pyodide runs in a Web Worker without DOM/fetch context. Simon walked Claude Opus 4.8 (via Claude Code for web) through a single-session rewrite that puts Pyodide inside a Service Worker, which intercepts fetch and routes it to the ASGI app. Working demos for FastAPI and Datasette 1.0a31 included. The pattern generalizes beyond Datasette: any team distributing internal tools as "static + offline-capable" web apps now has a credible architecture to copy.

### 2. openrsync — A clean OpenBSD-team rsync implementation — `[Hacker News · 184 pts]`
<https://github.com/kristapsdz/openrsync>

BSD-licensed, plain C, minimal dependencies, wire-compatible with mainline rsync. Two threads in the HN comments worth surfacing: auditability ("finally something readable") and supply-chain hygiene as the BSDs continue their slow detachment from GPL tooling. Useful for teams running rsync on embedded targets, in regulated environments, or anywhere a license review of GPL-3 dependencies costs more than the tool itself.

### 3. Pandoc Templates community site — `[Hacker News · 274 pts]`
<https://pandoc-templates.org/>

A curated central catalog of Pandoc templates — LaTeX, Beamer, HTML, reveal.js, DOCX, EPUB. Until now the Pandoc onboarding tax has been "go find someone's gist." With LLM-generated drafts increasingly piped through Pandoc for final layout, having a real template registry materially shortens the path from "Claude wrote this" to "we shipped a PDF that looks like our brand."

### 4. 16 GB AMD GPU: Transformers beats vLLM and SGLang? — `[V2EX · Local LLM]`
<https://www.v2ex.com/t/1216752>

A practitioner benchmark out of the Chinese local-LLM community: on a 16 GB AMD card, plain HuggingFace Transformers beat vLLM and SGLang on both throughput and VRAM use. The thread attributes it to PagedAttention fallbacks on the ROCm path plus framework overhead dominating at small batch sizes. Useful counterweight to the default "always reach for vLLM" advice — if you're on AMD silicon, measure first.

### 5. End-to-end encrypted backups to consumer cloud storage — `[V2EX · 程序员]`
<https://www.v2ex.com/t/1216774>

Stack favored in the thread: rclone crypt, Cryptomator, Restic / Kopia, plus age for key management. The premise — treat any consumer cloud (iCloud, Drive, OneDrive, plus the major Chinese providers) as dumb object storage and put zero trust in the provider — is a sensible default for personal DR. The discussion also covers rclone's chunked-encryption tradeoff vs. Restic's deduplicated archive model.

### 6. "Claude Max 20x isn't enough" — 8 token-saving techniques — `[Zenn · 207 likes]`
<https://zenn.dev/acntechjp/articles/1396e20b5167ce>

The top-trending Japanese-language post today. Practitioner tips for surviving Claude Max 20x quotas: pin a `CLAUDE.md` index, prune context explicitly per task, split into sub-agent calls rather than monolithic prompts, pre-compute codebase summaries. Echoes a broader late-May trend: heavy Claude Code users hitting Max 20x ceilings and reaching for workflow discipline before reaching for the next paid tier.

### 7. AWS Interconnect — multicloud goes free up to 500 Mbps — `[Publickey · Infrastructure]`
<https://www.publickey1.jp/blog/26/aws500mbpsaws_interconnect_-_multicloud.html>

AWS introduced a free tier of up to 500 Mbps for its private cross-cloud Interconnect service connecting AWS to Google Cloud and Azure. Egress and NAT pricing have been the perennial blocker to multicloud architectures; AWS is now treating the data plane between hyperscalers as a strategic surface to occupy. Worth a re-read of your cross-cloud bill before re:Invent.

### 8. microsoft/markitdown — Any Office / PDF / image / audio file → Markdown — `[GitHub Trending · 2,759 stars today]`
<https://github.com/microsoft/markitdown>

Microsoft's Python utility that converts docx / pptx / xlsx / pdf / images / audio into LLM-friendly Markdown. Sitting at 134K stars and still climbing — the obvious read is that internal-AI / RAG platform work has moved from prototyping to production at large companies, and the document-ingestion layer needed a defensible default.

### 9. OpenBMB/VoxCPM2 — Open-source multilingual TTS — `[GitHub Trending · 639 stars today]`
<https://github.com/OpenBMB/VoxCPM>

Second-generation TTS from the Tsinghua-affiliated OpenBMB group: tokenizer-free, multilingual, supports voice cloning and creative voice design. Open-source TTS has lagged the LLM stack badly; VoxCPM2 makes self-hosted, production-grade narration / dubbing / podcast workflows materially more credible for teams that want to keep audio data inside their own VPC.

### 10. EveryInc/compound-engineering-plugin — Claude Code / Codex / Cursor — `[GitHub Trending · 243 stars today]`
<https://github.com/EveryInc/compound-engineering-plugin>

EveryInc packages "compound engineering" — decompose work into parallel sub-agents with explicit context handoffs — into a plugin that drops into Claude Code, Codex, and Cursor. The interesting framing isn't the framework itself but the meta-move: the patterns that productive Claude/Codex users invented by hand are now being shipped as reusable, IDE-agnostic plugins. Plugin ecosystems are starting to matter the way IDE extensions did a decade ago.

---

## Editor's note

The meta-theme today is "extracting more leverage from AI tooling without raising the bill": Simon's Service Worker rewrite, the Zenn token-saving piece, the EveryInc plugin, and AWS's cross-cloud freebie all point in the same direction. If you only read two: **#1 (Pyodide + Service Worker)** for the architectural imagination, and **#6 (Claude token-saving)** for something you can apply before your next standup.
