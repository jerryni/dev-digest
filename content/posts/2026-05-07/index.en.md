---
title: "May 7 · Today's 10 Dev Picks"
date: 2026-05-07T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Claude", "DeepSeek", "TypeScript", "AWS", "auth"]
categories: ["daily"]
summary: "Simon Willison admits vibe coding and agentic engineering are collapsing into one thing, Anthropic ships Claude Opus 4.7, DeepSeek V4 Pro is 75% off through May 31, AWS's Middle East UAE region needs months more to recover, and TypeScript 7.0 Beta lands with the Go-rewritten compiler."
---

## Today at a glance

The thread running through today's links is the boundary between writing code and orchestrating agents collapsing in real time. Read Simon Willison's latest reflection alongside HN's "The bottleneck was never the code" — they describe two halves of the same shift. On the model side, Anthropic shipped Opus 4.7 (better vision), DeepSeek slashed V4 Pro pricing to a quarter through end of May, and Google quietly buried reCAPTCHA in favor of a behavior-and-AI-based fraud platform. The hard infra story is AWS's Middle East UAE region: still months from full recovery after physical-layer damage tied to regional conflict.

---

## 1. Simon Willison: vibe coding and agentic engineering are converging

Tag: [EN · Simon Willison]
Link: <https://simonwillison.net/2026/May/6/vibe-coding-and-agentic-engineering/>

Simon has held the line for a while between vibe coding (don't read the code, judge by behavior) and agentic engineering (let an agent draft, but humans actually review). His new post concedes the toolchain has erased the practical difference. The sharpest line: once your review cadence drops below a threshold, you are vibe coding regardless of what you tell yourself. Worth sending to anyone running a coding agent rollout — it reframes "review gates" from process hygiene to product surface.

## 2. The bottleneck was never the code

Tag: [EN · HN Top]
Link: <https://www.thetypicalset.com/blog/thoughts-on-coding-agents>

Pair it with #1. Argument: writing code was never the rate limit; understanding requirements, debugging, coordination, and gathering context were. Speeding up code generation just makes the surrounding work look slower. The HN comments are unusually substantive here, with several engineers describing how their teams have hit exactly this wall: more code, no faster outcomes.

## 3. From Supabase to Clerk to Better Auth

Tag: [EN · HN Top]
Link: <https://blog.val.town/better-auth>

Val Town's two-step migration: Supabase Auth → Clerk → Better Auth (open source, self-hostable). The "why we left Clerk" section is the meat — vendor pricing scaled badly with their growth model, and the lock-in surface was wider than expected. Useful as a mid-stage reference for anyone deciding between hosted auth and rolling-your-own-on-OSS-primitives in 2026.

## 4. V2EX debate: Podman or Docker in 2026

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1208359>

The Chinese dev community is rehashing the container runtime question. Rough consensus: greenfield projects → Podman (daemonless, rootless, systemd-friendly); existing Docker setups → don't bother migrating without a forcing function. Useful sanity check if you've been hearing the same conversations on your side of the firewall.

## 5. V2EX: in 2026, Android/HarmonyOS still chokes on non-ASCII project paths

Tag: [ZH · V2EX]
Link: <https://v2ex.com/t/1204805>

Old bug, new year. Project path with Chinese characters → build failure on Android and HarmonyOS toolchains. Worth a glance not because the bug is interesting but because it's a clean demonstration of how deprioritized i18n stays at the bottom of the toolchain stack — even on platforms where the primary user base writes non-Latin scripts.

## 6. AWS Middle East (UAE) region: months more before full recovery

Tag: [JA · Publickey]
Link: <https://www.publickey1.jp/blog/26/awsuae2.html>

ME-CENTRAL-1 took physical-layer damage from regional conflict; AWS broke a two-month silence to say full restoration is still months away. This is genuinely unprecedented in scale and duration for a hyperscaler. If you're running production in UAE, the realistic options are now ME-SOUTH-1 (Bahrain) or EU-WEST-1 — and your DR runbook needs updating, not next quarter, this week.

## 7. TypeScript 7.0 Beta: Go-rewritten compiler, 10x faster

Tag: [JA · Publickey]
Link: <https://www.publickey1.jp/blog/26/typescript_70typescriptgo10.html>

Microsoft's Go port of the TS compiler is now in 7.0 Beta. Reported 10x improvement on multi-million-line codebases. If your monorepo CI spends double-digit minutes on type-checking, this is the upgrade to plan for. Note: 7.0 is the first major on the native compiler, so expect 5.x to enter maintenance soon.

## 8. Claude Opus 4.7

Tag: [EN · Anthropic]
Link: <https://www.anthropic.com/news/claude-opus-4-7>

Anthropic shipped Opus 4.7 on May 4. Headline change is vision: higher-resolution image understanding, which in practice means better screenshot debugging, UI automation, and document parsing. Pricing unchanged from 4.6 ($5/M input, $25/M output). Anthropic also confirmed an expanded compute partnership with SpaceX.

## 9. DeepSeek V4 Pro: 75% off through May 31

Tag: [EN · HN]
Link: <https://api-docs.deepseek.com/quick_start/pricing>

A quarter of normal pricing on the entire V4 Pro tier. If you've been deferring an A/B against your current provider on cost-sensitive workloads (long-context summarization, classification at scale), this is the window. Quality vs Claude/GPT-4 class models depends on your eval, but the cost delta makes the comparison easy to justify running.

## 10. Google Cloud Fraud Defense: the next reCAPTCHA

Tag: [EN · HN]
Link: <https://cloud.google.com/blog/products/identity-security/introducing-google-cloud-fraud-defense-the-next-evolution-of-recaptcha/>

reCAPTCHA quietly retired, replaced by a behavior-signals-plus-AI fraud platform positioned as a competitor to Sift, Riskified, and Stripe Radar rather than a bot-blocker widget. If your fraud stack is still anchored on reCAPTCHA v2/v3, it's worth pricing this against the vendor you'd otherwise be evaluating next quarter.

---

## Editor's note

The meta-theme is that "writing code" has stopped being the constraint. Read #1 and #2 first if you only have time for two; they're a coherent pair. The two operationally urgent items are AWS's UAE region status (#6) — escalate this with platform/SRE today — and TypeScript 7.0 Beta (#7) if your team has been hand-wringing over CI type-check times. The rest is the ongoing model-pricing-and-capability war, mostly business-as-usual now.
