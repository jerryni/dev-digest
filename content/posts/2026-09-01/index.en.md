---
title: "September 1 · Today's 10 Dev Picks"
date: 2026-09-01T07:00:00+09:00
draft: false
tags: ["digest", "2026-09", "ai", "developer-tools", "browser", "observability", "open-source"]
categories: ["daily"]
summary: >-
  Today's edition follows browser platform changes, compatibility-layer engineering, Python testing and tracing, agent skills, and practical database and cloud-permission notes from Japanese engineering blogs.
---

## Today at a glance

The strongest theme today is tooling becoming infrastructure. Chrome extension policy changes affect real user control, agent skills are turning into reusable engineering assets, and local or OS-level agents are pushing permission design into the foreground. The most practical reads are the Terraform plan permissions piece and the Spanner execution-plan deep dive.

---

### 1. Google removes MV2 extensions from the Chrome Web Store, including uBlock Origin — `[Hacker News]`
<https://webiterate.dev/google-removed-extensions-ublock-origin-108/>

This Hacker News item tracks Google removing Manifest V2 extensions from the Chrome Web Store, including legacy uBlock Origin. It is not just an ad-blocking story; it is a platform migration story with consequences for user control, security tooling, and enterprise extensions. Teams that maintain internal Chrome extensions should treat MV3 compatibility as an operational requirement, not a someday cleanup.

### 2. Darling runs macOS software on Linux — `[Hacker News]`
<https://www.darlinghq.org/>

Darling is a compatibility layer for running macOS software on Linux. Think Wine-shaped ambition, but with Mach-O binaries, macOS system interfaces, and desktop-framework compatibility in the way. It is unlikely to become a default production dependency soon, but it is a useful reminder of how much engineering hides below application portability.

### 3. Simon Willison introduces wrapture for Python testing and tracing — `[Simon Willison]`
<https://simonwillison.net/2026/Aug/31/introducing-wrapture/>

Simon Willison highlights Graham Dumpleton's `wrapture`, a young project that extends monkeypatch-style wrapping into testing and runtime tracing. The interesting part is the unified mechanism: replace behavior in tests, observe calls in production-like runs, and export traces via OpenTelemetry. Python teams with older codebases may find this useful as a lower-friction path into observability.

### 4. OpenMAIC brings multi-agent classrooms to GitHub Trending — `[GitHub Trending]`
<https://github.com/THU-MAIC/OpenMAIC>

`OpenMAIC` describes itself as an Open Multi-Agent Interactive Classroom. Education is a natural testbed for agent orchestration because it has roles, feedback loops, pacing, assessment, and memory. The larger signal is that agent products do not have to start inside IDEs; onboarding, training, and internal enablement may be better early surfaces.

### 5. archify packages architecture diagrams as an agent skill — `[GitHub Trending]`
<https://github.com/tt-a1i/archify>

`archify` is an agent skill for generating architecture, workflow, sequence, data-flow, and lifecycle diagrams as self-contained HTML. That matters because diagrams are one of the first engineering artifacts agents can generate for review, not just for decoration. In a real design process, the key question is provenance: what code, ADR, API spec, or runtime trace did the diagram come from?

### 6. V2EX reports Antigravity errors in daily agent use — `[V2EX]`
<https://www.v2ex.com/t/1238542>

A V2EX thread discusses errors encountered with Antigravity. The single thread is narrow, but the pattern is broad: once AI coding agents enter daily work, error messages, logs, workspace state, network configuration, and retry behavior become part of the developer experience. Teams evaluating these tools should test failure diagnostics as deliberately as they test happy-path code generation.

### 7. V2EX questions Codex Ultra and superpowers usage costs — `[V2EX]`
<https://www.v2ex.com/t/1238551>

Another V2EX discussion calls out quota consumed when Codex Plus automatically invoked superpowers during a worktree merge-and-push workflow. Whether or not that specific case is expected, it points to a real product issue: agent cost is driven by model tier, tool calls, subtask fan-out, and helper skills. Heavy users need visibility into what the agent did, not just a final answer and a remaining quota number.

### 8. Zenn digs into Spanner's back join behavior — `[Zenn]`
<https://zenn.dev/kauche/articles/23c490c3872f77>

This Zenn post from Kauche Tech Blog walks through Spanner's back join behavior. It is a focused database piece, which is exactly why it is useful. Distributed SQL systems make many things feel managed until a query plan gets expensive; reading the plan is still the shortest path to understanding indexes, table design, and latency.

### 9. Zenn designs a role for running terraform plan with ReadOnlyAccess — `[Zenn]`
<https://zenn.dev/dely_jp/articles/terraform-plan-readonly-access>

Kurashiru Tech Blog covers how to run `terraform plan` with AWS `ReadOnlyAccess` and what the plan execution role should look like. `plan` sounds harmless, but providers, data sources, remote state, and account metadata can make the required permissions messy. Platform teams should use this as a prompt to review CI roles, temporary credentials, and audit trails.

### 10. Publickey covers Omarchy Quattro and OS-level AI agents — `[Publickey]`
<https://www.publickey1.jp/blog/26/dhhlinux_osomarchy_quattroaiosaios.html>

Publickey reports that DHH has released `Omarchy Quattro`, a desktop Linux OS release that integrates AI agents into OS configuration, operations, and plugin creation. It may stay niche, but the design direction matters. When agents move from editor plugins into the operating system layer, permissions, reversibility, and user trust become product requirements.

## Editor's note

Today's edition includes 10 items: EN 5, ZH 2, and JA 3. Anthropic News was reachable, but no fresh official post from the last 24 hours was selected. Dev Digest editor would start with the Chrome MV2 removal, wrapture, and the Terraform plan permissions article.
