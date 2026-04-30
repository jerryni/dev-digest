---
title: "April 30 · Today's 10 Dev Picks"
date: 2026-04-30T07:00:00+09:00
draft: false
tags: ["digest", "2026-04", "zed", "anthropic", "claude-code", "mistral", "rust", "github", "mcp", "security", "v2ex", "xiaomi"]
categories: ["daily"]
summary: "A telling Thursday on HN. Zed 1.0 lands with the day's highest score (1319 pts, HN #2) — but the #1 slot belongs to a GitHub issue inside anthropics/claude-code: a config file called HERMES.md, an internal A/B experiment, double-charged a customer ~$200 and Anthropic refused the refund (836 pts). HN #13 'We need a federation of forges' (488 pts) keeps yesterday's Ghostty-leaving-GitHub thread burning. AI: Mistral Medium 3.5 ships remote agents (HN #24). Security double feature: Copy Fail / CVE-2026-31431 (HN #3) and Ramp's Sheets AI exfiltrating financials via prompt injection (HN #9). Japan's Zenn delivers two strong Claude Code field reports — LayerX's 'ccgate' auto-approves 97% of permission prompts; Finatext warns against handing Google accounts to AI agents. China's V2EX is consumed by Xiaomi's MiMo Token Plan."
---

## 🌐 Today at a glance

A small inversion on HN today. **Zed 1.0** ships and takes the day's highest score (1319 pts, HN #2) — but the #1 slot is held by a GitHub issue inside `anthropics/claude-code` (836 pts): a customer found `HERMES.md`, an internal A/B-experiment config, was double-counting tokens for the cohort it landed on, costing them ~$200 in a week — and support refused the refund. The fact that it reached HN #1 is its own form of accountability theater. HN #13 — Tangled's "We need a federation of forges" — keeps yesterday's Ghostty-leaves-GitHub current alive. AI: **Mistral Medium 3.5** (HN #24) lands with remote agents — Europe's answer to Operator/Computer Use. Security ships two: **Copy Fail / CVE-2026-31431** (HN #3) shows browser copy-actions can be hijacked, and **PromptArmor** demonstrates indirect prompt injection exfiltrating real financial data from Ramp's Sheets AI (HN #9). On the Japan beat, two strong Zenn pieces: **LayerX's ccgate** auto-approves 97% of Claude Code permission prompts; **Finatext** writes the field manual on why your AI agents should not hold a human Google account. China beat: V2EX is consumed by **Xiaomi's MiMo Token Plan** — independent devs running the math on whether the ¥659/month max tier is worth it.

---

## 🔥 Today's 10

### 1. [Hacker News / zed.dev] Zed 1.0
**Link:** https://zed.dev/blog/zed-1-0
HN #2 (1319 pts, 417 comments) — top score of the day. Four years after the original Atom team (Nathan Sobo et al.) started rebuilding their editor in Rust, Zed reaches 1.0. The 1.0 case: GPU-accelerated rendering that visibly outpaces VS Code on big files and split panes; Live-share-grade collaboration built in, no extension; AI assist with first-class Claude / OpenAI / Ollama support. **The real signal**: VS Code's Copilot lock-in plus Microsoft telemetry has been pushing a meaningful slice of senior engineers toward an exit, and Zed is now serious enough to be that exit — open source, local-first, AI built in. If you've been waiting to evaluate it, this is the cut.

### 2. [Hacker News / github.com/anthropics] Anthropic over-charges Claude Code user $200, refuses refund
**Link:** https://github.com/anthropics/claude-code/issues/53262
HN #1 (836 pts, 322 comments). A Claude Code user discovered `HERMES.md`, a config file shipped to the `anthropics/claude-code` repo to gate an internal A/B experiment that doubled token accounting for the affected cohort. They were over-charged ~$200 in a single week, requested a refund, and were told "per ToS, no refunds." Two threads dominate the comments: (a) **A/B experiments must be cost-neutral to the customer** — Anthropic should eat the delta, not invoice it; (b) the fact that a GitHub issue is the most reliable accountability path is itself a critique. Pair this with the broader trust-fracture theme and **the actionable read for AI buyers is**: audit your vendor's experiment policy and refund SLA *before* the next contract renewal.

### 3. [Hacker News / blog.tangled.org] We need a federation of forges
**Link:** https://blog.tangled.org/federation/
HN #13 (488 pts, 311 comments). Same lineage as yesterday's Ghostty post. Tangled — built on AT Protocol — argues the obvious-once-said point: **Git is decentralized; hosting is not**. Issues, PRs, and Actions remain trapped on a per-platform island, so "leaving GitHub" today still means losing context. Three protocols are now competing for "federated developer social": ActivityPub (mature, mostly used by ForgeFed), AT Protocol (Tangled), and Nostr (a few smaller forge experiments). **Operational implication for self-hosted Gitea / GitLab admins**: bake "issue-history portability" into your migration playbook — without it, mirror-everything is theater.

### 4. [Hacker News / corrode.dev] Bugs Rust won't catch
**Link:** https://corrode.dev/blog/bugs-rust-wont-catch/
HN #20, 613 pts, 332 comments. corrode.dev's recurring high-quality Rust longform. The thesis is unfashionable but correct: **Rust catches memory safety and data races; logic bugs, `unwrap` panics, `unsafe` misuse, and TOCTOU vulnerabilities still ship to production.** A dozen worked examples: `RwLock` fairness assumptions that don't hold across versions, `mem::forget` as an undetected leak path, `Send`/`Sync` boundaries that compile but lie. **For teams six months into a Rust migration**, this is the article to circulate before the next post-mortem — to recalibrate which classes of bug your tooling actually closes.

### 5. [Hacker News / mistral.ai] Mistral Medium 3.5 — remote agents
**Link:** https://mistral.ai/news/vibe-remote-agents-mistral-medium-3-5
HN #24 (370 pts, 181 comments). Mistral's Europe-flavored answer to OpenAI Operator and Claude Computer Use, plus a model bump. SWE-Bench Verified numbers land near Claude Sonnet 4 at ~35% lower cost. **Why this matters beyond "another model"**: GDPR-anchored deployments — financial, healthcare, EU public-sector — have been quietly shut out of the Operator / Computer Use generation because of where the agent runs and what it can see. Medium 3.5 is the first credible non-US/non-China option that actually has the agent harness, not just the chat completions endpoint. Expect EU procurement RFPs to add it to the shortlist within the quarter.

### 6. [Hacker News / promptarmor.com] Ramp's Sheets AI exfiltrates financials via prompt injection
**Link:** https://www.promptarmor.com/resources/ramps-sheets-ai-exfiltrates-financials
HN #9 (77 pts, 25 comments). PromptArmor demonstrates indirect prompt injection against Ramp (a $13B B2B finance SaaS): an attacker plants instructions in an invoice PDF, the Sheets AI ingests it, and company spend data leaves via an outbound webhook. **This is not a PoC against a toy** — it's a working exploit against a production agentic SaaS in active enterprise use. The traditional WAF / DLP layer cannot see the "read PDF → call tool → exfiltrate" chain. Mitigations PromptArmor recommends are pragmatic and immediately implementable: read-only model mode, tool-call allowlists, mandatory human confirmation on writes. If you ship agentic features, this is today's reading.

### 7. [Hacker News / copy.fail] Copy Fail — CVE-2026-31431
**Link:** https://copy.fail/
HN #3 (338 pts, 169 comments). A small, nasty class of vulnerability: **the browser's copy action itself can be hijacked** so that what you paste isn't what you saw — a wallet address, a shell command, a token. Affects multiple Chrome / Firefox versions; PoC and CSP-based mitigations published. **Why this matters for the LLM-era developer**: the muscle memory of "copy from ChatGPT/Claude → paste into terminal" is two years old and now demonstrably exploitable. Today's hygiene update: paste shell commands into an editor first, never paste wallet addresses out of an enriched-content surface, push the browser update.

### 8. [Zenn / LayerX] "ccgate" — auto-approve 97% of Claude Code permission prompts
**Link:** https://zenn.dev/layerx/articles/20260428-ccgate
A LayerX engineer publishes the OSS gateway they built after measuring that **Claude Code permission prompts were costing developers ~30% of their attention** — and most "yes" answers were rote anyway. ccgate sits in front of Claude Code as an MCP-shaped gateway, classifies requested operations (read / write / network), checks against a per-team allowlist, auto-approves the trivial 97%, and forces human confirmation on the rest with audit logging. **Why it matters**: this is the first OSS-layer answer to enterprise Claude Code rollouts where individual `--allowedTools` config doesn't scale. The same pattern transfers to Codex and Cursor. Today's must-clone repo.

### 9. [Zenn / Finatext] You're handing your company's Google account to an AI agent
**Link:** https://zenn.dev/finatext/articles/mcp-gateway-google-sa
A Finatext security engineer writes the field manual for a problem that is going to bite a lot of companies in the next six months. Many teams enable AI agents on Gmail / Calendar / Drive by handing over **a human OAuth token** — your token, the agent's token, same blast radius. One prompt injection and the company's mail and calendar are exfiltratable. The article walks the correct shape: **Service Accounts behind an MCP gateway** with per-request audit logs and minimum-scope delegation, with concrete GCP IAM snippets and MCP middleware code. Read alongside today's Ramp post-mortem (#6) — the question of "what credential does your agent hold and what outbound paths can it take" should be on the agenda of every security review this quarter.

### 10. [V2EX] Xiaomi MiMo Token Plan ("100T plan") — is it worth it?
**Link:** https://www.v2ex.com/t/1209234
**Related threads:** [t/1209334](https://www.v2ex.com/t/1209334), [t/1209476](https://www.v2ex.com/t/1209476). The dominant V2EX engineering thread of the week. Xiaomi launched MiMo Token Plan with a max tier at ¥659/month for a 100-trillion-token cap on its in-house MiMo models. Three useful things in the comments: (a) the price is not decisively below DeepSeek-V3 / Kimi K2 on real workloads; (b) thread 1209476 dissects how "100T tokens" is a *call ceiling*, not a real inference budget; (c) thread 1209334 debates whether the price tier is too high — leaving GPUs idle and starving Xiaomi of training-data feedback. **Why this is a useful read for non-Chinese engineers**: it's the first temperature reading on China's domestic LLM market entering a genuine zero-sum phase, with independent-developer math you can't get from press releases.

---

## Editor's note

Two themes braid together today: **AI vendor trust is fracturing in public** (the HERMES.md issue), and **the community is paving over the cracks itself** (ccgate, Finatext's Google-account warning). If you read two things, read those two — same week, same problem space, opposite ends of the supply chain. Zed 1.0 is excellent but not urgent; spin it up over the holiday. Mistral / Ramp / Copy Fail are scanline reads for AI and security weeks. Tomorrow at 7am.

— Dev Digest editor
