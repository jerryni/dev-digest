---
title: "June 3 · Today's 10 Dev Picks"
date: 2026-06-03T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "openai", "codex", "stanford", "rolldown", "vite", "anthropic", "alphabet", "aws"]
categories: ["daily"]
summary: "OpenAI's frontier models and Codex land on AWS. Rolldown 1.0 ships and Vite 8.0 picks it up as the default bundler. Alphabet raises $80B for AI infrastructure. Anthropic widens Project Glasswing the day after filing S-1."
---

## Today at a glance

The dominant thread today is infrastructure positioning. OpenAI added AWS to its distribution list, Alphabet announced an $80B equity raise specifically for AI compute, and Anthropic — fresh off its confidential S-1 filing — expanded the Project Glasswing security coalition. On the actual developer-tooling front, the most concrete win is Rolldown 1.0 GA being adopted as Vite 8.0's default bundler. Meanwhile, OpenAI quietly forced phone-number 2FA on every Codex account overnight, which is melting down developer forums across Asia.

---

### 1. OpenAI frontier models and Codex now on AWS — `[Hacker News · 285 pts]`
<https://openai.com/index/openai-frontier-models-and-codex-are-now-available-on-aws/>

OpenAI shipped GPT-5.5 / 5.4 / 5.3 and the Codex family to AWS Bedrock at price parity with Azure. The procurement story is the real news: AWS-first shops no longer need a parallel Azure tenant just to call GPT models. Tokyo and Frankfurt regions go live on day one, which makes this a serious option for latency-sensitive workloads. The bigger signal is OpenAI itself softening its "compute sovereignty via Azure" stance — distribution beats exclusivity when you're scaling toward an IPO window.

### 2. Stanford CS336: Language Modeling from Scratch — `[Hacker News · 480 pts]`
<https://cs336.stanford.edu/>

Percy Liang's full course materials, assignments, and reference implementations are publicly available. The course walks from tokenizer implementation through Transformers, data pipelines, RLHF, and evaluation, with runnable PyTorch code at every step. Treat the companion `CLAUDE.md` file (yesterday's HN hit) as the agent-collaboration sidecar. If you've been bluffing your way through "how does an LLM actually work" conversations, this is the single best free resource in 2026.

### 3. Rolldown 1.0 GA, adopted as Vite 8.0's default bundler — `[Publickey · Jun 2]`
<https://www.publickey1.jp/blog/26/rustjavascriptrolldown10vite_80.html>

The Rust-based Rolldown bundler hits 1.0 and Vite 8.0 makes it the default for both dev and build. Benchmarks show 30–50% improvements over esbuild with full Rollup plugin compatibility, which removes the long-standing dev/prod divergence that's haunted Vite users since v3. For monorepos still on Webpack 5, this is the migration that finally looks worth doing. Vite 8.0 ships mid-June.

### 4. Alphabet announces $80B equity raise for AI infrastructure — `[Hacker News · 205 pts]`
<https://abc.xyz/investor/news/news-details/2026/Alphabet-Announces-Proposed-80-Billion-Equity-Capital-Raise-to-Expand-AI-Infrastructure-and-Compute-2026-b0myAMewCa/default.aspx>

Alphabet is raising $80B in a single equity tranche earmarked for TPU fabrication, datacenters, and power contracts. Stack this against Microsoft's $80B and Meta's $70B CapEx and you get a ~$300B hyperscaler AI buildout in 2026 alone. The capital intensity story is now well past the point where smaller foundation-model labs can credibly compete on pretraining scale. Watch for second-order effects on power grids in the US Southeast and the Tokyo–Chiba corridor, where new datacenter announcements have already accelerated.

### 5. AWS Kiro Web: browser-based coding agent goes public — `[Publickey · May 28]`
<https://www.publickey1.jp/blog/26/awswebaikiro_web.html>

AWS released Kiro as a hosted web app, no IDE install required. Kiro's differentiator is spec-driven flow — you write the spec first, the agent implements against it — versus the chat-loop style of Cursor and Windsurf. Enterprise procurement is the obvious target: one AWS bill instead of a per-seat external SaaS rider. If your company has been blocking Cursor for security reasons but already trusts AWS, this is the path of least resistance.

### 6. Anthropic expands Project Glasswing — `[Anthropic · Jun 2]`
<https://www.anthropic.com/news/expanding-project-glasswing>

One day after filing its confidential S-1, Anthropic added new members to Project Glasswing, the critical-software security initiative it spun up with AWS, Apple, Cisco, Google, Microsoft, NVIDIA, and others in April. The new additions include European participants and open-source orgs. Operationally this is mostly governance plumbing, but as a narrative move it pairs naturally with the S-1: Anthropic wants to enter public markets framed as responsible infrastructure, not as a model vendor.

### 7. CS336 AI Agent Guidelines — `[Hacker News · 426 pts]`
<https://github.com/stanford-cs336/assignment1-basics/blob/main/CLAUDE.md>

The companion file to today's CS336 course release: a `CLAUDE.md` that tells AI agents how to behave when helping students with the assignments. Worth reading even if you have no interest in the course — it's one of the most refined public examples of agent-collaboration specs (when to ask, when to act, what to verify before committing). Many teams are using it as a starting template for their own internal agent guidelines.

### 8. Fooling around with encrypted reasoning blobs — `[Hacker News · 101 pts]`
<https://blog.cryptographyengineering.com/2026/05/29/fooling-around-with-encrypted-reasoning-blobs/>

Matthew Green dissects OpenAI's new "encrypted reasoning blob" feature, which encrypts chain-of-thought such that even OpenAI's serving infra can't introspect it. His take: the construction is reasonable, but the trust model still pivots on OpenAI not silently rotating keys. For anyone trying to convince a CISO that LLM reasoning can satisfy compliance constraints, this is the rare technical write-up that's both honest about the gaps and useful as a primer.

### 9. OpenAI forces 2FA on every Codex account overnight — `[V2EX · multiple hot threads]`
<https://www.v2ex.com/t/1217218>

OpenAI silently rolled out mandatory phone-number 2FA across every Codex login, including Plus subscribers. Effects are most visible on Chinese-language dev forums (V2EX has four front-page threads on it) where shared-account workflows are widespread. The timing — same week as the AWS launch — strongly suggests this is a compliance cleanup ahead of broader enterprise rollout. If your team relied on rotating Codex accounts, today is the day to fix that.

### 10. The newest Instagram "exploit" is the goofiest I've seen — `[Hacker News · 1872 pts]`
<https://www.0xsid.com/blog/meta-account-takeover-fiasco>

A security researcher walks through a Meta account-takeover chain that, at one point, requires guessing a six-digit code by hand. The detailed writeup is the highest-rated HN post of the day with good reason — it's both a great teardown of Meta's response process and a reminder that account-takeover surfaces in 2026 are still mostly social-engineering-shaped, not cryptographic. Worth a read even if you don't work in app security.

---

## Editor's note

Today's meta-theme: **infrastructure consolidation among the AI majors**. OpenAI extending into AWS, Alphabet raising $80B for compute, and Anthropic broadening its security coalition all point to the same thing — the front-runners are spending the IPO/pre-IPO window locking in distribution and political legitimacy. For working developers, the two must-reads are **#2 Stanford CS336** if you want to understand what's actually under the hood, and **#3 Rolldown 1.0** if you ship JavaScript for a living.

Zenn trending HTML was not fetchable today; substitutes drawn from Publickey and HN.
