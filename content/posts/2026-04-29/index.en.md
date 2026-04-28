---
title: "April 29 · Today's 10 Dev Picks"
date: 2026-04-29T07:00:00+09:00
draft: false
tags: ["digest", "2026-04", "github", "ghostty", "warp", "terminal", "ai", "openai", "anthropic", "typescript", "spanner", "claude-code"]
categories: ["daily"]
summary: "A loaded Wednesday. HN #1 is Mitchell Hashimoto pulling Ghostty off GitHub (1097 pts). Same day: Warp goes open-source (HN #4 + #18), and HN #25 — 'GitHub Actions is the weakest link' — closes the trifecta. CVE-2026-3854: Wiz publishes a GitHub RCE breakdown (HN #9). Business: Stratechery interviews Sam Altman and AWS CEO Matt Garman together — OpenAI models are coming to Amazon Bedrock (HN #3). Japan beat: TypeScript 7.0 Beta (10× faster, Go-rewritten compiler) and Google Cloud's local-installable Spanner Omni preview. China beat: V2EX threads on Codex outpacing Claude Code in reputation, and an open-source multi-IM agent project openbee."
---

## 🌐 Today at a glance

One throughline today: **developer trust in GitHub is fracturing**. Mitchell Hashimoto (HashiCorp co-founder, GitHub user 1299) moved Ghostty off GitHub after keeping a year-long journal of every Actions outage that cost him real work — HN #1 with 1097 points. Same day, Warp open-sourced its full Rust codebase (HN #4 + #18). HN #25 is nesbitt.io's "GitHub Actions is the weakest link" — a calm SRE breakdown of why the most-relied-upon piece of GitHub is also its weakest. Read all three together and the signal is clear: **single-vendor CI/CD is finally a budget-line conversation, not a religious one**. On the business side, Stratechery's joint interview with Sam Altman and AWS CEO Matt Garman lands HN #3 — OpenAI is heading to Bedrock days after the Microsoft exclusivity agreement officially ended. Wiz drops CVE-2026-3854's full GitHub RCE post-mortem (HN #9). Japan: Publickey doubles down with TypeScript 7.0 Beta (Go-rewritten, ~10× compile speed) and **Spanner Omni** — Spanner you can install on your own machines. China's V2EX is debating whether Codex has overtaken Claude Code in real-world agent work.

---

## 🔥 Today's 10

### 1. [Hacker News / mitchellh.com] Ghostty is leaving GitHub
**Link:** https://mitchellh.com/writing/ghostty-leaving-github
HN #1 (1097 pts, 309 comments). Mitchell Hashimoto kept a year of journal entries marking each day GitHub blocked him from real work; the day he wrote this post, Actions cost him another two hours of PR review. "I'm GitHub user 1299. I've opened it every day for 18 years. It's no longer a place for serious work." Personal projects stay for now — Ghostty does not. **Practical signal**: this isn't one outage, it's a cultural inflection. Multi-host (mirror to Codeberg, Gitea, GitLab self-managed) and multi-runner (self-hosted + Buildkite/Earthly) stop being over-engineering and start being baseline 2026 hygiene.

### 2. [Hacker News / warp.dev] Warp terminal is now open source
**Link:** https://github.com/warpdotdev/warp
HN #4 (164 pts) + HN #18 (109 pts). Warp — the AI-native terminal that defined the "fancy paid terminal" category — released its full codebase under a permissive license. Context: a wave of OSS competitors (Wave, Tabby, etc.) and the broader AI-tooling shift toward "ship the source, monetize the cloud." **What it changes**: AI completion, inline agents, block-style rendering — features that were paywalled — are now self-hostable. Pair it with yesterday's OpenCode story and the meta-pattern crystallizes: **AI dev tools are converging on OSS + local + cheaper**, faster than any vendor's roadmap suggested.

### 3. [Hacker News / nesbitt.io] GitHub Actions is the weakest link
**Link:** https://nesbitt.io/2026/04/28/github-actions-is-the-weakest-link.html
HN #25 (184 pts, 62 comments). The companion piece to the Ghostty story. SRE-style analysis: across the GitHub platform, Actions is the component with the worst measured availability — and yet it's the root node for releases, deploys, dependency bumps, and security automation. The author's prescription isn't "leave GitHub," it's **layered redundancy** — keep core pipelines reachable through self-hosted runners or a second executor. **For platform teams**: useful ammunition next time someone questions the cost of dual-runner setups.

### 4. [Hacker News / Stratechery] OpenAI models coming to Amazon Bedrock
**Link:** https://stratechery.com/2026/an-interview-with-openai-ceo-sam-altman-and-aws-ceo-matt-garman-about-bedrock-managed-agents/
HN #3 (115 pts, 40 comments). Ben Thompson's joint interview with Sam Altman and AWS CEO Matt Garman. Two beats: (a) OpenAI models are coming to Bedrock, and (b) Bedrock Managed Agents — AWS's bet on durable-state, sandboxed, long-horizon agent execution. Last week's Microsoft exclusivity unwind turned into actual wiring within days. **For platform/AI architects**: Bedrock is now the only place where Anthropic + Meta + OpenAI all show up under one IAM policy. That changes the math for anyone evaluating multi-cloud AI today.

### 5. [Hacker News / Wiz] CVE-2026-3854 GitHub RCE breakdown
**Link:** https://www.wiz.io/blog/github-rce-vulnerability-cve-2026-3854
HN #9 (178 pts, 45 comments). Wiz publishes the chain, timeline, and blast radius of the GitHub RCE. Reading it next to today's Ghostty post is darkly funny: developers are simultaneously upset that Actions falls over and that it has serious holes when it's up. **Action items today**: audit GitHub Apps, OAuth token scopes, and self-hosted runner network isolation. If you ship via GHA, this CVE is a free internal threat-modeling exercise.

### 6. [Hacker News / GitHub] LocalSend — open-source AirDrop alternative
**Link:** https://github.com/localsend/localsend
HN #17 (707 pts, 223 comments). Flutter app, all five major platforms, LAN-only file transfer with no cloud roundtrip. Re-surfaced today and resonates with the day's meta-theme — the consumer side of "stop relying on a central platform." **Practically useful** for any household with a mix of iPhone / Android / Windows / Mac, where AirDrop only works in one quadrant of the matrix.

### 7. [Publickey] TypeScript 7.0 Beta — compiler ported to Go, ~10× faster
**Link:** https://www.publickey1.jp/blog/26/typescript_70typescriptgo10.html
Microsoft shipped the first beta of `tsc` rewritten in Go: 10× compile, 8× editor startup, half the memory, validated on multi-million-line codebases. Zenn already has multiple deep-dives ([ubie_dev's analysis](https://zenn.dev/ubie_dev/articles/typescript7-tsgo-whatsnew), [terass_dev's piece](https://zenn.dev/terass_dev/articles/d9335be2a69c85)). **For monorepo owners**: TypeScript build time has been the silent tax on every CI run for years; a 10× cut is the kind of number that justifies a Q3 platform initiative on its own. Compatibility surface is reportedly small — start scoping a migration spike in May.

### 8. [Publickey] Spanner Omni preview — install Spanner on your own hardware
**Link:** https://www.publickey1.jp/blog/26/google_cloudrdbspanner_omni.html
The other heavyweight from Google Cloud Next 2026. Spanner — the "globally distributed strongly-consistent RDB you could only get on GCP" — is now installable on your own infrastructure as a preview. **Why this matters**: it directly attacks Oracle Exadata at the high end and answers the data-residency objection (regulated industries, sovereign clouds) that kept Spanner off many shortlists. Worth tracking through GA.

### 9. [V2EX / Chinese-language] Is Codex's reputation overtaking Claude Code?
**Link:** https://www.v2ex.com/t/1207711
A thread that opened April 22 has been gathering momentum all week. The community sentiment: Codex now feels stronger on long-horizon agent tasks and multi-file edits, while Claude Code remains preferred for review and root-cause analysis. OpenAI's Codex-as-plugin for Claude Code ([t/1202376](https://v2ex.com/t/1202376)) accelerates the blur. **Reading**: same theme as the GitHub trust crisis — independent devs are explicitly designing their workflow around two vendors instead of one.

### 10. [V2EX / Chinese-language] openbee — open-source multi-IM AI agent orchestrator
**Link:** https://www.v2ex.com/t/1208983
A self-shared OSS project that integrates WeChat / DingTalk / Slack and orchestrates Claude Code, Codex, Pi, Kimi, and others — voice-driven task completion across IM platforms. **Why it's worth a click**: (a) multi-IM integration is real engineering, and the discussion thread surfaces the hard parts (rate limits, model routing, audit trails); (b) multi-agent orchestration has no agreed best practice yet, and community implementations are where the design debate is actually happening.

---

## Editor's note

Today's meta-theme is **trust under reconstruction**. Trust in GitHub, Microsoft–OpenAI exclusivity, tsc being slow forever, Claude Code as the lone serious agent for solo devs — four givens cracked the same day. **If you read only one piece**: Mitchell Hashimoto's Ghostty post — it's the rare engineering essay where emotion, data, and decision all line up. **If you can stomach two**: pair it with the TypeScript 7.0 Beta announcement on Publickey for the rare "10× speedup is real" tech win. The Stratechery interview is excellent but paywalled — HN comments cover the substance. Simon Willison didn't drop a new long-form today (yesterday's AGI-clause archaeology piece is still echoing), so the EN/JA/ZH source mix tilts EN today; I trimmed weak picks rather than fill the slate. See you tomorrow.

— Dev Digest editors
