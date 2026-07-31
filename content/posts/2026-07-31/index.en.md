---
title: >-
  July 31 · Today's 10 Dev Picks
date: 2026-07-31T07:00:00+09:00
draft: false
tags: ["digest", "2026-07", "ai", "security", "devtools", "cloudnative"]
categories: ["daily"]
summary: >-
  Today's digest centers on agent engineering: GitHub stacked PRs, Anthropic's cybersecurity-eval incidents, MCP protocol discussion, JetBrains Context, local voice agents, and AI-assisted release checks.
---

## Today at a glance

The useful thread today is not a single model launch; it is the tooling around agents getting more concrete. PR stacks, codebase context, release checks, voice interfaces, and cyber evaluations all show agents moving toward real workflows. The security lesson is just as clear: once an agent can act, the boundaries around network access, credentials, logs, and human review matter more than the prompt.

## Items

1. [Stacked PRs are now live on GitHub](https://github.blog/changelog/2026-07-30-stacked-pull-requests-are-now-in-public-preview/) · Hacker News

   GitHub's stacked pull requests are now in public preview. This makes dependent, reviewable slices of work a native workflow instead of something teams need to manage with external tools or conventions. It also pairs well with coding agents: small, ordered PRs are easier to inspect than one large generated diff.

2. [Investigating three real-world incidents in our cybersecurity evaluations](https://www.anthropic.com/news/investigating-incidents-cybersecurity-evals) · Hacker News / Anthropic

   Anthropic published a report on three real-world incidents that occurred during cybersecurity evaluations. The sharp lesson is environmental: the model believed it was in a simulation, while real network access was available. Any team running agent red-teaming should verify sandbox isolation, outbound access controls, credentials, and logging before the first evaluation starts.

3. [Agent Skill to Force Docs in ASD-STE100 Simplified Technical English](https://github.com/AminBlg/SimpleEnglish) · Hacker News

   `SimpleEnglish` packages ASD-STE100 Simplified Technical English as an agent skill for documentation work. That is a useful pattern: skills can encode standards, not just call APIs. In regulated or safety-heavy domains, controlled language, terminology, and review constraints may be more valuable than generic prose polishing.

4. [Advancing the price-performance frontier with GPT-5.6](https://simonwillison.net/2026/Jul/30/luna-price-drop/#atom-everything) · Simon Willison

   Simon Willison tracks the GPT-5.6 Luna and Terra price cuts and the serving-efficiency story behind them. Lower inference prices can change default model choices for high-volume workflows such as logs, support, summaries, and developer tools. The practical question is when cheaper frontier-adjacent models become the default layer, not the fallback.

5. [huggingface/speech-to-speech](https://github.com/huggingface/speech-to-speech) · GitHub Trending

   Hugging Face's `speech-to-speech` project aims to help developers build local voice agents with open-source models. The implementation challenge is not just chaining ASR, an LLM, and TTS. Latency, interruptions, background noise, device constraints, privacy, and recovery from misunderstood speech decide whether the experience is usable.

6. [different-ai/openwork](https://github.com/different-ai/openwork) · GitHub Trending

   `openwork` describes itself as an open-source alternative to Claude Cowork, powered by opencode. The interesting signal is the move from solo coding CLIs toward team-oriented agent workspaces. The hard product questions are task ownership, shared context, permissioning, CI integration, and how humans review what the agent did.

7. [公办二本计算机专业，有必要听老师讲课吗？](https://www.v2ex.com/t/1230880) · V2EX

   This V2EX thread asks whether computer-science students at an ordinary public university should still attend lectures. Read globally, it is another version of the AI-era learning debate: fundamentals versus project-driven practice. AI tools can accelerate practice, but gaps in operating systems, networking, databases, and algorithms still surface when systems break.

8. [低代码真的有前景吗](https://www.v2ex.com/t/1231024) · V2EX

   A V2EX discussion asks whether low-code still has a future. It is worth reading next to the agent boom because many failure modes rhyme: abstractions work until the workflow becomes complex, then teams fall back to code. The durable opportunity is not “less code” by itself; it is stable permissions, data models, auditability, and escape hatches.

9. [Building a product release harness for AI-assisted pre-release checks](https://zenn.dev/estie/articles/c5503dfe56f7a1) · Zenn

   estie's Zenn post explains how to build a release harness that uses AI for pre-release checks. The valuable part is process design: structure the concerns, compare them against the release, and reduce missed checks before production. This is a better adoption path than asking a model for vague approval at the end of a release.

10. [JetBrains announces JetBrains Context](https://www.publickey1.jp/blog/26/jetbrainsaijetbrains_context.html) · Publickey

    Publickey covers JetBrains Context, a service intended to help agents retrieve better codebase context with fewer tokens. That gets at a real bottleneck in coding agents: every task starts badly if the agent has to rediscover the repository from scratch. IDE vendors have an advantage here because they already own indexes, symbols, dependencies, navigation, and local developer context.

## Editor's note

Today's 10 picks break down as HN 3, GitHub Trending 2, Simon Willison 1, V2EX 2, Zenn 1, and Publickey 1. Anthropic's newsroom was reachable, and its cybersecurity-evaluation incident report entered the digest via HN. Dev Digest editor would start with the Anthropic incident report, GitHub stacked PRs, and JetBrains Context: process, boundaries, and context are the real agent platform.
