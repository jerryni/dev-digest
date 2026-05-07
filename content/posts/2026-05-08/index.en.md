---
title: "May 8 · Today's 10 Dev Picks"
date: 2026-05-08T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Claude", "agents", "Anthropic", "Google", "privacy"]
categories: ["daily"]
summary: "Simon Willison breaks down what the xAI/Anthropic Colossus deal actually means, HN argues agents need control flow not more prompts, AI slop debate hits the front page again, Anthropic ships a finance-agents stack, Google DeepMind publishes AlphaEvolve impact, and Chrome quietly retracts its on-device AI privacy claim."
---

## Today at a glance

The thread today is the gap between what AI vendors say and what's actually shipped. Simon Willison digs into the xAI/Anthropic compute deal — confirming Anthropic now leases "all of Colossus" from xAI, an awkward arrangement given the two companies' public posture toward each other. The agent-architecture conversation matures another step on HN with "Agents need control flow, not more prompts" — a useful counter to the "just give the LLM bigger tools" crowd. And on the trust ledger: Chrome silently removed its claim that on-device AI doesn't send data to Google. Read items 1, 2 and 9 if you only have time for three.

---

## 1. Simon Willison: notes on the xAI/Anthropic data center deal

Tag: [EN · Simon Willison]
Link: <https://simonwillison.net/2026/May/7/xai-anthropic/>

The biggest news from yesterday's "Code w/ Claude" event wasn't a new model — it was that Anthropic is renting "all of the capacity" of xAI's Colossus data center. Simon's read: this is a two-sided trade. xAI gets a guaranteed revenue stream during a stretch where its own products are underperforming; Anthropic gets the compute it needs without raising another mega-round. The political optics are awkward (xAI and Anthropic have publicly traded barbs all year), but the math evidently works for both sides. Pair with item 8.

## 2. Agents need control flow, not more prompts

Tag: [EN · HN Top]
Link: <https://bsuh.bearblog.dev/agents-need-control-flow/>

Front page on HN today (235 points). Argument: most agent failures aren't due to weak instructions — they're due to the absence of explicit branching, retries, and termination conditions. The author makes a clean case that we've been hiding control flow inside prompts when it should be code. If your team is debating whether to build agents in LangGraph / DSPy / your-own-state-machine vs. one big system prompt, this post is the cleanest framing of why the state-machine side wins as scope grows.

## 3. AI slop is killing online communities

Tag: [EN · HN Top]
Link: <https://rmoff.net/2026/05/06/ai-slop-is-killing-online-communities/>

Robin Moffatt on the visible degradation of forums, mailing lists and tracker bug reports as low-effort LLM output drowns the signal. The HN comments (255 and counting) are roughly evenly split between "this is overstated" and "we already had to lock down our open source repo because of this." Worth reading not for the headline but for the open question at the end: what's the maintenance burden a project owner can carry before community moderation just collapses?

## 4. V2EX: persistent terminal apps over SSH instead of the browser

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1210713>

A Chinese developer pushes back on the "everything must live in a browser" default and proposes server apps that you reach via a stateful SSH connection — sessions survive disconnects, no auth dance, no frontend tax. The thread is a useful real-world counterweight to the React-everywhere consensus, with the caveat that mobile clients and corporate firewall environments will give you grief. Filed under "things old-school engineers were already doing."

## 5. V2EX: how to call home GPU compute from outside the LAN

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1210806>

The homelab AI question of 2026: the OP has decent local compute (likely a 4090 or M-series) at home and wants to call it from anywhere. Thread surveys Tailscale + Ollama, frp tunnels, ngrok, Cloudflare Tunnel, and self-hosted llama.cpp behind WireGuard. Useful collected wisdom if you're trying to dodge the per-token tax on local-grade workloads — though as several commenters note, residential upload bandwidth is the real bottleneck, not the tunneling layer.

## 6. Zenn: your Claude Code WebFetch isn't actually reading the web

Tag: [JA · Zenn]
Link: <https://zenn.dev/zhizhiarv/articles/claude-code-webfetch-haiku-summary>

A Japanese engineer dug into Claude Code's `WebFetch` and discovered that the tool doesn't return raw page content — it returns a Haiku-summarized version. That means your "agent reading the docs" is reading a summary of the docs, with the lossiness that implies. Significant if you've been writing agentic tasks that depend on exact strings, code blocks, or version numbers from the live page. Workaround in the post: pipe through curl + your own parser.

## 7. Publickey editor's note: a long weekend with Claude Code and Antigravity

Tag: [JA · Publickey]
Link: <https://www.publickey1.jp/blog/26/aigoogle_agent_studioamazon_s3aifoundry_local20264.html>

Buried in the bottom of Publickey's monthly recap is editor Niino's first-person experience using Claude Code and Google Antigravity over Japan's Golden Week. Task: rewrite a defunct external-service call in his own old JavaScript and migrate XHTML to modern HTML. Estimate of unaided time: 2-3 days. Actual time with agents: a fraction of that. The honest tone — neither hype nor dismissal — is the kind of thing that lands harder with skeptical Japanese SI shops than another Anthropic announcement.

## 8. Anthropic: Higher usage limits and the SpaceX/xAI compute deal

Tag: [EN · Anthropic]
Link: <https://www.anthropic.com/news/higher-limits-spacex>

The official side of item 1. Anthropic announced expanded plan limits and confirmed the compute partnership with xAI/SpaceX. Headline numbers in the post: Pro tier limits up materially, Max tier gets even more headroom. If you've been bumping into rate limits on Code w/ Claude or long agent runs, the new ceilings should land in your account this week.

## 9. Google DeepMind: AlphaEvolve scaling impact across fields

Tag: [EN · DeepMind]
Link: <https://deepmind.google/blog/alphevolve-impact/>

DeepMind's report on AlphaEvolve, the Gemini-powered coding-agent system, applied across mathematics, chip design, and infrastructure optimization. The blog claims concrete wins — improvements to Google's data center scheduling, novel proofs in combinatorics, faster matrix multiplication kernels — though without enough detail to fully replicate. The interesting structural point is that AlphaEvolve uses an evolutionary loop with the LLM as a mutation operator, not just chain-of-thought.

## 10. Chrome silently removes claim that on-device AI doesn't send data to Google

Tag: [EN · HN]
Link: <https://old.reddit.com/r/chrome/comments/1t5qayz/chrome_removes_claim_of_ondevice_al_not_sending/>

A Redditor noticed that Chrome's on-device AI documentation used to state that data stays on the device — and the language has now been quietly removed. Google hasn't issued a clarification at the time of writing. The optimistic read is that the wording was over-promised; the cynical read is that on-device AI is, like many things called "on-device," not always strictly on-device. If you've been recommending Chrome's local AI to privacy-sensitive users, time to re-read the policy.

---

## Editor's note

The meta-theme today is honesty about AI plumbing — what the contracts actually say, what the tools actually fetch, what stays on the device versus what doesn't. Items 1 and 8 form a pair you should read together if compute economics in 2026 matters to your roadmap. Item 6 is the most operationally useful for engineers actively building with Claude Code today. Item 10 is the sleeper — small story, large implications for how we should default-trust local-AI vendor copy.
