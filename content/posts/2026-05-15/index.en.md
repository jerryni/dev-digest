---
title: "May 15 · Today's 10 Dev Picks"
date: 2026-05-15T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "Claude", "VSCode", "Bun", "Node.js", "Mojo", "Nginx", "Skills", "security"]
categories: ["daily"]
summary: "Three threads this morning. (1) The platform layer is paying down years of debt at once: VS Code 1.108 ships a preview 'Agent window' for running multiple coding agents side-by-side, the long-running Bun rewrite-in-Rust PR finally lands on main, Node.js 26 turns on Temporal by default, and Mojo 1.0 hits Beta. (2) Security and privacy are pushing back hard: HN's #1 story (442 pts) is an owner physically removing the DCM and GPS from a 2024 RAV4 hybrid, #2 is a public stack-overflow PoC against Nginx, and the V2EX thread of the day is a manager discovering coworkers resold the company's LLM gateway key. (3) Skills as an interface have a real day in the sun: obra/superpowers cracks the GitHub trending top 5, and a Zenn write-up of Claude Code vs Codex playing Othello with identical Skills (final: 56-8) is making the rounds."
---

## Today at a glance

The story under all ten items is the same one we've been tracking for weeks: AI tooling has become normal enough that the *system around it* — IDEs, runtimes, employment contracts, API keys, automotive telemetry — is being renegotiated in public, often messily. If you read two: VS Code's Agent window (#7) and the Claude-vs-Codex Othello write-up (#8). The first tells you where IDEs are heading; the second is one of the few side-by-side data points on how different frontier models actually reason inside the same Skills harness.

---

## 1. Removing the modem and GPS from my 2024 RAV4 hybrid

Tag: [EN · HN #1, 442 pts]
Link: <https://arkadiyt.com/2026/05/13/removing-the-modem-and-gps-from-my-rav4/>

A step-by-step guide to physically pulling the DCM (Data Communication Module) and GPS antenna out of a 2024 RAV4 hybrid, then terminating the relevant CAN lines with resistors so the head unit doesn't notice. HN debate split between "necessary consumer sovereignty" and "you just lost automatic crash notification — is that worth it?" The piece is worth reading less for the wrench-work than for the policy subtext: the EU Data Act is already moving toward a statutory right to disable vehicle telemetry, and the discussion in the U.S. is shifting from hobbyist to mainstream. If you build telematics SaaS, treat today as a forcing function to re-examine consent flows.

## 2. New Nginx exploit (stack overflow PoC)

Tag: [EN · HN #2, 223 pts]
Link: <https://github.com/DepthFirstDisclosures/Nginx-Rift>

`DepthFirstDisclosures/Nginx-Rift` drops a working PoC for a stack-based overflow in Nginx, triggered by a specific worker configuration plus upstream chunked encoding. F5's official advisory wasn't out at publication; HN commenters have posted interim mitigations they're running at the edge (tighter `large_client_header_buffers`, dropping chunked on specific upstream paths). If you're on OpenResty or a cloud Nginx fork, audit whether your ingress path is exposed before the patch lands.

## 3. GitHub trending #4: obra/superpowers — a Skills framework for Claude Code

Tag: [EN · GitHub Trending]
Link: <https://github.com/obra/superpowers>

Jesse Vincent's "agentic skills framework": a directory layout plus shell helpers that package domain knowledge, tool-use patterns, and cautionary rails into Skills that Claude Code can load. 1,801 stars per day this week, and the most-cited reference implementation in the Skills ecosystem. Compatible with Anthropic's spec, but with a stronger opinion on the authoring order: write the runbook in Markdown first, codify into scripts only afterward. Today's Zenn piece on Claude vs Codex Othello (#8) uses Skills authored in this style. If your team is starting an internal "how we work with AI" playbook, the layout alone is worth borrowing.

## 4. Mojo 1.0 hits Beta

Tag: [Wildcard · Modular via Publickey]
Link: <https://www.modular.com/blog/mojo-10-beta>

Modular's Mojo — the Python-shaped, MLIR-backed language Chris Lattner has been working on — reaches 1.0 Beta. Beta means the language spec is effectively frozen; the next few months are about stdlib and the package manager. The pitch, unchanged, is that you can write Python-grade ergonomics and have it lower to the same MLIR pipeline that targets GPUs, TPUs, and exotic accelerators. For teams building inference infra, this is the rare candidate that could compress custom-kernel work by an order of magnitude. Worth a couple of hours this week on the SIMD/vectorization primitives — even just to inform PyTorch 2026 planning.

## 5. Bun's Rust rewrite PR has merged to main

Tag: [ZH source · V2EX / Bun upstream]
Link: <https://www.v2ex.com/t/1212789>

Bun was originally written in Zig. Earlier this year the team announced a gradual migration to Rust — partly because Zig's toolchain maturity has been a tax on enterprise contributors. The PR that landed today swaps the core native bindings to a Rust runtime; tests are green. Two strands of debate in the V2EX thread: (a) Zig was one of Bun's differentiators; converging on Rust like Deno and Node may dull the character. (b) Several long-standing npm-compat bugs were *not* tackled in this PR, which disappoints the part of the community most invested in production use. If your monorepo tooling has bet on Bun, this is a good day to refresh your risk register.

## 6. Coworkers quietly resold the company's LLM API key

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1212742>

A team lead in China posts that the company's annual-contract Claude/OpenAI gateway key was being shared by a coworker with "a few friends," and the monthly usage blew past projection. The comment thread quickly turns operational: per-user keys with audit logs, never share master tokens at the team level, and — pointedly — in several jurisdictions this kind of conduct can rise to misappropriation rather than mere policy violation. For any organization running LLMs in production today: the three-point control set is (1) per-developer keys, (2) automatic rotation, (3) per-user usage ceilings. If you don't have all three, this thread is your business case.

## 7. VS Code 1.108: "Agent window" preview for running multiple AI agents in parallel

Tag: [JA source · Publickey / VS Code release notes]
Link: <https://www.publickey1.jp/blog/26/vs_codeaiagent_window.html>

VS Code 1.108 (May 13) ships an "Agent window" preview: a new window class designed to host multiple coding agents side-by-side. You can run Copilot, Claude Code, Codex, and a local model against the same workspace, each with its own conversation pane and a separate staged-diff buffer, then compare and merge selectively. This is Microsoft's answer to Boris Mann's quip (which Simon Willison surfaced yesterday) that "I have 11 AI agents" is a meaningless statement: meaning comes from the orchestration substrate, and the IDE is now choosing to be that substrate.

## 8. Same Skills, different model: Claude Code beats Codex 56-8 at Othello

Tag: [JA · Zenn]
Link: <https://zenn.dev/doai/articles/cc97075e985938>

@doai handed the same Skills bundle (Othello rules + an evaluation function) to Claude Code and Codex and watched them play. The score is the headline; the substance is the side-by-side reasoning logs. Claude tends to compute "stable disc count four moves out" before committing; Codex runs more like heuristic-plus-try-and-correct. That difference shows up downstream in larger engineering tasks — the failure modes diverge. Comparisons of how identical Skills interact with different frontier models are rare; this is a useful empirical contribution.

## 9. Anthropic and the Gates Foundation: $200M, five years, global health

Tag: [Wildcard · Anthropic]
Link: <https://www.anthropic.com/news/gates-foundation-partnership>

Anthropic and the Bill & Melinda Gates Foundation announced a five-year, $200M partnership focused on infectious-disease surveillance, primary-care decision support, and health-data stewardship in low- and middle-income countries. About half flows as Anthropic API credits plus embedded engineering; the rest as direct grants to NGOs and ministries. The strategic read: rather than out-spending OpenAI in pure enterprise, Anthropic is building a "foundation model × public-interest partnership × government procurement" triangle. Expect this deal's vendor-lock-in language to be referenced in sovereign-AI RFPs for the next two years.

## 10. Node.js 26: Temporal is on by default

Tag: [Wildcard · Publickey / Node.js release notes]
Link: <https://www.publickey1.jp/blog/26/nodejsdatetemporaltemporalchromeedgefirefoxnodejs.html>

Node.js 26 enables ECMA-402 Temporal by default, finishing the sweep (Chrome, Edge, Firefox, Node). Temporal pays off the historical debt of `Date`: it's immutable, months are 1-indexed, time-zone handling is first-class via `Temporal.ZonedDateTime`. For cross-region SaaS, the practical move this week is to add a lint rule banning `new Date()` in new code and start migrating the date-juggling hotspots. dayjs and Luxon become reach-throughs you can finally peel off.

---

## Editor's note

Two arrows pointing in different directions today: the runtime layer is finally getting around to long-overdue cleanup (Bun-on-Rust, Node Temporal, Mojo Beta, IDEs treating AI as a first-class citizen), while the human and organizational layer keeps tripping over assumptions that no longer hold (resold API keys, owners ripping out telemetry hardware, multi-agent orchestration becoming a normal workflow). If you only read two: #7 (Agent window) for what your IDE looks like next quarter, and #6 (resold keys) for what your governance doc needs to cover before next month.

*Dev Digest editor*
