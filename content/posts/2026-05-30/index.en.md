---
title: "May 30 · Today's 10 Dev Picks"
date: 2026-05-30T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "claude", "kiro", "docker", "agents", "datasette"]
categories: ["daily"]
summary: "AWS pushes Kiro into the browser, Docker ships Gordon. Vicki Boykis on why engineers should be more tired than the model. Simon Willison argues Anthropic and OpenAI have crossed product-market fit, with corroborating evidence from V2EX consumer bills."
---

## Today at a glance

A Saturday digest, but the coding-agent shipping cadence didn't slow down. AWS quietly pulled Kiro into the browser, and Docker promoted its own Gordon agent to GA. Read together, the next battlefield isn't "which CLI do you install" — it's "which agent is already living in the tool you didn't have to install." On the reflection side, Vicki Boykis' "we should be more tired than the model" hit HN and is the most quotable thing this week. And Simon Willison's PMF essay finally puts numbers around what most builders already feel: enterprise spend on Claude is no longer a science experiment.

## Today's 10

### 1. AWS launches Kiro Web — coding agent, no install
**Source: Publickey (JP IT press)**
<https://www.publickey1.jp/blog/26/awswebaikiro_web.html>

AWS reframed its Kiro coding agent as a browser product. The obvious read is "another Cursor competitor," but the more interesting one is that Kiro Web kills the install-permission conversation that historically blocked agentic tooling inside large enterprises. Expect "agent already in the browser" to become a real category alongside the install-a-CLI model.

### 2. Docker's Gordon agent ships GA
**Source: Publickey (JP IT press)**
<https://www.publickey1.jp/blog/26/dockeraigordondocker.html>

Docker's own agent — narrow, vertical, only answers Docker questions, including fixing your Dockerfile — is now generally available, free tier included. Pair this with last week's official Dart & Flutter Agent Skills release, and a pattern emerges: upstream maintainers are starting to ship "the agent that knows our docs better than your agent does," and bundling it with the tool itself.

### 3. We should be more tired than the model
**Source: Vicki Boykis (via HN #9)**
<https://vickiboykis.com/2026/05/28/we-should-be-more-tired-than-the-model/>

A short, sharp essay from the author of *What are embeddings*. The thesis: if you've delegated work to an agent all day and feel like you haven't learned anything, you've been doing handoff, not engineering. Not anti-AI — pro-amplifier, anti-substitute. The HN thread is worth reading for the consistent senior-engineer pushback: the more experienced you are, the easier it is to slip into delegation mode and call it productivity.

### 4. Real-time LLM inference on standard GPUs at 3k tokens/s per request
**Source: blog.kog.ai (via HN #8)**
<https://blog.kog.ai/real-time-llm-inference-on-standard-gpus-3-000-tokens-s-per-request/>

A walkthrough of squeezing 3,000 tokens/s per request out of L40S / A100-class hardware by restructuring KV cache memory layout and writing custom attention kernels. With H100 capacity still scarce, this is the kind of work that pays back disproportionately — if you operate inference, the techniques here are worth a regression weekend.

### 5. I think Anthropic and OpenAI have found product-market fit
**Source: Simon Willison's Weblog**
<https://simonwillison.net/2026/May/27/product-market-fit/>

Simon assembles the public evidence — Anthropic's rumored first profitable quarter, the $47B run-rate, and the now-circulating anecdote of a company spending half a billion dollars in a single month on Claude after forgetting to cap usage — and concludes both labs are past PMF. The anecdotes are the leading indicator: when "I forgot to set a limit and we burned $500M" becomes a real sentence, the market has matured.

### 6. Claude Opus 4.8 says it's qwen
**Source: V2EX (CN Claude board)**
<https://www.v2ex.com/t/1216494>

A V2EX user noticed that Opus 4.8 routed through a third-party API reseller introduced itself as qwen. Half the thread laughs, half asks the real question: are some resellers silently downgrading to cheaper models? The honest answer is that self-identification is not a reliable check, and verification (e.g. logprob signatures, watermarks, or a known eval) needs to be part of any procurement that doesn't go direct.

### 7. AI trained me from $0 to $170/month
**Source: V2EX (CN programmer board)**
<https://www.v2ex.com/t/1216578>

A Chinese developer documents how they went from "I'll never pay for AI" to spending 1,200 RMB (~$170 USD) a month across ChatGPT Plus and Claude Code. Replies split predictably between "this just replaces freelancer spend" and "consumerism wearing a productivity costume." Read alongside Simon Willison's piece above and a clearer picture emerges: PMF isn't only at the enterprise tier.

### 8. Datasette 1.0a31 — SQL write queries and stored queries
**Source: Simon Willison's Weblog**
<https://simonwillison.net/2026/May/29/datasette/>

Datasette has long been the read-only SQLite browser. 1.0a31 adds first-class UI support for executing write SQL and saving query templates. For teams that have been hand-rolling small admin UIs over SQLite, Datasette is suddenly a credible drop-in for a chunk of those use cases.

### 9. Is AI causing a repeat of front-end's lost decade?
**Source: mastrojs.github.io (via HN #16)**
<https://mastrojs.github.io/blog/2026-05-23-is-AI-causing-a-repeat-of-frontends-lost-decade/>

The author maps the 2010s front-end story — framework wars, bundle bloat, end-user UX largely unchanged — onto the current agent-tooling boom. The argument: tool-chain progress is being mistaken for product progress, again. Sharp, short, and worth pushing back on if you disagree.

### 10. Orchestrating AI code review at scale
**Source: Cloudflare Blog (via HN #12)**
<https://blog.cloudflare.com/ai-code-review/>

Cloudflare on how they actually run AI code review in production: which PRs qualify, which model to use per category, how to collapse false positives, how to hand off to humans. Substantially more useful than the typical "we tried Claude on PRs" post and worth keeping as a reference if you're scaling agentic review beyond a single repo.

## Editor's note

Two quiet themes today: **agents are moving into the browser and the upstream toolchain** (Kiro Web, Docker Gordon, last week's Dart/Flutter), and **PMF is being proven by invoices** (Simon's piece, the V2EX bill). If you read one thing, read **#3, Vicki Boykis on staying tired** — it's the best framing of the current engineer-with-agent dynamic I've seen this month. If you read two, add **#10 Cloudflare** as your reference architecture for AI code review.

---

*GitHub Trending returned stale cached data today and was excluded. Anthropic's official news page had no new items beyond yesterday's coverage.*
