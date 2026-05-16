---
title: "May 17 · Today's 10 Dev Picks"
date: 2026-05-17T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Anthropic", "Claude", "security", "browser-standards"]
categories: ["daily"]
summary: "LinkedIn fingerprints 6,278 browser extensions, PyTorch Lightning gets a Shai-Hulud supply-chain hit, Anthropic ties up $200M with the Gates Foundation, and Mozilla draws a line against Chrome's Prompt API."
---

## Today at a glance

Today's threads cluster around two questions: how do you keep AI supply chains honest, and how far should agents be wired into your day-to-day tools? On the security side, LinkedIn was caught fingerprinting browser extensions and PyTorch Lightning got hit by a Shai-Hulud-themed dependency attack — both land in the same week your AI team is probably running `pip install` against fresh checkpoints. On the agent side, Anthropic shipped two enterprise moves (Gates Foundation partnership, Claude for Small Business), VS Code added Agent windows for multi-agent workflows, and Mozilla picked a fight with Chrome over a browser-native Prompt API. Pick your battles.

## Today's 10 picks

### 1. LinkedIn scans 6,278 browser extensions, encrypts the result into every request (HN · EN)

[Source: 404privacy.com](https://404privacy.com/blog/linkedin-is-scanning-your-browser-extensions-this-is-how-they-use-the-data/) · [HN thread](https://news.ycombinator.com/item?id=47967262)

Researchers found LinkedIn quietly fingerprinting 6,278 extension IDs and shipping the encrypted result on every request. If your account has ever felt unusually rate-limited or suspicious after installing a scraping or privacy extension, this is probably part of why. The interesting bit isn't the detection — sites have done this for years — but the move to encrypt the payload so even your own DevTools can't see what's being collected.

### 2. Shai-Hulud-style malware lands in PyTorch Lightning's dependency tree (HN · EN)

[Semgrep writeup](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · [HN thread](https://news.ycombinator.com/item?id=47964617)

Last year's npm Shai-Hulud worm now has a Python cousin sitting inside a Lightning dependency. The attack profile is brutally well-suited to AI shops: long-running training jobs with broad service-account scopes, GPU clusters with weak tenant isolation, and a culture of `pip install`-then-train. Pin your lockfiles, rotate CI tokens, and assume your training nodes can reach your model registry.

### 3. Programming languages aren't lock-in any more (Simon Willison · EN)

[Source: Not so locked in any more](https://simonwillison.net/2026/May/14/not-so-locked-in/)

Riffing on Bun's Zig-to-Rust rewrite and a mid-sized shop that used coding agents to port both native mobile apps to React Native in weeks, Simon makes a small but provocative observation: language choice used to be a decade-long bet, now it's closer to a reversible action. Worth bringing to the next stack-debate meeting — the framing shifts more than the conclusion.

### 4. One infra engineer's $200/week Codex bill, broken down (V2EX · ZH)

[V2EX thread](https://www.v2ex.com/t/1213114)

Real numbers from a serious infra developer, not a vendor case study: where Codex earned its keep, where it didn't, and how the weekly burn looks against the same engineer's prior baseline. If you're costing out Claude Code / Codex seats for a team this quarter, this is closer to ground truth than any pricing-page calculator.

### 5. "After AI-assisted coding, I'm losing my love for programming" (V2EX · ZH)

[V2EX thread](https://www.v2ex.com/t/1213164)

A V2EX post climbing the charts today, with parallel threads showing up on Zenn and HN. The argument isn't technical: when you no longer type the code that ships, what does professional pride look like? Worth tracking because it shows up in retention and IC career-ladder conversations before it shows up in tooling.

### 6. A Japanese engineer's notes on migrating from Claude Code to Codex (Zenn · JA)

[Zenn article (Japanese)](https://zenn.dev/gemcook/articles/e56eabc7ba2961)

Concrete, hands-on comparison from someone who used both seriously. Covers sub-agent granularity, context-window discipline, and the billing-model differences that catch teams off guard. If your team is in the "which one do we standardize on?" phase, this is a better starting point than the marketing pages on either side.

### 7. VS Code 1.120 ships "Agent window" preview for multi-agent dev (Publickey · JA)

[Publickey article (Japanese)](https://www.publickey1.jp/blog/26/vs_codeaiagent_window.html)

VS Code is bringing the multi-agent UX into the core editor: each agent runs in its own window with state aggregated to a single panel. This is VS Code's direct answer to Cursor / Codex desktop, but the more interesting downstream effect is that teams will need a shared convention — probably a checked-in `.vscode/agents.json` — for how agents are configured per repo.

### 8. Anthropic forms a $200M partnership with the Gates Foundation (Anthropic news)

[Anthropic announcement](https://www.anthropic.com/news/gates-foundation-partnership)

Two hundred million dollars channelled into global health, agriculture, and education via the foundation's partner network. Beyond the headline, this is a frontier lab formally productizing "AI for non-commercial use" — something startups in the nonprofit-tech space have been waiting for as a procurement signal.

### 9. Anthropic launches Claude for Small Business (Anthropic news)

[Anthropic announcement](https://www.anthropic.com/news/claude-for-small-business)

A separate SKU aimed at 5–50 person shops, sitting between Pro and Team. Strategically, Anthropic is segmenting by company size rather than by "individual vs. enterprise," which makes the lineup more legible for companies that previously had to hack Pro seats into a small business. Expect Google Workspace / Microsoft 365 to react.

### 10. Mozilla opposes Chrome's Prompt API proposal (HN · EN)

[Mozilla standards-positions issue](https://github.com/mozilla/standards-positions/issues/1213) · [HN thread](https://news.ycombinator.com/item?id=47959463)

Chrome wants to standardize a browser-native API that lets JS talk to an in-browser LLM; Mozilla says no, on the grounds that bundling model weights into the platform makes the Web depend on an opaque, non-portable runtime. This is the kind of fight that shapes the next decade of front-end architecture. Watch the W3C TAG response next.

## Editor's note

The day's meta-theme is the collision of "AI getting deeper into workflows" with "AI not being safe enough yet to be that deep." Two must-reads: **item 2** (Shai-Hulud in PyTorch Lightning) is a wake-up call about how thin AI supply-chain hygiene actually is, and **item 10** (Mozilla vs. Prompt API) sets the terms of debate for whether AI becomes a first-class Web primitive at all.

Source note: GitHub Trending was not reliably reachable during this morning's fetch and is excluded from today's pool. The other six sources returned cleanly.
