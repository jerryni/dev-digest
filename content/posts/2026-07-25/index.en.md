---
title: "July 25 · Today's 10 Dev Picks"
date: 2026-07-25T07:00:00+09:00
draft: false
tags: ["digest", "2026-07", "ai", "security", "postgres", "devtools"]
categories: ["daily"]
summary: >-
  Claude Opus 5 leads the day, but the practical engineering stories are broader: Postgres notifications, leaked GitHub credentials, local-first writing tools, AI gateways, and runtime migration work.
---

## Today at a glance

Today's feed is about control surfaces. Frontier models keep improving, but teams still need boring mechanisms: database primitives, secret scanning, local tooling, model gateways, runtime validation, and clear design ownership. V2EX was reachable, but its hot page did not expose parseable anonymous topic items today, so the Chinese community source is noted as unavailable.

## Items

1. [Claude Opus 5](https://www.anthropic.com/news/claude-opus-5) · Hacker News

   Claude Opus 5 dominated Hacker News today. The useful discussion is not just whether it tops a benchmark, but how stronger models change engineering process: tool permissions, audit trails, budget limits, and evals all become part of the deployment story. Treat this as a platform release, not a chatbot release.

2. [Postgres LISTEN/NOTIFY actually scales](https://www.dbos.dev/blog/postgres-listen-notify-scalability) · Hacker News

   This post argues that Postgres LISTEN/NOTIFY can scale further than many developers assume. That matters because teams often add Kafka, Redis Streams, or a managed queue before the workload needs it. LISTEN/NOTIFY will not replace a durable event bus, but for lightweight wakeups and single-database products it can remove a lot of operational weight.

3. [My security camera shipped a GitHub admin token in its login page](https://hhh.hn/hanwha-github-token/) · Hacker News

   A security camera shipped a GitHub admin token in a login page. That is a sharp reminder that secret scanning should cover built artifacts, not just commits. Frontend bundles, debug config, source maps, and release packaging all need controls, because customers see the artifact, not your clean repository policy.

4. [block/buzz](https://github.com/block/buzz) · GitHub Trending

   Buzz, from Block, describes itself as a hive mind communication platform. The interesting part is the overlap with agent collaboration: routing, shared context, consensus, and state are becoming common problems for humans and automated workers. It is early, but the direction is worth watching.

5. [Automattic/harper](https://github.com/Automattic/harper) · GitHub Trending

   Harper is an offline, privacy-first grammar checker written in Rust. That is a useful counterweight to cloud-only writing assistants, especially for code reviews, docs, and internal content. Local language tooling that is fast, embeddable, and open source has a clear place in developer workflows.

6. [Quoting Boris Cherny](https://simonwillison.net/2026/Jul/25/boris-cherny/) · Simon Willison

   Simon Willison highlights Boris Cherny's note that Opus 5 appears substantially harder to prompt-inject. This is the detail to care about if agents are touching browsers, documents, tickets, and codebases. Prompt injection resistance is no longer a research-side curiosity; it is part of the reliability budget for real automation.

7. [LiteLLM によるAI gateway を公式実装でデプロイして Claude Code で動かしてみた](https://zenn.dev/aws_japan/articles/e536274dc77a4f) · Zenn

   This Zenn post walks through deploying LiteLLM as an AI gateway and using it from Claude Code. Once teams use multiple models, the gateway becomes the control plane for keys, routing, budgets, logs, and fallback behavior. That is the right level to solve these problems, instead of scattering provider logic through every app.

8. [ソフトウェア設計は、「誰がどこまで考えるか」を決める仕事である](https://zenn.dev/kanaria007/articles/c392cbd1c1fc21) · Zenn

   This essay frames software design as deciding who thinks about what, from variable names through DDD, database boundaries, microservices, and org design. It is a clean mental model because many architecture failures are really responsibility failures. AI coding makes that sharper: teams need to decide what agents may decide and what humans still own.

9. [.NET MAUI、iOS/AndoridのランタイムがMonoからCoreCLRに更新](https://www.publickey1.jp/blog/26/net_mauiiosandoridmonocoreclrnet_11_preview_6.html) · Publickey

   Publickey covers .NET 11 Preview 6 moving .NET MAUI's iOS and Android runtime from Mono to CoreCLR. Runtime migration can affect startup, performance, debugging, dependency behavior, and CI. If you ship .NET MAUI apps, this is the kind of preview change to test before it becomes your production surprise.

10. [Introducing Claude Opus 5](https://www.anthropic.com/news/claude-opus-5) · Anthropic

    Anthropic's official release post lays out Opus 5's improvements in reasoning, coding, long-running work, and safety. Read it alongside the Hacker News thread and Simon Willison's security-focused note. The release is a useful input for model evaluation, procurement, and agent-risk planning.

## Editor's note

Today's 10 picks break down as HN 3, GitHub Trending 2, Simon Willison 1, Zenn 2, Publickey 1, Anthropic 1, and V2EX 0. V2EX was reachable, but the hot page did not return parseable anonymous topic entries, so that source is marked unavailable today. Dev Digest editor's must-reads are Postgres LISTEN/NOTIFY, the leaked GitHub token incident, and the Opus 5 prompt-injection note.
