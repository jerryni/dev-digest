---
title: "May 3 · Today's 10 Dev Picks"
date: 2026-05-03T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Kimi", "DeepSeek", "Mercedes", "Haskell"]
categories: ["daily"]
summary: "Kimi K2.6 beats Claude/GPT-5.5/Gemini on a coding challenge, DeepClaude pairs Claude Code's loop with DeepSeek V4 Pro, OpenAI's o1 outperforms ER doctors on triage, 'Agentic Coding Is a Trap' lands, Mercedes commits to physical buttons, and TUIs are back."
---

## Today at a glance

The throughline today is "Chinese open-weight models showing up where it matters." Kimi K2.6 beating Claude / GPT-5.5 / Gemini on a public coding challenge, paired with DeepClaude (Claude Code's loop running on DeepSeek V4 Pro at a fraction of the cost), is the most concrete signal yet that the cost-quality frontier for dev tooling has moved. Beside that: OpenAI's o1 outperformed ER doctors on triage in a Harvard trial — a number worth quoting in any conversation about AI in regulated verticals. The Agentic-Coding-Is-a-Trap and TUIs-are-back posts are the engineering-culture reads.

---

## 1. Kimi K2.6 beats Claude/GPT-5.5/Gemini on a coding challenge

Tag: [EN · HN Top]
Link: <https://thinkpol.ca/2026/04/30/an-open-weights-chinese-model-just-beat-claude-gpt-5-5-and-gemini-in-a-programming-challenge/>

Moonshot AI's open-weights model leads three closed frontier models on a public coding benchmark. HN comment thread (200+) mostly accepts the result. Notable because it's the clearest "Chinese open model is genuinely competitive on dev tasks" data point we've had — until now the lead was in math/reasoning benchmarks rather than coding.

## 2. DeepClaude — Claude Code's loop on DeepSeek V4 Pro

Tag: [EN · HN Top]
Link: <https://github.com/aattaran/deepclaude>

A GitHub project that swaps Claude Code's agent loop onto DeepSeek V4 Pro for a fraction of the cost. The HN thread has actual benchmark numbers from people running it. Most useful as a reproducible reference for anyone evaluating the cost/quality tradeoff for cheaper agent loops.

## 3. OpenAI o1 outperforms ER doctors on triage diagnoses (67% vs 50-55%)

Tag: [EN · HN Top]
Link: <https://www.theguardian.com/technology/2026/apr/30/ai-outperforms-doctors-in-harvard-trial-of-emergency-triage-diagnoses>

Harvard-affiliated trial. The methodological details matter — read the writeup before quoting the headline number — but this is the most important AI-in-medicine data point of the quarter. Regulatory and liability conversations will adjust around it.

## 4. Agentic Coding Is a Trap

Tag: [EN · HN Top]
Link: <https://larsfaye.com/articles/agentic-coding-is-a-trap>

The thoughtful skeptic post. Argument: today's agentic coding tools manufacture the *feeling* of engineering while review cadence drops. Pairs with Simon Willison's later May 6 reflection — together they're the engineering-culture reading list for the month.

## 5. Mercedes-Benz commits to bringing back physical buttons

Tag: [EN · HN Top]
Link: <https://www.drive.com.au/news/mercedes-benz-commits-to-bringing-back-phycial-buttons/>

Mercedes formally walked back the all-touchscreen direction; physical controls return in next-gen vehicles. 500+ HN comments. The HMI walk-back will ripple through every other manufacturer that committed too hard to glass.

## 6. Why TUIs are back

Tag: [EN · HN Top]
Link: <https://wiki.alcidesfonseca.com/blog/why-tuis-are-back/>

lazygit, k9s, helix, Claude Code, atuin — the resurgence of terminal UIs as a real product category. Argument: developers are exhausted by the browser-as-application-container assumption. Long but readable. Useful design-language reference if you're building dev tools.

## 7. A couple million lines of Haskell at Mercury

Tag: [EN · HN Top]
Link: <https://blog.haskell.org/a-couple-million-lines-of-haskell/>

Mercury runs 2M lines of Haskell in production. The post is concrete on the operational side — hiring, CI, debugging, refactoring — which is what makes it different from the usual "we love $LANG" engineering blog. Useful even if you're never going to write Haskell.

## 8. Specsmaxxing — writing specs in YAML to overcome AI psychosis

Tag: [EN · HN]
Link: <https://acai.sh/blog/specsmaxxing>

The argument: structured YAML specs are how you get reliable behavior from coding agents, not free-form prose. Comment thread is unusually substantive (295). The interesting subtext: documentation may be evolving from markdown back toward schemas as AI consumers become first-class readers.

## 9. Show HN: WhatCable — a Mac menu-bar tool to inspect USB-C cables

Tag: [EN · Show HN]
Link: <https://github.com/darrylmorley/whatcable>

Reads cable capability data the OS already has access to, surfaces it as plain English (wattage, data rate, Thunderbolt support). Open source, no tracking. Solves a real problem you've definitely had with the cable drawer.

## 10. BYOMesh — LoRa mesh radio with 100x bandwidth

Tag: [EN · HN]
Link: <https://partyon.xyz/@nullagent/116499715071759135>

Off-grid mesh communication that's actually fast enough to be useful for more than text. Niche, but if disaster comms or rural connectivity is anywhere on your roadmap, this is interesting.

---

## Editor's note

Two must-reads: #1 + #2 together (Chinese open models in dev tooling), and #3 (o1 outperforming ER doctors). Both will get cited in product and regulatory conversations for the rest of this quarter. #4 and #6 are the engineering-culture reads if you have an hour to think.
