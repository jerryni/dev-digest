---
title: "November 9 · Today's 10 Dev Picks"
date: 2026-11-09T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "developer-tools", "ai", "security"]
categories: ["daily"]
summary: "Local AI, desktop software, and security automation all point to the same question: where do new tools stop?"
---

# November 9 · Today's 10 Dev Picks

## Today at a glance

Today's links are about taking impressive capabilities out of demos and into bounded systems. WebGPU desktop-class apps, local inference, and browser agents are all useful precisely when their data, permissions, and failure modes are explicit.

## Picks

### 1. [KetchUp, an open-source SketchUp alternative built with Rust and WebGPU](https://ketchup3d.github.io/app/)
`Hacker News · Graphics`

KetchUp is aiming at browser-based 3D modeling with Rust and WebGPU. The interesting signal is less replacement rhetoric than the widening distribution path for GPU-heavy creative tools. Test import/export and large-model behavior before treating a polished demo as a production option.

### 2. [Dux, a free and open-source Wayland desktop shell](https://duxlabs.dev/)
`Hacker News · Linux`

Dux combines a desktop shell, file manager, and theming layer. Desktop environments are long-lived systems problems: input, window protocols, extension points, and maintenance all matter. It is a useful lens into where Wayland ecosystem work is concentrating.

### 3. [Llama-modchip runs 284B DeepSeek on 64GB RAM without a GPU](https://github.com/synchopate/llama-modchip)
`Hacker News · Local AI`

This project explores making an enormous model fit on a high-memory machine. It does not make self-hosting universally economical, but it sharpens the trade-offs among quantization, throughput, and data residency. For sensitive workloads, local executability is a capability worth measuring.

### 4. [parse_number(), a SQLite extension in C versus Rust](https://simonwillison.net/2026/Nov/8/sqlite-parse-number-c-vs-rust/)
`Simon Willison · Data tools`

Simon Willison uses a small SQLite extension to compare implementation paths in C and Rust. Small components are excellent language-choice experiments because build, packaging, FFI, and error handling show up immediately. Count installation and maintenance cost, not just lines of code.

### 5. [agent-browser on GitHub Trending](https://github.com/vercel-labs/agent-browser)
`GitHub Trending · Agents`

agent-browser gives agents a CLI for browser actions. That is useful, but it also brings authenticated sessions, downloads, and external navigation into the threat model. Start with read-only accounts, an allowlist, and replayable logs.

### 6. [Anthropic Skills on GitHub Trending](https://github.com/anthropics/skills)
`GitHub Trending · Workflow`

The repository treats reusable agent instructions as versioned artifacts. A skill should be more than prompt text: its permissions, prerequisites, and completion tests need the same review trail. That is how automation becomes inspectable rather than merely repeatable.

### 7. [FinallyShell, a Go-based SSH client](https://www.v2ex.com/t/1255296)
`V2EX · Developer community`

This community project recreates a familiar SSH workflow with a Go implementation and a different session layout. Terminal clients win or lose on everyday friction: keys, jump hosts, transfers, and reconnects. It is a good reminder that focused workflow improvements can still be strong product work.

### 8. [Terminal Spike, an Android terminal with SSH, Mosh, tmux, and agents](https://www.v2ex.com/t/1255422)
`V2EX · Mobile operations`

Terminal Spike brings several remote-operations tools to Android. Mobile access is valuable during incidents, but it needs short-lived credentials and a clear audit trail more than an expanded command palette. Keep direct production paths deliberately narrow.

### 9. [A Meiji-era date correction broke unit tests](https://zenn.dev/xin9le/articles/9a1cf8e10494d6)
`Zenn · Testing`

An update to historical calendar data caused tests to fail. Dates, time zones, calendars, and administrative reference data are dependencies that can change underneath stable code. Record their source and version in fixtures so a red CI build can be explained quickly.

### 10. [Automating vulnerability checks with Zero Wire, GitHub Actions, and Claude](https://zenn.dev/tomipetit/articles/zero-wire-github-actions)
`Zenn · Security automation`

This workflow connects vulnerability information to routine checks of public servers. The sensible boundary is to have a model generate leads for review, not autonomous remediation. The nearer automation gets to external assets, the more it needs human confirmation, notification, and rollback paths.

## Editor's note

Read the local-model experiment and the vulnerability-check workflow together: one moves capability closer to the machine, the other constrains capability inside a process. Distribution today is six English, two Chinese, and two Japanese items. Anthropic News had no verifiable same-day technical update, so this edition does not pad the list with older posts.
