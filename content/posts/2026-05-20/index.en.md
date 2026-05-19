---
title: "May 20 · Today's 10 Dev Picks"
date: 2026-05-20T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "ai-agents", "supply-chain", "vs-code", "anthropic"]
categories: ["daily"]
summary: >-
  Simon Willison compresses six months of LLM history into a five-minute PyCon talk; a Shai-Hulud-style supply chain attack lands inside PyTorch Lightning; Mozilla formally opposes Chrome's Prompt API; Anthropic absorbs Stainless to own the SDK pipeline and signs KPMG's 276k workforce. Coding agents are now boring infrastructure — and the second-order problems are arriving on schedule.
---

## Today at a glance

The story today is the second-order consequences of "coding agents actually work." Simon Willison's five-minute recap is the cleanest mile-marker for that shift. In the same news cycle: a poisoned dependency in PyTorch Lightning, Mozilla drawing a line on browser-native LLM APIs, Anthropic acquiring its SDK toolchain vendor, and a Big 4 firm wiring Claude into a 276,000-person workforce. The dev community itself is sorting into two camps faster than people predicted last year — see the V2EX threads for the unvarnished version.

## 1. Simon Willison — the last six months in LLMs, in five minutes

[The last six months in LLMs in five minutes](https://simonwillison.net/2026/May/19/5-minute-llms/) · `Simon Willison`

Annotated slides from Simon's PyCon US 2026 lightning talk. The throughline is the November 2025 inflection point: five frontier-model handoffs between Anthropic, OpenAI and Google; coding agents crossing from "occasionally works" to daily-driver; and the OpenClaw saga becoming load-bearing internet lore. If you only read one retrospective this month, make it this one.

## 2. Shai-Hulud-style malware lands in PyTorch Lightning

[Shai-Hulud Themed Malware Found in the PyTorch Lightning AI Training Library](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · `Semgrep / HN`

Semgrep's analysis of a poisoned dependency riding into PyTorch Lightning training pipelines. ML CI is now exactly the high-value target that npm and PyPI have been for years — API keys, weights, customer data all flowing through the same job runners. If your team is still treating training infra as "we'll lock it down later," this is the nudge.

## 3. Mozilla files formal opposition to Chrome's Prompt API

[Mozilla's opposition to Chrome's Prompt API](https://github.com/mozilla/standards-positions/issues/1213#issuecomment-4347988313) · `GitHub / HN`

Mozilla put a clear "harmful" stamp on Chrome's `window.ai.languageModel` proposal in the standards-positions repo. The objections — opaque models, fingerprinting surface, vendor lock-in, unpredictable behavior across browsers — are the right ones to litigate now, before web apps start hard-depending on a Chrome-only API. Expect this fight to define the AI-in-browser question for the next two years.

## 4. V2EX — programmers split cleanly into two groups

[AI 时代，程序员被清楚地分为了两类人](https://www.v2ex.com/t/1213387) · `V2EX`

A 74-reply thread on the Chinese dev forum. The dominant framing isn't "uses AI vs. doesn't" but "still owns the design and review loop vs. has outsourced understanding to the agent." The conversation is rawer than what you'll see on English Twitter and worth skimming for the diversity of opinions among engineers who are already shipping with agents daily.

## 5. V2EX — should an intern who's totally dependent on AI pass?

[实习生极度依赖 AI，要不要让他实习通过？](https://www.v2ex.com/t/1213466) · `V2EX`

A mentor asks: the intern ships, the docs are there, the tests pass — but they can't read their own PRs. The thread splits between "tool fluency is the new baseline" and "if you can't explain your code you're not an engineer." Every team running a 2026 internship is going to have to answer this, and most rubrics are still written for a 2022 world.

## 6. VS Code ships "Agent window" preview

[VS Code's new Agent window for multi-agent dev](https://www.publickey1.jp/blog/26/vs_codeaiagent_window.html) · `Publickey`

VS Code 1.120 introduces dedicated windows for multi-agent workflows, with explicit BYOK visibility and parallel long-running sessions. This is the IDE catching up to how senior devs are already working — three to five agents in flight at once, each with its own context. The BYOK panel matters most for orgs that need to prove which model touched which file.

## 7. Node.js 26 turns Temporal on by default

[Node.js 26 enables Temporal as the default date API](https://www.publickey1.jp/blog/26/nodejsdatetemporaltemporalchromeedgefirefoxnodejs.html) · `Publickey`

Twenty years of `Date` pain is finally winding down. Temporal is now default-on across Chrome, Edge, Firefox and Node.js 26. New projects can skip `dayjs` and `date-fns` entirely; existing codebases can migrate at their own pace. The wins are real: time zones, durations and non-Gregorian calendars all behave the way you'd expect from a modern stdlib.

## 8. Anthropic acquires Stainless

[Anthropic acquires Stainless](https://www.anthropic.com/news/anthropic-acquires-stainless) · `Anthropic News`

Stainless generates the official SDKs for Anthropic, OpenAI, Cloudflare and a long list of others from OpenAPI specs. Bringing them in-house means the Claude SDK / Connector / Skills surface gets one owner and one cadence. Short term: faster, more consistent SDK releases. Longer term: API-layer ergonomics start to look like a moat, the same way Stripe's SDK quality did a decade ago.

## 9. Anthropic and KPMG sign a 276,000-person strategic alliance

[KPMG integrates Claude across its core business and workforce of more than 276,000 in strategic alliance](https://www.anthropic.com/news/anthropic-kpmg) · `Anthropic News`

The first Big 4 firm to commit to a single AI vendor at this scope. Read it alongside the recent PwC, Gates Foundation and Blackstone announcements and the strategy is obvious: Anthropic is not chasing consumer share — it's planting flags in audit, legal, consulting and finance, where document density and review workflows are the actual product.

## 10. HN — Pu.sh: a full coding-agent harness in 400 lines of shell

[Show HN: Pu.sh – a full coding-agent harness in 400 lines of shell](https://pu.dev/) · `Hacker News / Show HN`

Tool calls, context management, subprocess isolation and file-diff application — the whole agent harness compressed into 400 lines of bash. The author's pitch is that with current model quality, you don't need LangChain or AutoGen to ship a serious internal dev tool. Whether or not you agree, it's a useful baseline to compare your own harness against.

## Editor's note

The meta-theme today: coding agents are normalized, and now the boring infrastructure questions are surfacing in parallel — supply chain hygiene, browser API standards, SDK ownership, enterprise rollout playbooks. The two must-reads are **Simon's six-month recap** (for the timeline) and the **Stainless acquisition** (for where the SDK and API ecosystem heads next). GitHub Trending rendered as an empty page on our fetch today, so individual trending repos didn't make this issue.
