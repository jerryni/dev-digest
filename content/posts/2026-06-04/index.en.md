---
title: "June 4 · Today's 10 Dev Picks"
date: 2026-06-04T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "microsoft-build", "anthropic", "vscode", "security", "codex", "windows", "performance"]
categories: ["daily"]
summary: "Microsoft Build 2026 floods the feed: seven first-party AI models, MXC sandboxes for agents, WSL containers, and GNU coreutils ported to Windows. A 1-click VSCode bug let attackers steal GitHub tokens. Anthropic doubles down on partners and ships a year of cyber-threat data."
---

## Today at a glance

Day two of Microsoft Build 2026 is doing most of the work in our feed. Redmond is using the show to plant flags everywhere a Linux dev currently lives: seven in-house AI models, a per-agent sandbox runtime called MXC, real Linux containers on WSL, and an official Coreutils-for-Windows that ships `ls` and `cat` in the box. On the security side, an `ammaraskar` post explains how a single click in VSCode could exfiltrate your GitHub PAT, which is the sort of finding you want to read before lunch, not after. Anthropic, meanwhile, opens a Services Track for its Partner Network and drops a sober look at a year of AI-enabled attack data mapped onto MITRE ATT&CK.

---

### 1. 1-Click GitHub Token Stealing via a VSCode Bug — `[Hacker News · 579 pts]`
<https://blog.ammaraskar.com/github-token-stealing/>

A workspace-trust bypass let a malicious repository trigger a single-click flow that exfiltrated the user's GitHub OAuth token. The writeup is the rare kind that walks through the URL handler abuse and the disclosure timeline without hand-waving. If you run VSCode with the GitHub extension and review PRs from random forks, this is your read of the day. Microsoft has patched, but a lot of teams pin VSCode versions for compliance reasons — go check yours.

### 2. Every Byte Matters — `[Hacker News · 166 pts]`
<https://fzakaria.com/2026/06/01/every-byte-matters>

A long, satisfying tour through what a single wasted byte costs you when it shows up in a hot path: cache lines, page faults, branch predictor pressure, and the way modern allocators round things up behind your back. The author works through real measurements rather than vibes, which makes the conclusions portable. Pair it with `perf stat` on your own service for an honest afternoon.

### 3. Pasted File Editor — `[Simon Willison]`
<https://tools.simonwillison.net/pasted-file-editor>

Simon shipped a small but telling tool: paste a long blob, get a file-attachment editor that mimics what Claude.ai and the Claude desktop apps do automatically. The interesting part is the build story — he had Codex desktop produce the whole thing from a single prompt, which is one more data point that 'Claude/Codex makes a webapp from a paragraph' is now table stakes. Useful as a clipboard utility, more useful as a template for your own internal tools.

### 4. Careful upgrading Codex (26.601.21317) — `[V2EX · 程序员]`
<https://www.v2ex.com/t/1217473>

The latest Codex desktop build is breaking auth flows for a chunk of Asia-Pacific users; the thread collects the symptoms and a couple of working downgrades. If you depend on `codex` in CI or commit-on-save loops, hold off a day or two — there's no real upside to being on the bleeding edge of this particular release.

### 5. A terminal app that lets you drive Claude Code / Codex from your phone — `[V2EX · 分享创造]`
<https://www.v2ex.com/t/1217542>

`rwecho` built a mobile terminal that proxies to a remote Claude Code or Codex session. The UX is closer to a chat client than to ssh, which is the right call for thumbs. Whether this is 'useful for real' or 'useful for the train' depends on how much of your day is single-prompt jobs, but it's a clean example of treating coding agents as the addressable thing rather than the editor they live inside.

### 6. Coreutils for Windows — `[Publickey · Microsoft Build 2026]`
<https://www.publickey1.jp/blog/26/unixwindowscoreutils_for_window.html>

Microsoft is shipping a Rust-based port of GNU coreutils as a first-party Windows component. `ls`, `cat`, `cp`, `mv`, `rm`, and friends will be present out of the box on Windows 11. PowerShell aliasing has been an unloved compromise for two decades; replacing it with the actual tools makes cross-platform Makefiles and shell-script-style automation usable on a stock Windows VM. The Rust uutils project gets a very large second wind out of this.

### 7. Microsoft Execution Containers (MXC) — `[Publickey · Microsoft Build 2026]`
<https://www.publickey1.jp/blog/26/aimicrosoft_execution_containers_mxc.html>

Microsoft introduced a per-agent isolation runtime aimed squarely at the 'what if your agent runs rm -rf' problem. MXC is customizable per-tool, supports policy gates, and integrates with the rest of the Agent Framework. The interesting comparison is Anthropic's Project Glasswing and the various Linux-namespace hacks coding agents use today — MXC reframes it as a first-class OS concept rather than a wrapper script.

### 8. Microsoft's first-party AI Models lineup — `[Microsoft AI Blog]`
<https://microsoft.ai/news/introducingmai-code-1-flash/>

Microsoft unveiled seven in-house 'Microsoft AI Models' at Build, with MAI-Code-1-Flash as the most engineer-relevant: a small, latency-optimized coding model meant to sit inside VSCode and the new Coreutils-aware Windows agents. The strategic read is straightforward — after years of being primarily an OpenAI distributor, Microsoft now ships a real model family of its own. The benchmark numbers are reasonable; the integration story is the actual product.

### 9. Anthropic Services Track and Partner Hub — `[Anthropic]`
<https://www.anthropic.com/news/services-track-partner-hub>

Anthropic formalized a services tier inside its Partner Network and launched a Partner Hub to surface implementation partners, training, and certification. For consultancies this is the closest thing yet to a stable channel program. For engineering leaders, the Hub is mainly useful as a vendor shortlist when you need someone to stand up Claude Code at scale and can't justify hiring for it directly.

### 10. What we learned mapping a year's worth of AI-enabled cyber threats — `[Anthropic · Policy]`
<https://www.anthropic.com/news/AI-enabled-cyber-threats-mitre-attack>

Anthropic released an analysis of AI-enabled threat patterns observed over the last year, mapped onto the MITRE ATT&CK framework. The headline finding is that current AI uplift is mostly in reconnaissance, social-engineering payload generation, and initial-access tooling — not novel exploit classes. The mapping itself is the contribution; it gives blue teams a way to talk about AI threats with the same vocabulary they already use for everything else.

---

## Editor's note

Today is Microsoft's day. Half the stories trace back to Build 2026, and the two most interesting non-Build items — the VSCode token bug and Anthropic's MITRE mapping — are both about agent / dev-tool security catching up with how much access we've granted these systems. If you only read two: **#1 (the VSCode token bug)** for the immediate operational risk, and **#7 (MXC)** for the medium-term direction of where agent sandboxes are heading.

— Dev Digest editor
