---
title: "April 28 · Today's 10 Dev Picks"
date: 2026-04-28T07:00:00+09:00
draft: false
tags: ["digest", "2026-04", "ai", "agents", "openai", "microsoft", "github-copilot", "ruby", "security", "claude-code"]
categories: ["daily"]
summary: "A heavy Tuesday. HN's #1 is the formal end of Microsoft and OpenAI's exclusive partnership and revenue-share — the AGI clause is now history. GitHub Copilot moves to usage-based billing (HN 532 pts, 408 comments). Mercor's 4TB voice-sample leak puts 40k AI annotators on the public web. pgbackrest stops maintenance and the Postgres community begins migrating. Microsoft drops VibeVoice on MIT — a Whisper-class ASR model with diarization that runs on a Mac with one `uv` line. Two strong Japan picks: Matz's own Ruby AOT compiler Spinel, and the CAMPFIRE GitHub-credentials breach postmortem."
---

## 🌐 Today at a glance

The day's biggest story is structural: **Microsoft and OpenAI formally end the exclusive compute / revenue-share partnership** that defined AI infra for the last seven years. HN #1 with 737 points and 648 comments. Simon Willison wrote a [companion archeology post](https://simonwillison.net/2026/Apr/27/now-deceased-agi-clause/) tracking the history of the AGI clause — the strange contractual provision saying that if AGI were ever achieved, Microsoft's commercial IP rights would extinguish — which is now also formally dead. Hitting developers more directly: **GitHub Copilot moves to usage-based billing** (HN 532 pts, 408 comments). The "fixed monthly seat for unlimited use" era is over; CFOs will be reopening spreadsheets this week. Two security stories worth pairing: **Mercor's 4TB leak** of voice samples from 40,000 AI annotators (HN 431 pts) and the **microsoft/VibeVoice** drop — an MIT-licensed Whisper-class ASR model with built-in diarization that Simon got running on a Mac with a single `uv` command. Read those side by side and the implication is uncomfortable: leaked training-grade voice data plus an MIT-licensed model lowers the bar from "interesting research artifact" to "anyone can fine-tune." On the infrastructure side, **pgbackrest is no longer being maintained** (HN 392 pts) — a major Postgres backup tool now in fork-or-migrate mode. The undercurrent: AI's commercial scaffolding is repricing, AI's compliance debt is starting to come due, and core OSS infra is wearing through its bus factor.

---

## 🔥 Today's 10

### 1. [Hacker News / Bloomberg] Microsoft and OpenAI end exclusive and revenue-sharing deal
**Link:** https://www.bloomberg.com/news/articles/2026-04-27/microsoft-to-stop-sharing-revenue-with-main-ai-partner-openai
HN #1 today (737 points, 648 comments). The 2019-vintage agreement under which Microsoft was OpenAI's exclusive cloud provider in exchange for an estimated 20% revenue share is being dismantled in stages, with both companies free to pursue independent partnerships. Simon Willison's [companion piece](https://simonwillison.net/2026/Apr/27/now-deceased-agi-clause/) is the best context read of the day: he traces the AGI clause through openai.com edits over the years and shows how its language drifted as both parties got closer to having a serious commercial reason to fight about what "AGI" actually means. Practical implication for infra teams: OpenAI is now free to take large compute commitments to AWS / GCP / Oracle, Microsoft is freer to lean into Anthropic and its own models, and the Azure-default assumption baked into many enterprise AI procurement decks is now wrong by default. If your 2026 AI roadmap assumed exclusivity in either direction, it's stale as of today.

### 2. [Hacker News / GitHub Blog] GitHub Copilot moves to usage-based billing
**Link:** https://github.blog/news-insights/company-news/github-copilot-is-moving-to-usage-based-billing/
HN #22 (532 points, 408 comments). Per-seat unlimited is over; from this rollout, Copilot meters by token. The comment thread splits cleanly: "this is finally honest pricing for the agent era" vs. "engineering org budgets just became unforecastable." The most useful thread takeaway: build a per-team token-consumption dashboard *this week*, before the first surprise invoice. Read alongside today's [Claude Pro Opus rate-limit change](https://support.claude.com/en/articles/11940350-claude-code-model-configuration) on HN and the message is consistent across vendors: AI coding tools have collectively crossed into the metered era. The downstream consequence worth flagging: tools that used to look "free at the margin" to engineers are now visibly priced at every keystroke, which will pressure how teams decide between Copilot, Claude Code, Cursor, and OpenAI Codex on individual tasks rather than as blanket subscriptions.

### 3. [Simon Willison / Microsoft] microsoft/VibeVoice — MIT-licensed Whisper alternative
**Link:** https://github.com/microsoft/VibeVoice
Microsoft released this Whisper-style ASR model in January but Simon only got to it today, and the [writeup](https://simonwillison.net/2026/Apr/27/vibevoice/) is the cleanest "try it now" doc you'll find. MIT license, speaker diarization built into the model, and the on-device numbers are concrete: 8m45s to transcribe one hour of audio on a 128GB M5 Max MacBook Pro, with 30GB peak memory. The Mac one-liner is worth saving: `uv run --with mlx-audio mlx_audio.stt.generate --model mlx-community/VibeVoice-ASR-4bit --audio lenny.mp3 ...`, and the output JSON ships with `start`, `end`, and `speaker_id` per segment. The catch: 1-hour limit per invocation, so longer audio needs chunking with overlap. For teams currently paying AWS Transcribe / Azure Speech for compliance-sensitive transcription workflows, this is a credible swap-in candidate — especially given the licensing.

### 4. [V2EX] Self-hosted AI token proxy for Codex / Claude Code
**Link:** https://www.v2ex.com/t/1208203
A Chinese developer publishes their self-hosted token-proxy stack — primarily a workaround for Claude Code / Codex availability and pricing inside China, but the broader pattern is what's interesting. The proxy lets them route requests across Claude, OpenAI, DeepSeek V4, and GLM 5.1 with token-budgeting, rate-limiting, and per-team accounting. Read this *together with* today's #2 (Copilot's metered pricing) and you see the same problem solved on two continents with different cultural defaults: Western devs comment, Chinese devs build a router. For startup CTOs feeling the AI-bill squeeze, the architecture pattern is worth borrowing — explicit routing layer, fallback model, per-call accounting — even if the geographic constraints don't apply.

### 5. [V2EX / Zenn] OpenCode — the open-source Claude Code alternative
**Link:** https://www.v2ex.com/t/1204410
A solid Chinese-language guide to [sst/opencode](https://github.com/sst/opencode), pluggable across Gemini 3 Pro, Claude 4.5 Opus, DeepSeek V4, GLM 5.1. Notably, [a Japanese-language OpenCode writeup](https://zenn.dev/xxishan/articles/9cb47819f835fa) hit Zenn the same day with 31 likes — the "Claude Code is great but expensive" gap is being filled in parallel across markets. The pragmatic adoption pattern emerging across both communities: keep Claude Code (or Cursor) for high-stakes work, route routine refactors / boilerplate / explore-and-summarize through OpenCode + a cheaper model. The cost discipline this enforces — explicitly choosing tier per task — is a reasonable forcing function regardless of which OSS tool you actually pick.

### 6. [Zenn] Trying out Matz's Ruby AOT compiler "Spinel"
**Link:** https://zenn.dev/geeknees/articles/edc3cb36ea251c
Yukihiro Matsumoto (Matz) — Ruby's creator — is personally building an AOT compiler for Ruby, and a Japanese developer has the first public hands-on writeup. The post is structured the way you'd want: local build steps, benchmarks vs. interpreted Ruby and YJIT, and an explicit list of dynamic features Spinel doesn't support yet. For Rails-shop CTOs the question this raises is "what's the next chapter after YJIT," and Spinel is now a serious answer to track. Worth noting that Matz's direct involvement is itself a signal — this is plausibly the path Ruby-the-language will commit to, not just one of several research forks.

### 7. [Zenn] CAMPFIRE 225k-user breach — what to learn from a GitHub-credentials leak
**Link:** https://zenn.dev/awesome_kou/articles/campfire-github-breach-2026
CAMPFIRE, Japan's largest crowdfunding platform, leaked 225,000 users' personal data after attackers obtained GitHub credentials (likely a stolen PAT or OAuth token). The Zenn writeup is unusually well-structured: incident reconstruction plus a generalizable checklist — scan historic commits with [trufflehog](https://github.com/trufflesecurity/trufflehog), PATs must be minimum-scope and short-lived, CI shouldn't carry long-lived tokens. The 30-minute action item for any reader: run trufflehog on your team's public repos today. The historical-commit search is the cheapest, highest-leverage security work most engineering orgs aren't doing on a regular schedule, and this is your reminder.

### 8. [Hacker News] 4TB of voice samples stolen from 40k AI contractors at Mercor
**Link:** https://app.oravys.com/blog/mercor-breach-2026
HN #12 today (431 points, 160 comments). Mercor supplies expert annotation and human data to most major AI labs, and the leaked 4TB reportedly includes voice samples from ~40,000 contractors used in RLHF and speech-model training. The interesting question isn't the data volume — it's the consent question: do the original contractor agreements cover "downstream third-party fine-tuning after data exfiltration"? Almost certainly not. Pair this with #3's MIT-licensed VibeVoice and the failure mode is visible: leaked training-grade voice corpus plus a free, permissively-licensed ASR / diarization model is the shortest path from breach to weaponized voice cloning we've seen. Compliance teams should be asking every AI data vendor in their stack for incident-response and audit-log evidence this week, not next quarter.

### 9. [Hacker News] pgbackrest is no longer being maintained
**Link:** https://github.com/pgbackrest/pgbackrest
HN #24 (392 points, 204 comments). One of the most widely-deployed PostgreSQL backup tools is now unmaintained per a maintainer note. The Postgres community is splitting into fork-it and migrate-to-alternatives camps (pg_basebackup, barman, wal-g). What you should actually do: (1) don't panic — existing deployments keep working; (2) put a 90-day migration evaluation on the calendar; (3) if you have someone who could be a maintainer, the [issue tracker](https://github.com/pgbackrest/pgbackrest/issues) is the entry point. The deeper story is the same OSS bus-factor problem we've been ignoring while everyone's attention was on AI infrastructure — and backup tooling is the worst possible category to discover that problem in production.

### 10. [Hacker News] Show HN: Dirac — OSS agent that topped TerminalBench on Gemini-3-flash-preview
**Link:** https://github.com/dirac-run/dirac
HN #25 (293 points, 118 comments). A solo developer's open-source agent ranks #1 on TerminalBench using Gemini 3 Flash Preview, beating commercial offerings. The codebase is roughly 3k lines of Python — a tight tool-calling loop, structured logs, and disciplined error handling. Two takeaways worth carrying into your own work: (a) SOTA-level agent harnesses are smaller than most teams assume — the complexity is in the discipline, not the volume of code; (b) a small fast model with a well-shaped harness can credibly beat a larger model with a generic harness on vertical benchmarks, which has implications for how to think about cost / latency tradeoffs in agent product design. If you're building agent infrastructure, this is a one-hour read that will probably suggest places to cut your own LOC.

---

## ✍️ Editor's note

Today's picks cluster around two themes. **First: the commercial scaffolding under AI is repricing, all at once.** The Microsoft / OpenAI uncoupling (#1) is the macro signal, GitHub Copilot's metered pricing (#2) is the developer-facing signal, and the Chinese token-proxy (#4) and OpenCode adoption pattern (#5) are the bottom-up signal — three layers of observers reaching the same conclusion: AI inference cost was being subsidized somewhere, and the subsidy is unwinding. **Second: AI's compliance debt is starting to come due.** The Mercor voice-data breach (#8) plus the CAMPFIRE GitHub-credentials breach (#7) plus the MIT-licensed VibeVoice release (#3) compose into one uncomfortable picture — leaked training data, plus a free permissive model, plus motivated attackers, equals nonlinear risk growth. The pgbackrest (#9) story is on a different timeline but rooted in the same neglect: OSS critical infrastructure has a bus-factor problem that AI's narrative gravity is making worse, not better.

**Must-reads today:**
1. **MS / OpenAI uncoupling (#1)** — read this if you have any AI procurement decision in flight.
2. **Copilot moves to usage-based billing (#2)** — build the per-team token dashboard this week, not next month.

— Dev Digest editor
