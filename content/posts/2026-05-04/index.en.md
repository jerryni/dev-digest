---
title: "May 4 · Today's 10 Dev Picks"
date: 2026-05-04T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "OpenAI", "GitHub", "Bun", "Edge"]
categories: ["daily"]
summary: "GameStop bids $55.5B for eBay, Microsoft Edge keeps all passwords in process memory in plain text, an 'I'm worried about Bun' post lands the same week as the Zig→Rust commit, OpenAI walks through low-latency voice infra, GitHub has another incident, and the EU mandates removable phone batteries from 2027."
---

## Today at a glance

A weirdly classic HN day. The marquee story is GameStop bidding $55.5B for eBay (yes, real). Right behind: Microsoft Edge holding every saved password in plain text in process memory regardless of usage; a thoughtful "I'm worried about Bun" post landing in the same week as the Zig→Rust commit; OpenAI publishing an unusually concrete piece on low-latency voice infrastructure. GitHub had another outage. The EU finalized 2027 removable-battery mandates. Read #4 for engineering value, #2 + #3 for governance-of-software value.

---

## 1. GameStop makes $55.5B takeover offer for eBay

Tag: [EN · HN Top]
Link: <https://www.bbc.co.uk/news/articles/cn0p8yled1do>

Not a joke. Stock-heavy bid, lopsided enterprise values, and HN comments split between earnest valuation analysis and Spirit-Air-style memes. If it closes, it's the biggest secondhand-commerce reshuffle in a decade.

## 2. Microsoft Edge keeps all saved passwords in process memory in plain text

Tag: [EN · HN Top]
Link: <https://twitter.com/L1v1ng0ffTh3L4N/status/2051308329880719730>

Security researcher's finding: Edge holds passwords in process memory in plaintext even when no login UI is active. Any malware that can read the process memory can scrape credentials. If your IT department defaults users to Edge, this is a Slack-channel-now item.

## 3. I am worried about Bun

Tag: [EN · HN Top]
Link: <https://wwj.dev/posts/i-am-worried-about-bun/>

A long-time Bun user lays out concerns: erratic releases, slow issue triage, unclear commercialization. Lands the same week as the Zig→Rust core port. Doesn't kill Bun as an option; does change the diligence required if you're pushing it into production.

## 4. How OpenAI delivers low-latency voice AI at scale

Tag: [EN · HN]
Link: <https://openai.com/index/delivering-low-latency-voice-ai-at-scale/>

A surprisingly engineering-deep post by OpenAI standards. Network, model, and streaming changes that get end-to-end latency into the "this feels natural" range. If you're building real-time voice — contact center, automotive, telephony — this is the reference target you should be benchmarking against.

## 5. GitHub Issues / Webhooks incident

Tag: [EN · HN]
Link: <https://www.githubstatus.com/incidents/72q3n8yxthcy>

Another day, another incident. Read alongside the popular "Days without GitHub incidents" meme site (also on the front page today). The compounding question: how many days of CI/CD impact has your team absorbed in 2026 alone?

## 6. EU mandates removable smartphone batteries from 2027

Tag: [EN · HN]
Link: <https://www.ecopv-eu.com/en/blog-en/replaceable-smartphone-batteries-2027-eu-regulation/>

Final regulation: user-replaceable batteries required for phones sold in the EU starting 2027. Manufacturer chassis design changes, third-party battery market opens up, repair industry wins. If you build hardware sold into the EU, scoping work for this should already be on the roadmap.

## 7. Agent Skills

Tag: [EN · HN]
Link: <https://addyosmani.com/blog/agent-skills/>

Addy Osmani on how Claude, Cursor, Cline, and others abstract "skills" as loadable, callable units. Useful synthesis if you're designing your own agent platform — the patterns are converging fast.

## 8. CARA 2.0 — solo-built quadruped robot

Tag: [EN · HN]
Link: <https://www.aaedmusa.com/projects/cara2>

Engineering blog. An individual builder iterates on a homemade quadruped: better joints, more stable gait, lower BoM. Not Unitree-cheap, but the design genuinely is reproducible by a determined hobbyist.

## 9. Trademark violation: fake Notepad++ for Mac

Tag: [EN · HN]
Link: <https://notepad-plus-plus.org/news/npp-trademark-infringement/>

A counterfeit Notepad++ landed on the Mac App Store; the original maintainer is asking Apple to act. The structural problem — Apple's review surface area for trademark protection of OSS projects — keeps recurring.

## 10. Removable batteries today, the rest of right-to-repair tomorrow

Tag: [EN · HN]
Link: <https://www.ecopv-eu.com/en/blog-en/replaceable-smartphone-batteries-2027-eu-regulation/>

Same EU regulation as #6 but worth flagging that this is one piece of a larger right-to-repair push — battery first, then displays, then OS-level lockouts. If you ship hardware-attached software, expect more of these compliance vectors over the next 24 months.

---

## Editor's note

The two pieces of practical engineering signal: #4 (OpenAI's voice infra walkthrough) and the security finding in #2. The platform-trust read is #3 + the Bun port commit from yesterday — they're the same essay split across two outlets.
