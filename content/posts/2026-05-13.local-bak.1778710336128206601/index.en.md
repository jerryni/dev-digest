---
title: "May 13 · Today's 10 Dev Picks"
date: 2026-05-13T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "browsers", "standards", "supply-chain", "Claude", "AWS", "design"]
categories: ["daily"]
summary: "LinkedIn probes 6,278 browser extensions and ships the encrypted result on every request — 299 points on HN. Mozilla files a formal 'opposed' on Chrome's Prompt API push, opening the browser-AI standards war in earnest. Simon Willison reads GitLab's Act 2 layoff post as the SaaS survival script for the agentic era. Zenn's #1 today asks why some engineers viscerally hate software design principles. Publickey reports Claude Platform on AWS shipping GA. V2EX has parallel threads on the explosion of AI API resellers and on AI coding being more exhausting than writing it yourself. Plus CopyFail not getting disclosed to Gentoo, a 400-line shell coding-agent harness, and a Game Boy emulator in F#."
---

## Today at a glance

If yesterday's thread was the cost of single-vendor agent dependence, today's is what happens **once the agent leaves the IDE**. The new friction surfaces are the browser (LinkedIn's extension probe, Mozilla vs Chrome on Prompt API), the org chart (GitLab Act 2, the Zenn piece on engineers who reject design principles), and the upstream cloud (Claude Platform on AWS). The two V2EX threads are the field reports — Chinese devs are noticing that the time agents save in keystrokes shows up later as audit fatigue and reseller risk. If you read three, make it 1, 3, and 6 — they're the cleanest cross-sections of the day.

## 1. LinkedIn probes 6,278 browser extensions and ships the encrypted hit list on every request

Tag: [EN · HN Top]
Link: <https://news.ycombinator.com/item?id=47967262>

299 points. 404privacy's writeup: LinkedIn's web client actively enumerates a list of 6,278 Chrome extension IDs — including ad blockers, privacy tools, and automation clients — and attaches an encrypted hit map to every backend request. The HN thread quickly converges on the obvious questions: which team signed this off, why is it not in bug-bounty scope, and how does it survive GDPR / DSA scrutiny. The broader signal for engineering leaders: in 2026, "we passively observe what extensions are installed" is no longer a grey zone — it's the kind of telemetry that ends up cited in regulatory orders. Audit your own frontend instrumentation today.

## 2. Mozilla files "opposed" on Chrome's Prompt API standardization push

Tag: [EN · HN Top]
Link: <https://news.ycombinator.com/item?id=47959463>

564 points. Mozilla's standards-positions repo now formally records `opposed` on Chrome's proposal to standardize `window.ai` (page-level access to a built-in local LLM). Mozilla's argument is that Chrome would unilaterally define the shape of in-browser AI and lock smaller vendors out. This is the AI-era rerun of the WebUSB / WebSerial fights — whoever defines the surface first gets to define the SDK era. If you ship Chrome extensions or embed an agent in a web product, the 18-month compatibility risk on `window.ai` just got more concrete: assume Firefox/Safari will not implement it, and design accordingly.

## 3. Simon Willison reads GitLab's Act 2 — the SaaS survival script for the agentic era

Tag: [EN · Simon Willison]
Link: <https://simonwillison.net/2026/May/11/gitlab-act-2/>

GitLab announced a sweeping restructure: cutting headcount in up-to-30% of its small-team countries, removing up to three management layers in some functions, re-org'ing R&D into ~60 small end-to-end teams, and retiring its CREDIT values framework (the one with the explicit D&I bullet). Their own framing is Jevons-paradox: "the agentic era multiplies demand for software." Simon's read is sober: GitLab's stock is down from ~$52 to ~$26 in a year, so their incentive to believe in the optimistic story is structural. Useful read for anyone running a developer-tools or DevOps SaaS — the same memo will land on your desk soon.

## 4. V2EX: AI API resellers ("中转站") have multiplied in the last two weeks

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1212033>

A thread from zfyime on the Chinese developer forum V2EX, capturing a real shift: the Codex / Claude / Gemini reseller ecosystem went from a steady trickle to a flood after GPT-5.5 and Opus 4.7's pricing tier changes. The replies split between "this is real arbitrage on the new price ladders" and "this is the final KYC-light cash-grab before regulators step in." Either way, the operational lesson is the same — if your team is on a reseller for cost reasons, today is a good day to check whether your prompts are getting un-redacted into training pipelines you didn't agree to.

## 5. V2EX: AI coding is more tiring than writing it yourself

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1212128>

midsolo's thread names a frustration a lot of teams have hit but haven't put words to: agents reduced the typing, but moved the attention budget into "reviewing the PR and rolling back confident-but-wrong outputs." The replies converge on three observations — (1) reviewing prompt output is a different fatigue mode than reviewing human code, (2) agents silently re-introduce errors around the 20k-token mark when context starts to slip, and (3) the time you "saved" shows up later as maintenance. Reads like the China-side dispatch from the same ecosystem as yesterday's bug-reintroduction thread.

## 6. Zenn's #1 today: why some engineers viscerally reject software design principles

Tag: [JA · Zenn trending]
Link: <https://zenn.dev/torao/articles/20260502-differences-in-engrs-cognitive-strategies>

Takami Torao's 21,000-character essay sits at the top of Zenn's trending list (289 likes). Thesis: engineers differ in how they ingest abstract rules — some run a top-down model and accept principles deductively, others build understanding inductively from examples. The latter group physically dislikes the canonical "here is the SOLID/DDD principle, here is the example" structure because it interrupts their processing path. The practical takeaway for principal engineers: before you mandate a "best practice," figure out which cognitive style your audience runs, and reorder your delivery. Cheap to do, expensive to skip.

## 7. Publickey: Claude Platform on AWS hits GA

Tag: [JA · Publickey]
Link: <https://www.publickey1.jp/blog/26/anthropicawsclaude_platform_on_awsclaudeaws.html>

Anthropic and AWS announced general availability of "Claude Platform on AWS" — Anthropic's own platform (Skills, Routines, Cowork, and the latest feature surface) running on AWS infrastructure. This is distinct from Claude-as-a-model in Bedrock, which continues to exist. Read alongside last week's Colossus-1 lease, Anthropic spent a single week locking in a serious multi-cloud / multi-power-source posture. For procurement: the "just use Claude through Bedrock" shortcut from 2024 needs a fresh look, because the feature parity story has flipped.

## 8. CopyFail wasn't disclosed to Gentoo

Tag: [EN · HN Top]
Link: <https://news.ycombinator.com/item?id=47965108>

312 points. The openwall post-mortem: last week's CopyFail Linux privilege-escalation chain went through a coordinated-disclosure cycle that skipped Gentoo's security contact, leaving Gentoo users unwarned through the 0-day window. A follow-up by dustri on Forgejo / Codeberg documents the same omission. The interesting structural problem here isn't malice — it's that the implicit list of "who has to be told" has drifted, and small distros and forges keep falling off. If you run infra on anything outside the top-5 distros, check whether you're on the upstream notification lists you assume you're on.

## 9. Show HN: Pu.sh — a complete coding-agent harness in 400 lines of shell

Tag: [EN · HN Top]
Link: <https://news.ycombinator.com/item?id=47968112>

nahimn shipped a Bash-only coding agent that calls OpenAI / Anthropic APIs, handles tool calls, retries, and stdin piping. The thread's most interesting question, in the year of Cursor and Claude Code: how thick does the agent layer actually need to be? Answer here, with caveats: thinner than the IDEs imply, if you're willing to give up the UI affordances. Useful as a CI-side scripting starter for teams that don't want an Electron app driving their pipeline.

## 10. A Game Boy emulator written in F#

Tag: [EN · HN Top]
Link: <https://news.ycombinator.com/item?id=47965503>

Nick Kossolapov's writeup, 176 points. The interesting parts aren't "can you write an emulator in F#" — it's the concrete patterns for cycle-accurate simulation in a functional language: opcode dispatch via pattern matching, mutable state contained at the right layer, memory-mapped I/O and interrupts in a tagged-union style, and benchmarks showing .NET's SIMD is fast enough for the target. The pleasant read of the day for anyone who's tired of agent-layer arguments.

---

## Editor's note

Today's meta-theme is **what breaks first when agents leave the IDE**. Items 1 and 2 are the browser front. Items 3 and 6 are the cultural and organizational aftershocks. Item 7 is the upstream consolidation. Items 4, 5, and 8 are the operational tell — the time agents save shows up as audit work, reseller risk, and disclosure gaps. If you only read three, make it 1, 3, and 6. If you want to enjoy yourself, item 10.
