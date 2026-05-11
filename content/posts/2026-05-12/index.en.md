---
title: "May 12 · Today's 10 Dev Picks"
date: 2026-05-12T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Claude", "security", "supply-chain", "Rust", "SQLite", "privacy"]
categories: ["daily"]
summary: "Claude Code is reportedly refusing requests or up-charging when commits mention 'OpenClaw' — 865 points on HN and counting. Shai-Hulud lands in PyTorch Lightning. Simon Willison digs into Anthropic's Colossus-1 lease and the new 'Elon can yank the compute' supply-chain risk. Bun migrates from Zig to Rust in a week with Claude. Zed 1.0 ships. V2EX has the bug-reintroduction complaint we've all been thinking. Plus Rivian's hard-off privacy switch, durable queues inside SQLite, and Daniel Lemire on beating binary search."
---

## Today at a glance

Today's thread is the cost of single-vendor agent dependence. The Claude Code "OpenClaw" story (item 1), the V2EX bug-reintroduction complaint (item 5), and the Colossus-as-supply-chain-risk piece (item 3) are all variants of the same question: when your stack is one vendor's agent + one cloud provider's compute, how much of your roadmap is hostage to a policy decision you don't get to see? On the optimistic side, Bun finished a one-week Claude-driven Zig-to-Rust migration (item 6) and Zed shipped 1.0 (item 7) — the AI-native systems-language reset is happening for real. If you only read three: items 1, 3, and 5.

---

## 1. Claude Code refuses requests when your commits mention "OpenClaw"

Tag: [EN · HN Top]
Link: <https://news.ycombinator.com/item?id=47963204>

865 points and 497 comments — the runaway top story today. Theo's report is that Claude Code will refuse requests, or in some cases up-charge, when the repository's commit messages or files reference "OpenClaw" (a competing open-source coding agent). The thread is split between "obvious safety/abuse heuristic gone wrong" and "this looks deliberate and the longer Anthropic stays silent the worse it looks." Whatever the eventual explanation, the lesson for vendor-management is the same: an opaque server-side policy can downgrade your tool at any moment, and you won't get a changelog entry when it happens.

## 2. Shai-Hulud-themed malware found in PyTorch Lightning

Tag: [EN · HN Top]
Link: <https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/>

Semgrep's writeup on a malicious dependency planted in the Lightning AI training library, themed after the Shai-Hulud campaign that's been chewing through the Python ML ecosystem for six months now. The payload targets exactly the workstations with the loosest controls and the largest blast radius — GPU training boxes with cached credentials and access to private model weights. If your team trains on shared infra, this is a "audit lockfiles before lunch" item, not an afternoon-meeting item.

## 3. Notes on the xAI/Anthropic data center deal

Tag: [EN · Simon Willison]
Link: <https://simonwillison.net/2026/May/7/xai-anthropic/>

Simon's followup on the Colossus-1 lease Anthropic announced at Code w/ Claude this week. The shape of the deal: ~300MW / 220,000 NVIDIA GPUs of new capacity within the month, sourced from the data center with the country's worst air-quality record. Elon Musk's tweet attached to the deal includes the phrase "we reserve the right to reclaim the compute" if Anthropic's AI is judged to harm humanity — with the judge implicitly being Elon. New supply-chain risk category: politically conditional GPU allocation.

## 4. V2EX: Codex's new Chrome extension can drive browsers headlessly

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1211090>

JaydenTong reports OpenAI shipped a Codex Chrome extension that puppeteers Chromium-family browsers from the background. Thread is split between "this is the killer feature that finally beats Claude on browser tasks" and "great, now two coding agents fight over my session." Lands the same week as Anthropic's expansion of Claude for Chrome — so on both sides, AI-in-the-browser surface area is consolidating fast. The interesting second-order question: how long before security teams ban any browser-driving agent extension by default?

## 5. V2EX: AI writes code well, but doesn't remember the bug we fixed last week

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1211151>

huoru's thread (98 replies) names the failure mode many of us have hit without articulating: the agent will cheerfully re-introduce a bug your team patched seven days ago, because nothing in its context stitched the patch into durable memory. The replies converge on a project-level "what we fixed and why" file the agent re-reads at session start. This is exactly the gap Anthropic's Routines and Dreams (Code w/ Claude this week) are supposed to close — and exactly the gap that's still wide open in everyday Claude Code / Codex / Cursor usage.

## 6. Publickey: Bun migrates from Zig to Rust, using Claude

Tag: [JA · Publickey]
Link: <https://www.publickey1.jp/blog/26/javascriptbunclaudezigrust.html>

Jarred Sumner announced Bun — until now the highest-profile production Zig codebase — is moving to Rust, and Claude is doing nearly all of the translation work. About one week, near-complete. Two things matter: (a) it's a real, large-scale demonstration of model-driven cross-language porting at the upper end of difficulty, and (b) Zig just lost its biggest showcase project at the moment Rust is consolidating mindshare in systems work. This will compound.

## 7. Publickey: Zed 1.0 ships

Tag: [JA · Publickey]
Link: <https://www.publickey1.jp/blog/26/aized_10atomrust.html>

Zed Industries — the original Atom team rebuilding the editor from scratch in Rust — hit 1.0. Available on Windows, Mac, Linux. The pitch is that Zed treats AI agents as first-class collaborators rather than retrofitting them onto a 20-year-old VS Code model. Whether the agent ergonomics are actually better than Cursor / Claude Code / VS Code + Copilot is the open question; 1.0 is at least a real commitment to ship cross-platform.

## 8. Honker: durable queues, streams, pub/sub, cron — inside a single SQLite file

Tag: [EN · HN Top]
Link: <https://honker.dev/>

158 points on HN. Honker pitches a small library that puts a full async infra stack — queues, streams, pub/sub, scheduler — into one SQLite file, in the same "one file, zero infra" lineage as Litestream and Turso. The interesting design problem is pub/sub without polling; the project leans on WAL-based change streams. Even if you don't adopt it, the architecture writeup is the most readable explanation I've seen of where SQLite-as-infra stops being a toy.

## 9. Rivian lets you disable all internet connectivity

Tag: [EN · HN Top]
Link: <https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle>

331 points. Rivian published an official support article showing how to hard-disable all data collection on its vehicles — a meaningfully more honest posture than the implied "trust our privacy dashboard" defaults you get from most carmakers. The HN thread's comparison to Tesla, Ford, and GM is unkind to all three. If you do threat modeling for execs, journalists, or anyone whose movement patterns are a target, this is the only major US EV with a real off-switch today.

## 10. You can beat the binary search

Tag: [EN · HN Top]
Link: <https://lemire.me/blog/2026/04/27/you-can-beat-the-binary-search/>

Daniel Lemire's short writeup on how branchless / SIMD-friendly search routines beat textbook binary search on modern CPUs for small-to-medium sorted arrays. Benchmark code is on GitHub. The broader pattern is the one worth internalizing: most "fundamental" undergrad algorithms now have CPU-friendly variants that win on real hardware, and if you maintain a hot-path lookup, profiling the new generation of branchless options is worth a day.

---

## Editor's note

The meta-theme is single-vendor risk. Item 1 (OpenClaw / Claude Code) and item 3 (Colossus / Musk's conditional compute) are both versions of "the platform you depend on can change its mind without telling you." Item 5 (bug reintroduction on V2EX) is the same story from the other side: when the agent has no durable memory of your codebase, you're paying for a dependency you can't even audit. Items 6 and 7 (Bun → Rust, Zed 1.0) are the more hopeful counterpoint — AI-driven rewrites and AI-native tools are actually shipping. Must-reads if you only have ten minutes: items 1, 3, and 5.
