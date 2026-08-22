---
title: "August 22 · Today's 10 Dev Picks"
date: 2026-08-22T07:00:00+09:00
draft: false
tags: ["digest", "2026-08", "ai", "github", "security", "devtools", "llm"]
categories: ["daily"]
summary: >-
  Today's digest is about AI tooling becoming operational: agent skills, Cursor plugins, SDK dependency drift, search filtering, multimodal APIs, and Flutter release mechanics.
---

## Today at a glance

The useful theme today is not a single model launch. It is the tooling around model-driven development becoming more concrete: skills as repo artifacts, plugins as IDE surface area, SDK dependencies as production risk, and multimodal APIs as another benchmark item. Anthropic News was reachable, but no fresh official post from the last 24 hours made the cut.

---

### 1. Kagi adds a setting to remove paywalled links — `[Hacker News]`
<https://kagi.com/changelog#11296>

Kagi added a search setting that filters paywalled links out of results. That sounds small, but it treats readability as part of search quality rather than an afterthought. For developers who use search as a daily debugging and research tool, access friction is now part of the ranking conversation.

### 2. Accidentally logging phone calls to military bases through E.164 routing — `[Hacker News]`
<https://lina.sh/blog/hijacking-e164-arpa>

This write-up walks through an E.164/ENUM routing issue that led to the author receiving metadata for large numbers of calls to military bases. The lesson is not limited to telecom: legacy delegation chains can fail in ways that modern security dashboards may not model. DNS, phone numbers, certificates, and mail routing still deserve real inventory work.

### 3. DeepSeek publishes a vision experimental API guide — `[Hacker News]`
<https://api-docs.deepseek.com/guides/vision/>

`deepseek-v4-flash-vision-exp` showed up on HN as another sign that multimodal APIs are moving into lower-cost, easier-to-test territory. Treat the `exp` label seriously: this belongs in evaluation harnesses before it belongs in production paths. The interesting comparison points are latency, image reasoning quality, pricing, and safety behavior under messy inputs.

### 4. `mattpocock/skills` turns agent habits into versioned assets — `[GitHub Trending]`
<https://github.com/mattpocock/skills>

Matt Pocock's `skills` repo was high on GitHub Trending today. The important part is not that it is another prompt collection; it frames agent skills as files that can be reviewed, reused, and retired. Mature teams will likely move from private prompt tricks toward shared skill libraries with ownership and review.

### 5. Cursor's plugin specification lands in Trending — `[GitHub Trending]`
<https://github.com/cursor/plugins>

`cursor/plugins` contains Cursor's plugin specification and official plugins. As AI IDEs become extensible runtimes, plugin governance becomes a security and platform concern. The hard questions are permissions, distribution, auditability, and how quickly a team can disable a risky extension.

### 6. Simon Willison ships `llm 0.32.1` after OpenAI SDK dependency drift — `[Simon Willison]`
<https://simonwillison.net/2026/Aug/21/llm/>

Fresh installs of Simon Willison's `llm` broke because the OpenAI Python package stopped pulling in `httpx`, which `llm` had been getting transitively. The fix pins `openai<3` for now, with a follow-up release planned. It is a clean reminder that AI tooling still fails like ordinary software: transitive dependencies, version bounds, and packaging assumptions matter.

### 7. Can a Bank of China VISA card buy Codex? — `[V2EX]`
<https://www.v2ex.com/t/1236338>

This V2EX thread is short, but it captures a real adoption issue for developers outside the default US payment path. Access to AI development tools can hinge on cards, regions, invoices, and account risk controls. For teams, payment and procurement reliability should be part of the tool evaluation, not an afterthought after the pilot succeeds.

### 8. An AI startup-opportunity discovery tool looks for growth help — `[V2EX]`
<https://www.v2ex.com/t/1236337>

The post describes an AI tool for discovering startup opportunities and asks for growth or operations collaborators. It is not deep engineering content, but it reflects where the bottleneck has moved: prototypes are cheap, validation is not. The durable advantage is increasingly distribution, feedback loops, and iteration discipline.

### 9. Using Codex efficiently with ChatGPT and GitHub — `[Zenn]`
<https://zenn.dev/aun_phonogram/articles/3f8c1a7b5d902e>

This Zenn article on using Codex with ChatGPT and GitHub drew strong attention. The broader point is that agent productivity depends on workflow shape: issue framing, branch scope, PR feedback, and review loops. A good process beats a giant one-shot prompt.

### 10. Flutter 3.47 separates UI packages and keeps pushing toward WebAssembly — `[Publickey]`
<https://www.publickey1.jp/blog/26/fluter_347uiwebassembly.html>

Publickey covers Flutter 3.47, including more independent updates for UI libraries and continued movement toward WebAssembly output. For cross-platform teams, this changes upgrade planning more than it changes a single feature checklist. Watch plugin compatibility, renderer behavior, Web build size, and whether UI package cadence makes patching easier or noisier.

---

## Editor's note

Today's 10 picks came from HN 3, GitHub Trending 2, Simon Willison 1, V2EX 2, Zenn 1, and Publickey 1; by language, the mix is EN 6, ZH 2, JA 2. V2EX was reachable but light on hard technical threads, so the Chinese picks focus on adoption friction and early product signals. Dev Digest editor's must-reads are the E.164 incident, `mattpocock/skills`, and `llm 0.32.1`: infrastructure risk, agent workflow assets, and dependency hygiene in one morning.
