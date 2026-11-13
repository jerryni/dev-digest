---
title: "November 13 · Today's 10 Dev Picks"
date: 2026-11-13T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "security", "ai", "tooling"]
categories: ["daily"]
summary: "Rust reaches 1.100, a longstanding PostgreSQL flaw gets a serious postmortem, and agent tooling keeps moving into normal engineering work."
---

# November 13 · Today's 10 Dev Picks

## Today at a glance

The through-line is operational maturity: language releases, old vulnerability classes, and agent-assisted workflows all reward teams that make boundaries explicit. The practical reads today are the Rust release notes, the PostgreSQL exploit analysis, and the test-runner updates.

## Picks

### 1. [Rust 1.100](https://blog.rust-lang.org/2026/11/12/Rust-1.100.0/)
`Hacker News · Languages`

Rust 1.100 is a satisfying milestone, but the useful question is which newly stable capabilities remove friction in your own codebase. Language upgrades should be paired with an MSRV decision, dependency audit, and CI matrix update. Treat a round number as a good time to delete local workarounds rather than as a reason to upgrade on faith.

### 2. [A 22-year-old PostgreSQL bug turned into remote code execution](https://mehmetince.net/part-3-6-how-i-ended-up-turning-a-22-year-old-postgresql-type-confusion-primitive-into-rce-cve-2026-6460/)
`Hacker News · Security`

This exploit write-up follows a type-confusion primitive in PostgreSQL to remote code execution. The deeper lesson is that mature infrastructure is not immune to old assumptions becoming dangerous under new compositions. Database patching needs asset inventory and recovery rehearsal, not just a ticket saying the version changed.

### 3. [Foundation Models framework](https://developer.apple.com/foundation-models-framework/)
`Hacker News · Platform APIs`

Apple's Foundation Models framework brings on-device model access into a first-party developer surface. That makes privacy and latency attractive defaults for some features, while also making capability and platform-version checks part of product design. Build a useful degraded path first; model access should enrich the interaction rather than gate it.

### 4. [modern-web-guidance-src](https://github.com/GoogleChrome/modern-web-guidance-src)
`GitHub Trending · Web engineering`

Google Chrome's trending guidance repository packages current web best practices for coding agents. A repo like this is most valuable when it is used as review criteria and tested against a real application, not pasted wholesale into instructions. Version the guidance you adopt so a later recommendation change is observable in your own engineering process.

### 5. [Codex Security CLI and TypeScript SDK](https://github.com/openai/codex-security)
`GitHub Trending · Application security`

OpenAI's Codex Security project is trending as tooling for finding, validating, and fixing vulnerabilities. Automated findings can shorten triage, but the validation step is the distinction between a useful signal and an expensive alert stream. Start with a bounded repository and make ownership of accepted, fixed, and rejected findings explicit.

### 6. [Microsoft 365 service degradation](https://www.v2ex.com/t/1256329)
`V2EX · Developer community`

The V2EX discussion tracks a broad Microsoft service disruption from the developer's seat. Public status pages are only the beginning of incident response: teams still need to identify their own broken workflows, fallback channels, and customer-facing impact. If a SaaS dependency is critical, practice the workday that follows when it is unavailable.

### 7. [Copying a full subscription URL on a phone can leak it](https://www.v2ex.com/t/1256332)
`V2EX · Security hygiene`

This community reminder is small but concrete: a full subscription link copied on mobile can expose credentials or access tokens. URLs are often treated as harmless text even when they are bearer credentials. Redact them in screenshots, avoid sharing them through syncable clipboards, and rotate exposed tokens rather than merely deleting the message.

### 8. [How to check whether Node.js 22, 24, or 26 vulnerabilities affect your app](https://zenn.dev/)
`Zenn · JavaScript security`

This Zenn trending guide frames Node.js vulnerability response as an impact-assessment problem, not a version-number panic. Identify the runtime actually deployed, the affected feature path, and the base image before scheduling a change. A short compatibility test is still cheaper than discovering a production break during an emergency update.

### 9. [Reducing Claude Code token use by making it forget](https://zenn.dev/)
`Zenn · AI-assisted development`

A Zenn write-up reports lower Claude Code token use after deliberately trimming remembered context. The transferable idea is that agent context is a budgeted dependency: keep durable project rules, discard stale execution detail, and retrieve evidence when it is needed. Smaller context can improve both cost and the chance that the relevant constraint is noticed.

### 10. [Playwright officially supports Bun](https://www.publickey1.jp/blog/26/playwrightbun.html)
`Publickey · Testing`

Publickey reports that Playwright 1.65.0 officially supports running its test runner on Bun. That is useful for teams already standardizing on Bun, but browser-test reliability still depends on pinned browsers, CI images, and deterministic fixtures. Measure the full suite before changing a shared pipeline; startup speed alone is not the contract.

## Editor's note

Today's strongest pairing is the PostgreSQL exploit analysis and the Node.js impact guide: both argue for evidence-driven patching instead of reactive version churn. Anthropic News was reachable but did not surface a fresh technical announcement in the collection window, so its wildcard capacity went to current engineering tooling and testing coverage.
