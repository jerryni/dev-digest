# Daily Digest Generation Playbook

This document is the **spec for the scheduled task** that generates a new digest every morning at 07:00 Tokyo time. The scheduled task's prompt will tell Claude to read this file and execute it.

---

## 1. Sources (精简版 · v1)

Claude should fetch from these sources in this priority order:

| # | Source | Language | What to pull | URL |
|---|--------|----------|--------------|-----|
| 1 | **Hacker News** | EN | Top 10 stories | `https://hacker-news.firebaseio.com/v0/topstories.json` (API) or `https://news.ycombinator.com/` |
| 2 | **GitHub Trending** | EN | Daily trending repos, top 10 | `https://github.com/trending?since=daily` |
| 3 | **Simon Willison** | EN | Latest post if published in last 24h | `https://simonwillison.net/atom/everything/` |
| 4 | **V2EX 热门** | ZH | Top threads from /?tab=hot | `https://www.v2ex.com/?tab=hot` |
| 5 | **Zenn Trending** | JA | Daily trending articles | `https://zenn.dev/` |
| 6 | **Publickey** | JA | Latest posts if any new | `https://www.publickey1.jp/atom.xml` |
| 7 | **Anthropic / OpenAI / Google DeepMind blogs** | EN | Any official posts in last 24h | RSS feeds respectively |

## 2. Daily workflow

For each daily run, Claude must:

### Step 1 — Fetch & dedup
1. Pull raw items from each source (parallel WebFetch/WebSearch calls).
2. Deduplicate across sources: if the same URL or clearly-same story appears in multiple sources, keep one and note the cross-reference.
3. Discard items that are: obvious spam / promotional / recruiting / paywalled with no public summary / political flame.

### Step 2 — Rank & select
1. Score each surviving item by: technical depth, novelty (is this the FIRST time I'd mention this?), cross-cultural relevance, actionability.
2. Pick **exactly 10** items, ensuring source diversity — avoid picking 6 from HN and 1 from elsewhere. Aim for roughly:
   - 3 EN from HN / GitHub Trending / Simon Willison
   - 2 ZH from V2EX
   - 2 JA from Zenn / Publickey
   - 3 wildcard from AI company official blogs, whichever has fresh news today
3. If a source has nothing noteworthy, shift the slot to another source rather than forcing a weak pick.

### Step 3 — Write three independent language versions (路线 C)

**CRITICAL**: Do NOT translate. Write each language for its native reader.

For each of Chinese / Japanese / English:
- Pick the title style appropriate for that audience (ZH: "X月X日 · 今日技术精选"; JA: "X月X日 · 今日のテック厳選10本"; EN: "Month D · Today's 10 Dev Picks").
- Write a short "今日速览 / 本日のサマリー / Today at a glance" intro (2-3 sentences) that frames the themes for that specific readership. E.g., the Chinese version can reference China-market implications; the Japanese version can reference 日本企業 context; the English version speaks to the global dev audience.
- For each of the 10 items: headline + source tag + link + 2-4 sentence contextual blurb. The blurbs should differ across languages — same facts, but framing/analogies/concerns relevant to that culture.
- Close with an 编者按 / 編集後記 / Editor's note: 2-3 sentences identifying the day's meta-theme and recommending the top 1-2 "must read" items.

### Step 4 — File naming & front matter

Create three files under `content/posts/YYYY-MM-DD/`:
- `index.zh.md`
- `index.ja.md`
- `index.en.md`

Front matter template (swap strings per language):

```yaml
---
title: "..."
date: YYYY-MM-DDT07:00:00+09:00
draft: false
tags: ["digest", "YYYY-MM", <topical tags>]
categories: ["daily"]
summary: "..."
---
```

### Step 5 — Commit & push

From the repo root:

```bash
git add content/posts/YYYY-MM-DD/
git commit -m "digest: YYYY-MM-DD"
git push origin main
```

GitHub Actions will build and deploy automatically (~2 min).

### Step 6 — Sanity check

After push, confirm:
- Three files exist under the new date folder.
- Git commit is on `main` and the push succeeded (check `git status` and `git log -1`).
- Print the deployed URL: `https://jerryni.github.io/dev-digest/zh/posts/YYYY-MM-DD/`

## 3. Failure handling

- **Source unreachable**: skip it, continue with the rest. Note in editor's note that "source X was unavailable today".
- **All sources unreachable**: create a minimal placeholder post noting the outage; commit anyway (the daily streak matters, and the error log is valuable context).
- **Push fails (auth)**: stop. Report the error so the user can fix credentials — do NOT retry silently. This is a signal that PAT may have expired.
- **Duplicate day**: if `content/posts/YYYY-MM-DD/` already exists, update the existing files rather than creating new ones. Use git to amend or create a new commit like `digest: YYYY-MM-DD (update)`.

## 4. Tone guide per language

- **中文版**：简洁、直给、偶尔一句吐槽也 OK。目标读者是北美/日本的华人开发者 + 国内开发者双圈。避免"干货满满"这类过度营销词。
- **日本語版**：敬体でもカジュアルでも一貫していれば OK。ですます調を基本、たまに体言止め。日本の技術者が普段読んでいる記事のトーン（Zenn・Publickey 寄り）。
- **English**：Crisp, technical, slightly opinionated. Mid-career engineer audience. Avoid buzzword soup ("revolutionary", "game-changing") — let the facts speak.

## 5. Things to explicitly NOT do

- ❌ Do not run the same English text through translation for ZH and JA — write independently.
- ❌ Do not pad to hit exactly 10 if only 7 items are genuinely worth reading. It's fine to publish fewer with a note about why.
- ❌ Do not commit `public/` or `.hugo_build.lock` — they're in `.gitignore`.
- ❌ Do not include emoji in tags (breaks some feed readers).
- ❌ Do not write "As an AI, I..." anywhere. The editorial voice is "Dev Digest editor".
