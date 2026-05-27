---
title: "May 27 · Today's 10 Dev Picks"
date: 2026-05-27T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "browser-fingerprinting", "supply-chain", "ai-agents", "web-standards", "coding-tools", "nuclear", "privacy"]
categories: ["daily"]
summary: >-
  LinkedIn turns out to be probing browsers for 6,278 named extensions and shipping the result back encrypted on every request. Mozilla files a sharp 'harmful' standards position against Chrome's Prompt API. A Shai-Hulud-themed npm/PyPI supply-chain campaign lands inside PyTorch Lightning. Docker GA's an in-CLI AI agent (Gordon). .NET MAUI finally walks away from the Mono runtime. Belgium reverses its nuclear-decommissioning policy as data-center load forecasts blow past 2030 grid plans. Rivian ships a real 'kill all telemetry' switch. Armin Ronacher pushes back on AI-rewritten GitHub issues. Meta-theme: trust boundaries — between sites and your browser, between AI and your codebase, between AI-rewritten text and your bug tracker — are being redrawn in public this week.
---

## Today at a glance

Today's items cluster around one question: **where do we still draw a trust boundary in 2026?** LinkedIn pushing an encrypted 6,278-extension probe on every page load makes browser-side fingerprinting a first-class adversarial problem again. Mozilla's filing against Chrome's Prompt API is the most pointed standards-position document the project has issued in years — it argues that shipping a built-in LLM API in the browser breaks the web's core compatibility model. The Shai-Hulud-style malware inside PyTorch Lightning shows the AI supply chain is now the preferred target, not the side door. On the tooling side, Docker GA's an in-CLI agent (Gordon) the same week Cursor visibly tightens its usage caps and Chinese devs openly debate which free coding tool to switch to. Two wildcards — Belgium walking back nuclear decommissioning specifically because of data-center demand, and Rivian shipping a serious 'disconnect everything' switch — round out the picture.

## 1. LinkedIn scans your browser for 6,278 extensions on every request

[LinkedIn scans for 6,278 extensions and encrypts the results into every request](https://news.ycombinator.com/item?id=47967262) · `404privacy.com / HN 299`

404privacy.com reverse-engineered the LinkedIn web client and found it probes for a hard-coded list of 6,278 extensions via web-accessible-resource pings, then encrypts the bitmap and attaches it to every outbound request. The encryption isn't end-to-end — it's a client-side obfuscation step meant to defeat extension-side blocking. The interesting twist isn't surveillance-as-such; it's that a major SaaS now treats your installed extensions as part of its fingerprint. Anyone running an enterprise extension allowlist should expect this to leak the org's identity through any logged-in employee's session.

## 2. Mozilla calls Chrome's Prompt API "harmful"

[Mozilla's opposition to Chrome's Prompt API](https://github.com/mozilla/standards-positions/issues/1213#issuecomment-4347988313) · `github.com/mozilla / HN 564`

Mozilla's standards-positions repo now carries a formal "harmful" classification for Chrome's `window.ai.languageModel` proposal. The core objection: an LLM exposed through a web API can't be specified, because its output is neither deterministic nor versionable across browsers. Mozilla argues this hollows out the web's "write once, render everywhere" contract. The thread also pulls in Apple's WebKit team, who quietly agrees. If you ship a site that uses Chrome's Prompt API today, write it on the assumption it will be a Chrome-only feature indefinitely.

## 3. Shai-Hulud-themed malware lands in PyTorch Lightning

[Shai-Hulud themed malware found in the PyTorch Lightning AI training library](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · `semgrep.dev / HN 299`

Semgrep's research team caught a malicious dependency injected into PyTorch Lightning's transitive chain, themed after the recurring "Shai-Hulud" supply-chain campaign that hit npm last quarter. The payload targets HuggingFace tokens, AWS keys, and Wandb sessions — the exact credential mix a model-training pipeline holds. The strategic shift to watch: AI-training repos now sit where build systems sat in 2020. If your CI bakes model weights, treat the training-time supply chain with the same paranoia you reserve for production deploys.

## 4. Docker GA's "Gordon," an in-CLI AI agent for Docker

[Docker's official AI agent Gordon ships GA — answers anything about Docker and auto-fixes errors](https://www.publickey1.jp/blog/26/dockeraigordondocker.html) · `Publickey`

Docker promoted Gordon out of beta this week. It's bundled directly into the Docker CLI: `docker ai` opens an agent that can read your Dockerfile, explain build errors, propose fixes, and apply them. Free tier is generous enough to be the default for most individual developers. The interesting positioning: Gordon doesn't compete with Claude Code or Antigravity at the IDE level — it competes inside the CLI of a specific tool. Expect kubectl, terraform, and gh to ship the same shape over the next two quarters.

## 5. .NET MAUI walks away from the Mono runtime

[.NET MAUI finally leaves Mono behind, moving to CoreCLR](https://www.publickey1.jp/blog/26/mononet_mauinet_mauimonocoreclr.html) · `Publickey`

Microsoft confirmed .NET MAUI will move off Mono (the Xamarin-era runtime) onto CoreCLR for mobile and desktop targets in the next major release. This closes a multi-year migration that started when Xamarin was acquired. Practical consequences for cross-platform .NET teams: AOT performance gets significantly better on iOS, GC behavior unifies with server .NET, and several long-standing Mono-only quirks (notably around generic interface dispatch) disappear. If you've been waiting to upgrade off Xamarin.Forms, the runtime parity is finally there.

## 6. Cursor tightens the screws on 500-request users

[Cursor seems to be cracking down on 500-request users — anyone know the last good version?](https://www.v2ex.com/t/1215208) · `V2EX`

A V2EX thread tracks Cursor quietly lowering effective ceilings for users on the $20 "Pro" tier — specifically the 500 fast-request allotment. Multiple users report that newer Cursor versions classify previously-fast requests as slow more aggressively. The thread becomes a swap-meet for which historical version still behaves as advertised. Useful read alongside this week's broader pattern: AI coding tools have moved past "rate limits are a future problem" and into the kind of grey-zone enforcement that breeds version pinning, just like the Claude Code "OpenClaw" behavior story did last week.

## 7. "My company won't pay for AI — which coding agent do I actually use?"

[My company won't pay — which AI should I use to code?](https://www.v2ex.com/t/1215305) · `V2EX`

A pragmatic V2EX thread that maps the current state of the free-tier AI coding tool landscape from a Chinese-developer vantage point. The shortlist that emerges: Qwen3-Coder-via-Aliyun's free plan, Gemini-via-AI-Studio, plus open-weights running locally on a 4090. Notably absent: Claude (paywall is too hard for unfunded use), Cursor (see item 6), Copilot (corporate-key gated). For anyone shipping personal projects today, this is closer to the real lived experience than any vendor benchmark page.

## 8. Belgium reverses nuclear-decommissioning policy

[Belgium stops decommissioning nuclear power plants](https://news.ycombinator.com/item?id=47961319) · `dpa-international / HN 712`

Belgium's federal government has formally paused its nuclear plant shutdowns and is now drafting legislation to extend reactor lifetimes past 2035. The cited driver is electricity demand from AI and cloud workloads outpacing every 2022 forecast. Belgium isn't unique — Germany, the Netherlands, and Sweden are all having the same internal debate — but it's the first EU member to actually reverse a decommissioning timetable. Worth filing alongside the HBM/memory wafer story from last week: AI infrastructure costs are being absorbed by every layer of the physical world, not just by Nvidia margins.

## 9. Rivian ships a real "disable all telemetry" switch

[Rivian allows you to disable all internet connectivity](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) · `rivian.com / HN 331`

Rivian quietly added a single setting that severs all outbound network connectivity from the vehicle — including OTA updates, fleet telemetry, and remote diagnostics. No tier, no upsell, no "but". Counter-trend to every other manufacturer's connected-car push, and the HN thread is dominated by people testing whether this is real or whether some traffic still leaks (early indication: it really does cut everything). If car telemetry policies are on your threat model, this is the new baseline to point at.

## 10. Armin Ronacher pushes back on AI-rewritten GitHub issues

[Armin Ronacher: condensed issue reports beat AI-rewritten ones](https://lucumr.pocoo.org/2026/5/24/pi-oss/) · `lucumr.pocoo.org / Simon Willison`

Armin Ronacher, on receiving a wave of GitHub issues against his new Pi runtime that had clearly been passed through an LLM before submission, articulates the "slop issue" failure mode clearly: AI-condensed reports tend to project false confidence, fabricate minimal repros, and bury the four things that actually matter — the command run, the expected behavior, the observed behavior, the exact error. Useful framing for any open-source maintainer drafting an issue template for the AI-tooling era. The honest version of an issue is four bullet points; anything longer is usually slop.

## Editor's note

The meta-theme is **trust-boundary renegotiation.** LinkedIn quietly extending its fingerprint into your browser extension list, Mozilla declaring Chrome's in-browser AI a standards violation, PyTorch Lightning's supply chain getting compromised exactly because it sits upstream of AI training, Cursor reclassifying what counts as a "fast" request, AI agents creeping into individual CLIs (Docker Gordon), and humans like Armin Ronacher pushing back on AI as an intermediary for human communication — every layer is being asked to relitigate who gets to see, decide, and speak. If you read only two, start with **item 2 (Mozilla vs Prompt API)** for the cleanest framing of why the web platform can't absorb an LLM cleanly, then **item 10 (Ronacher on slop issues)** for the human-process equivalent of the same question.
