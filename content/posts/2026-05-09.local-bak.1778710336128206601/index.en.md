---
title: "May 9 · Today's 10 Dev Picks"
date: 2026-05-09T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Claude", "Bun", "AWS", "privacy", "Anthropic"]
categories: ["daily"]
summary: "Google quietly broke reCAPTCHA for de-googled Android, a viral 'I went back to AWS' postmortem hits 732 points, Bun's Rust rewrite crosses 99.8% test compat, Timothy Gowers walks through using ChatGPT 5.5 Pro on real math, and the EU calls VPNs a loophole to be closed. Plus Simon Willison's piece on the WebRTC voice-AI problem and a fresh io_uring zcrx LPE."
---

## Today at a glance

The thread today is about platforms reasserting control. Google broke reCAPTCHA on de-googled Android (intent unclear, effect very clear), the EU is calling VPNs a regulatory loophole that needs closing, and Meta shut down end-to-end encryption for Instagram DMs. Counterweight: a viral postmortem about leaving and returning to AWS that landed on every engineering Slack today. If you only have time for three, read items 1, 4 and 7.

---

## 1. Google broke reCAPTCHA for de-googled Android users

Tag: [EN · HN Top]
Link: <https://reclaimthenet.org/google-broke-recaptcha-for-de-googled-android-users>

1520 points and counting. A change pushed to reCAPTCHA's challenge logic now treats CalyxOS, GrapheneOS and similar de-googled Android forks as suspicious, gating their users behind unsolvable image puzzles on a large fraction of the open web. There's no clear evidence of explicit intent, but the effect is that you can't reasonably use the open web without Google Mobile Services. Pair with item 8 below — between this and EU age-gating, the cost of "exiting" Google's mobile stack is being raised, brick by brick, this quarter.

## 2. I returned to AWS and was reminded why I left

Tag: [EN · HN Top]
Link: <http://fourlightyears.blogspot.com/2026/05/i-returned-to-aws-and-was-reminded-hard.html>

732 points. The author left AWS for a smaller-cloud provider, then was forced back by an enterprise customer, and wrote the most-quoted ops postmortem of the week. Specific grievances: IAM as a moat, console-vs-API drift, multi-account organisation overhead, and the bill engineering becoming a full role of its own. The piece doesn't argue AWS is bad — it argues that the per-engineer cognitive overhead of running on it is structural, not skill-based, and that's the thing nobody costs into the migration decision.

## 3. Bun's experimental Rust rewrite hits 99.8% test compatibility

Tag: [EN · HN Top]
Link: <https://twitter.com/jarredsumner/status/2053047748191232310>

691 points. Jarred Sumner posted that Bun's in-progress port from Zig to Rust is now passing 99.8% of the existing test suite on Linux x64 glibc — a much faster ramp than most expected. The HN comments are mostly about why (long answer: easier to attract contributors, better stdlib for systems work, mature tooling). The interesting structural read is that this is one of the higher-profile Zig→Rust migrations to date and may set a precedent for new-language projects that hit the contributor-recruitment wall.

## 4. A recent experience with ChatGPT 5.5 Pro (Timothy Gowers)

Tag: [EN · HN Top]
Link: <https://gowers.wordpress.com/2026/05/08/a-recent-experience-with-chatgpt-5-5-pro/>

689 points. Fields Medalist Timothy Gowers walks through a session where he used ChatGPT 5.5 Pro on real research-grade mathematics. The post is careful and specific: where the model helped, where it made plausible-but-wrong claims, where its proof sketches needed surgical editing. Gowers' takeaway, paraphrased: it's no longer a toy for serious mathematicians, but it doesn't replace the work of verifying. The clearest counter-example to "AI plateaued" you'll read this month.

## 5. Simon Willison: WebRTC is the problem for voice AI

Tag: [EN · Simon Willison]
Link: <https://simonwillison.net/2026/May/9/luke-curley/>

Simon highlights Luke Curley's post arguing that WebRTC is structurally wrong for LLM voice interfaces: it aggressively drops audio packets to preserve real-time latency, which makes sense for a Zoom call but is exactly wrong for a slow-token-rate generative response where you'd rather wait 200ms than get a corrupted prompt. Curley's other point — "it is impossible to retransmit a WebRTC audio packet within a browser" — is the kind of plumbing detail nobody mentions in OpenAI's voice-AI press materials.

## 6. Using Claude Code: The unreasonable effectiveness of HTML

Tag: [EN · HN]
Link: <https://twitter.com/trq212/status/2052809885763747935>

513 points. Thariq Shihipar (on the Claude Code team) makes the argument that HTML, not Markdown, is the right output format to request from Claude for explanation tasks. The cost — extra tokens — used to matter; with 1M+ context windows it doesn't. The win — Claude can drop in SVG diagrams, color-coded annotations, inline interactive widgets — is large. Simon Willison's commentary on the post (item 5 above's neighbour on his blog) is also worth reading. If you've been defaulting to "respond in Markdown" since the GPT-4 days, the calculus has changed.

## 7. EU Parliamentary Research Service: VPNs are "a loophole that needs closing"

Tag: [EN · HN Top]
Link: <https://cyberinsider.com/eu-calls-vpns-a-loophole-that-needs-closing-in-age-verification-push/>

635 points. An EU Parliament-commissioned report frames consumer VPN usage as an obstacle to the bloc's age-verification regime and recommends regulatory action. The proposed mechanisms are vague — provider registries, mandatory logging, downstream platform obligations — but the framing matters: "loophole" reframes a privacy tool as a problem to be regulated away. Whether or not anything concrete passes, it tightens the Overton window for what counts as legitimate online anonymity.

## 8. V2EX: AI is devaluing things — at every layer

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1211027>

Short Chinese-language thread but the argument bites. The OP points out that all the artisanal effort-signals from the pre-LLM era — a polished README, a 100-commit GitHub repo, a clean blog post, a well-written PR description — are no longer legible as effort signals. Anyone can produce them in minutes. Worth pairing with item 4: the math example shows AI moving up the value chain; the V2EX thread is what that movement looks like from the bottom.

## 9. Zenn: AI agent-era DB design — Turso is rewriting the rules

Tag: [JA · Zenn]
Link: <https://zenn.dev/emuni/articles/6eef9f97f564b4>

85 likes on Zenn. A Japanese engineer at Emuni argues that agent workloads — many short-lived workers, each with their own per-task database — are exactly the use case Turso's "millions of cheap SQLite databases" architecture was designed for. The post walks through cost math (Turso: cents/month per agent-db; Postgres-per-tenant: dollars), operational simplifications, and architectural patterns. If you're building multi-tenant agent systems, this is the architectural posture worth comparing your current Postgres-per-tenant setup against.

## 10. You gave me a u32. I gave you root. (io_uring ZCRX freelist LPE)

Tag: [EN · HN]
Link: <https://ze3tar.github.io/post-zcrx.html>

213 points. Fresh local privilege escalation in Linux's io_uring zero-copy receive path, walked through with the kind of detail you'd want for both teaching and defense. The bug is a freelist mismanagement that an unprivileged user can trigger from a single u32 of attacker-controlled input. io_uring's security track record continues to be the operational nightmare that the hot-path performance wins are supposed to justify. If you run a hardened multi-tenant Linux fleet, this is your "patch fast" alert for the day.

---

## Editor's note

The meta-theme is platform power tightening — Google on Android, the EU on VPNs, Meta on Instagram DMs — punctuated by one viral piece of nostalgia for being able to leave AWS without coming back. Items 1 and 7 together are the regulatory story; items 3 and 4 together are the technical-progress story. Read item 2 if you have a multi-cloud decision in front of you, and read item 4 if you've been arguing AI plateaued — Gowers' post is the most thoughtful counter-evidence you'll see this month.
