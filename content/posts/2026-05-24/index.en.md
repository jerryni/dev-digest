---
title: "May 24 · Today's 10 Dev Picks"
date: 2026-05-24T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "memory-shortage", "ai-privacy", "supply-chain", "anthropic"]
categories: ["daily"]
summary: >-
  HBM eats into consumer memory wafers — cheap smartphones are about to get pricier. Opus 4.7 can reconstruct your real identity from writing style alone. Daniel Lemire shows how to beat binary search on modern CPUs. Zenn trending is dominated by Claude token-saving tactics and Vibe-Coding supply-chain attacks. Anthropic publishes Project Glasswing's first six-month report. cPanel has an actively exploited bug. Today's thread — AI is forcing a recalibration of every yardstick we use, from price tags to privacy defaults to engineering KPIs.
---

## Today at a glance

Today's items map cleanly to four layers — physical (HBM crowds out DDR/LPDDR), model (Opus 4.7 reads identity from prose), process (does commit-count survive AI?), and governance (Glasswing's first audit, in-the-wild cPanel exploitation). Each layer is being repriced by AI in some form. The two most actionable items for engineering leaders: rethinking long-horizon memory procurement budgets, and assuming "anonymous" inputs to any frontier model are no longer anonymous.

## 1. The memory shortage is repricing consumer electronics

[The memory shortage is causing a repricing of consumer electronics](https://davidoks.blog/p/ai-is-killing-the-cheap-smartphone) · `Simon Willison / David Oks`

Three companies make the world's RAM. Their wafer capacity is fixed, and HBM (the memory bolted to GPUs) is forecast to jump from 2% of allocation to 20% by the end of 2026. Each gigabyte of HBM consumes 3x the wafer area of LPDDR/DDR. The first casualty is the sub-$100 smartphone, with knock-on effects through emerging markets. Bookmark this for your next discussion about AI's externalities — it's the clearest framing of the trade-off so far.

## 2. Opus 4.7 reconstructs identity from writing style

[Opus 4.7 knows the real Kelsey](https://www.theargumentmag.com/p/i-can-never-talk-to-an-ai-anonymously) · `The Argument Magazine / HN`

Kelsey Piper logged in to Claude with a stripped-down anonymous account and the model still surfaced her real name and beat within a few turns — extrapolating from vocabulary, phrasing, and topic affinity. Her conclusion: anonymous chat as a UX promise is already broken at the frontier. Worth reading if your product surface still ships an "incognito" mode and you assume the model treats it as such.

## 3. You can beat binary search

[You can beat the binary search](https://lemire.me/blog/2026/04/27/you-can-beat-the-binary-search/) · `lemire.me / HN`

Daniel Lemire rewrites `lower_bound` to use conditional moves instead of branches and gets 20-40% wins over `std::lower_bound` on million-element arrays. The takeaway isn't that binary search is wrong — it's that branch-prediction penalties on modern x86 dominate the asymptotic story for small-to-medium arrays. Ten-minute read for anyone with hot lookup paths.

## 4. Anthropic publishes Project Glasswing's first audit

[Project Glasswing: An initial update](https://www.anthropic.com/research/glasswing-initial-update) · `Anthropic`

Glasswing — the AWS / Apple / Google / Microsoft / CrowdStrike / JPMorgan / Linux Foundation coalition using Claude to audit critical OSS — drops its six-month update: CVEs fixed, coordination workflow with maintainers, and an oblique response to the NHS pulling several repos private. The interesting thing is less the numbers than the precedent: AI-assisted security review is becoming an institutional layer of infrastructure, not just a research demo.

## 5. Hackers are actively exploiting a cPanel/WHM bug

[Hackers are actively exploiting a bug in cPanel and WHM](https://techcrunch.com/2026/04/30/hackers-are-actively-exploiting-a-bug-in-cpanel-used-by-millions-of-websites/) · `TechCrunch / HN`

cPanel powers a huge fraction of shared hosting worldwide. There is an in-the-wild exploit, working PoCs are circulating, and patch deployment is the action item for today. If you run anything that even touches cPanel through a reseller, check root SSH logs and recent webshell uploads alongside the patch.

## 6. The EFF and the AT&T whistleblower

[How Mark Klein told the EFF about Room 641A (book excerpt)](https://thereader.mitpress.mit.edu/the-whistleblower-who-uncovered-the-nsas-big-brother-machine/) · `MIT Press Reader / HN`

MIT Press releases an excerpt covering how AT&T technician Mark Klein delivered the Room 641A documentation to the EFF in 2006. Read alongside the Opus 4.7 identity story above: in 2006 the threat was a literal fiber tap inside a telco; in 2026 the threat is a frontier model inferring identity from prose. The mechanism evolved; the loss of anonymity didn't.

## 7. V2EX · Has commit-count survived AI?

[自从有了 AI 之后，Commit 数量是不是已经不适合衡量开发效率了](https://www.v2ex.com/t/1214914) · `V2EX`

A Chinese-language dev thread that splits cleanly: one camp says commit-count is now inflated by AI-generated noise; another argues that PR-acceptance rate and incident frequency are the right post-AI metrics; a third just calls for retiring any KPI that AI can trivially game. If your org's OKRs still bake in commit-count as a proxy, this is the discussion you'll be having in six months — get ahead of it.

## 8. V2EX · qwen3.7-max changes the China-side conversation

[qwen3.7-max 的代码能力提升非常大](https://www.v2ex.com/t/1214878) · `V2EX`

Practitioner reports on qwen3.7-max put it close to Claude Sonnet 4.6 on a non-trivial refactor benchmark, with broad agreement that this is a real generational step rather than a benchmark gain. With Alibaba Cloud's token plan, it's also directly callable inside China. For global teams with China-side customers or partners, expect "try qwen first" to become a default ask this quarter.

## 9. Zenn trending · Saving Claude Max 20x tokens

[Claude Max 20xプランでも足りないので、トークン節約のためにやったこと8選](https://zenn.dev/acntechjp/articles/1396e20b5167ce) · `Zenn / Accenture Japan`

Accenture Japan engineers ran out of Claude Max 20x quota and wrote up eight token-saving tactics — context layering, cache-hit shaping, plan-with-cheap-model-then-execute-with-expensive-model, when to `/clear`, and so on. The interesting subtext: the $200/month plan is no longer trivially "enough", and the bottleneck has shifted from budget to optimization skill.

## 10. Zenn trending · Vibe-coding supply-chain attacks

[Vibe Coding 時代のサプライチェーン攻撃と防御方法](https://zenn.dev/loglass/articles/c619f704045181) · `Zenn / Loglass`

Loglass's security team catalogs supply-chain attacks specific to AI-generated code: slopsquatting (registering packages the model hallucinates), prompt-injected lockfile rewrites, IDE extensions performing silent installs. Pair with this week's PyTorch Lightning Shai-Hulud incident and you have a workable pre-deployment checklist for coding-agent rollouts.

## Editor's note

Today's meta-theme: AI is forcing a recalibration of every default we'd stopped questioning — memory price curves, what "anonymous" means, what commit-count measures, whether O(log n) is the floor. Two must-reads: the **memory-shortage piece** (it'll change how you scope multi-year hardware budgets) and the **Opus 4.7 / Kelsey story** (rethink any product surface that promises anonymity). Today's Zenn API results were drawn from monthly-trending and skew about a month old, but the two we included are genuinely useful. GitHub Trending returned an empty body for today's fetch, so it's omitted.
