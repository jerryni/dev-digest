---
title: "November 14 · Today's 10 Dev Picks"
date: 2026-11-14T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "ai", "cloud", "testing", "developer-tools"]
categories: ["daily"]
summary: >-
  Today's reads are about making external systems tractable: local AWS emulation, agent isolation, executable specifications, and a more flexible browser-test runtime.
---

## Today at a glance

The useful theme today is not a new model leaderboard. It is engineering control: replacing opaque cloud dependencies with local feedback loops, isolating risky workloads, and turning requirements into tests rather than wishes.

---

### 1. Reverse-engineering a Coway purifier to leave the cloud — `[Hacker News]`
<https://scottjg.com/posts/2026-11-11-reverse-engineering-my-coway-air-purifier-to-ditch-the-cloud/>

This walkthrough reverse-engineers a Coway air purifier so it can operate without the vendor cloud. It is a sharp illustration of the mismatch between hardware lifetime and SaaS lifetime. IoT teams should treat offline behavior and exportable control surfaces as product requirements, not rescue features.

### 2. Terminal borders that do not consume a cell — `[Hacker News]`
<https://www.joshka.net/cell-borders/>

An unusually deep look at drawing borders in a terminal UI without sacrificing a character cell to them. The result matters most in narrow panes, remote shells, and dense layouts. Good CLI tools tend to win on exactly these unglamorous rendering constraints.

### 3. Live migration for FreeBSD and bhyve is moving toward RFC — `[Hacker News]`
<https://gyptazy.com/blog/freebsd-bhyve-live-migration-support-rfc/>

Live migration support for FreeBSD and bhyve is being proposed. It will not transform every deployment overnight, but it meaningfully expands the operational toolkit for self-hosted and FreeBSD-heavy estates. The key questions are rollback behavior and network state, not just whether a demo migrates.

### 4. Simon Willison flags AWS Emulator — `[Simon Willison]`
<https://simonwillison.net/2026/Nov/11/aws-emulator/>

Simon Willison notes the formal release of AWS Emulator. Local service emulation can shorten the edit-test loop and make failure paths cheaper to exercise. It is still not a substitute for real-environment validation of IAM, networking, and managed-service edges.

### 5. A Mac system monitor called Ebb asks for feedback — `[V2EX]`
<https://www.v2ex.com/t/1256714>

A developer introduces Ebb, a Mac system monitor, and asks the community to try it. Monitoring is a crowded category, yet developers still value quiet interfaces that surface the one signal that needs attention. More charts are rarely the differentiator; confidence in the reading is.

### 6. An Outlook outage disrupts cross-time-zone work — `[V2EX]`
<https://www.v2ex.com/t/1256701>

This discussion captures the immediate impact of an Outlook outage on customer meetings. Collaboration tooling is a delivery dependency, not background plumbing. Teams working across borders should keep alternate contact channels and meeting handoff procedures in their runbooks.

### 7. Testing generated code against RFC 9457 — `[Zenn]`
<https://zenn.dev/tkydev/articles/2026-11-12_rfc9457_2>

The article tests a familiar failure mode: a model may know a standard but fail to apply it while generating code. Naming an RFC in a prompt is not a compliance mechanism. Turn the requirement into assertions, contract tests, or review checks, then make the agent's output pass them.

### 8. Building an MCP server for CIMD and verifying it with CLIs — `[Zenn]`
<https://zenn.dev/aldagram_tech/articles/f734954a1a5fbb>

This implementation note builds an MCP server with CIMD support and checks it with Claude Code and Codex CLI. Cross-client verification is where permission boundaries, error behavior, and observability become concrete. For production adoption, reproducible integration tests beat a polished demo.

### 9. AWS Emulator reaches general availability — `[Publickey]`
<https://www.publickey1.jp/blog/26/awsawsaws_1.html>

Publickey's report on AWS Emulator reinforces a broader shift: cloud vendors are treating local emulation as a first-class developer experience. It can accelerate CI and catch configuration mistakes early. Keep a real-cloud gate, though, because authorization and managed-service semantics remain the final authority.

### 10. Playwright officially supports Bun — `[Publickey]`
<https://www.publickey1.jp/blog/26/playwrightbun.html>

Playwright now officially supports running its test runner with Bun. Teams already using Bun can bring browser tests into a more uniform toolchain. Start with one representative E2E path in CI before switching the entire suite; fixture behavior and parallelism are where compatibility claims get tested.

## Editor's note

Today's distribution is four English items from Hacker News and Simon Willison, two Chinese-community items from V2EX, and four Japanese items from Zenn and Publickey. GitHub Trending was reachable but yielded no selected item; Anthropic News had no suitable engineering post from the last 24 hours. Start with AWS Emulator, the RFC 9457 validation piece, and Playwright on Bun.
