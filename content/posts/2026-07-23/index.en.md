---
title: "July 23 · Today's 10 Dev Picks"
date: 2026-07-23T07:00:00+09:00
draft: false
tags: ["digest", "2026-07", "ai", "devtools", "performance", "architecture"]
categories: ["daily"]
summary: >-
  Today is less about a single launch and more about production-adjacent engineering: faster tokenization, HTML-native slide decks, SIMD fundamentals, WiFi sensing, architecture diagrams, and Jira becoming an entry point for AI coding agents.
---

## Today at a glance

The useful thread today is infrastructure around the work: how AI systems tokenize, how agents receive tasks, how teams keep architecture visible, and how developers avoid forgetting basic performance tools. The Chinese community sources were noisy today, so only two practical V2EX discussions made the cut. Anthropic News was reachable, but there was no sufficiently fresh developer-facing item to force into the list.

## Items

1. [Terrence Tao's ChatGPT Conversation about the Jacobian Conjecture Counterexample](https://chatgpt.com/share/6a5fdc7a-d6f8-83e8-bbea-8deb42cfed56) · Hacker News

   A public ChatGPT conversation from Terence Tao made the top of Hacker News, centered on reasoning around a possible Jacobian Conjecture counterexample. The interesting part is not a simplistic claim that AI solved mathematics. It is watching an expert use a model as an interactive reasoning surface: probing assumptions, asking for counterexamples, and testing weak spots in an argument.

2. [GigaToken: ~1000x faster Language model tokenization](https://github.com/marcelroed/gigatoken/) · Hacker News

   GigaToken claims a dramatic speedup for language model tokenization. Even if the exact benchmark needs careful reading, tokenizer cost is real in high-throughput AI systems: context splitting, billing estimates, log processing, batching, and request admission all touch it. Teams optimizing inference should measure the whole path, not just model tokens per second.

3. [Show HN: Bento - An entire PowerPoint in one HTML file](https://bento.page/slides/) · Hacker News

   Bento packages a slide editor, viewer, data, and collaboration surface into a single HTML file. The point is not that every company should abandon PowerPoint tomorrow. It is a reminder that browser-native, portable, inspectable artifacts are still underexplored for demos, training, internal docs, and sales engineering workflows.

4. [Everyone Should Know SIMD](https://mitchellh.com/writing/everyone-should-know-simd) · Hacker News

   Mitchell Hashimoto argues that SIMD should be part of every developer's performance literacy. That is a fair bar in 2026: AI workloads, parsers, compression, search, media processing, and analytics all benefit from vectorization. You do not need to write intrinsics every week to benefit from understanding memory layout, batch processing, and what your libraries are doing.

5. [ruvnet/RuView](https://github.com/ruvnet/RuView) · GitHub Trending

   RuView explores real-time spatial intelligence and presence sensing from commodity WiFi signals. It is an intriguing alternative to camera-based sensing, especially for smart spaces and industrial environments. The hard parts will be calibration, false positives, environmental drift, and explaining the privacy model to users.

6. [likec4/likec4](https://github.com/likec4/likec4) · GitHub Trending

   LikeC4 keeps C4-style architecture diagrams close to code. Architecture diagrams usually rot because they are not tied to the change process, not because teams lack drawing tools. A diagramming workflow that fits reviews and code evolution has a better chance of staying useful.

7. [大家 VibeCoding 的作品最终用起来了嘛？](https://www.v2ex.com/t/1229044) · V2EX

   This V2EX thread asks a practical question: did the things people built with vibe coding actually become tools they use? That is the right test. AI reduces the cost of starting, but deployment, data migration, permissions, error handling, and maintenance still decide whether a prototype survives.

8. [我做了一个 Kimi K3 资料导航站：K3 Nova](https://www.v2ex.com/t/1229180) · V2EX

   A Chinese community post introduces a navigation site for Kimi K3 resources. Treat it as an ecosystem signal rather than a benchmark. Model adoption depends not only on raw capability, but also on examples, deployment notes, compatibility guides, and people documenting the rough edges.

9. [Rust に書き直さなくても C 言語をメモリ安全にできる Fil-C を試した](https://zenn.dev/mattn/articles/cace8c5a00b9cc) · Zenn

   Mattn tries Fil-C as a way to improve memory safety for C code without rewriting the entire project in Rust. That makes the article useful in the wake of Bun's Rust rewrite and the broader Zig/Rust debate. For large legacy systems, incremental safety mechanisms may be more realistic than heroic rewrites.

10. [Atlassian adds Jira features for AI-generated requirements and agent task assignment](https://www.publickey1.jp/blog/26/jiraaiclaudecopilotai.html) · Publickey

    Publickey covers Atlassian's new Jira features for generating requirements, breaking down work, and assigning tasks to agents such as Claude Code and GitHub Copilot. This is the next obvious battleground: coding agents moving from IDEs into planning systems. The key questions are context quality, review ownership, audit trails, and how failed agent work gets routed back to humans.

## Editor's note

Today's 10 items break down as HN 4, GitHub Trending 2, V2EX 2, Zenn 1, and Publickey 1. Simon Willison was reachable, but the freshest technical item overlapped heavily with yesterday's OpenAI/Hugging Face coverage; Anthropic News was also reachable, but did not have a fresh developer-facing post worth forcing in. Dev Digest editor's top reads are GigaToken, Everyone Should Know SIMD, and the Jira AI workflow story.
