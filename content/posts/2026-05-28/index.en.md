---
title: "May 28 · Today's 10 Dev Picks"
date: 2026-05-28T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "cloudflare", "llm", "code-agent", "qwen", "dotnet-maui", "vscode", "anthropic", "xai"]
categories: ["daily"]
summary: >-
  Cloudflare productizes its internal SRE stack as Flagship, taking dead aim at Datadog and PagerDuty. A clear-eyed essay on where pure next-token prediction stops working makes the front page. A different post argues the famous 'engineer who can say no' was just a ZIRP-era artifact. V2EX is debating whether domestic Chinese code agents can actually replace Cursor, and whether Qwen3.7-Coder really beat GLM5.1. Publickey reports .NET MAUI is finally migrating from Mono to CoreCLR, and VS Code shipped an Agent window for multi-AI workflows. Wildcards: Anthropic publishes the first Glasswing consortium results, Google ships Gemini 3.5 Flash straight to GA, and xAI's Grok Build enters beta with parallel sub-agents.
---

## Today at a glance

The throughline today is **agents leaving the chat box**. VS Code's Agent window, xAI's parallel sub-agents in Grok Build, and the V2EX debate about Chinese code agents are all pointing at the same near-future: by H2 2026, the IDE will be "editor plus a team of AI workers" rather than "editor plus a copilot." Around that center, two infra-layer shifts deserve attention: Cloudflare walking directly into Datadog's territory, and .NET MAUI dropping the Mono runtime for CoreCLR. If you only have time for two pieces today, take #2 (the technical case for why agents are inevitable) and #3 (the organizational case for the same).

## 1. Cloudflare productizes its internal SRE stack as Flagship

[Cloudflare Flagship](https://developers.cloudflare.com/flagship/) · `HN 199`

Cloudflare has been running its own incident management, observability, and runbook automation stack internally for years. Today they're packaging it for customers as Flagship and aiming straight at Datadog and PagerDuty. The pitch is concrete rather than aspirational: "we use this to run 20% of global internet traffic, daily." For Workers-first shops the switching cost is already low. Datadog renewal conversations get more interesting next quarter.

## 2. Where does next-token prediction leave us?

[Where does next-token prediction leave us?](https://pop.rdi.sh/where-does-next-token-prediction-leave-us/) · `HN 175`

A calm post that maps out what pure next-token prediction can and cannot do in 2026. The author concedes scaling still works in some dimensions, then walks through long-horizon planning, tool use, and self-verification — places where another 10x of compute doesn't close the gap. This is the cleanest explanation I've seen for why the entire industry has shifted to agent frameworks plus RL post-training. Useful citation material for internal strategy docs.

## 3. The 'just-say-no engineer' was a ZIRP phenomenon

[The just-say-no engineer was a ZIRP phenomenon](https://www.seangoedecke.com/the-just-say-no-engineer-was-a-zirp-phenomenon/) · `HN 130`

Sean argues that the senior engineer who could push back on PMs was a product of the 2015–2022 zero-rate, talent-scarce regime. Once capital got expensive, companies stopped tolerating that profile and started rewarding the engineer who ships first and complains later. Whether you agree or not, it's a sharper diagnosis than most of the AI-replaces-engineers takes — and it'll change how you read every "are we cooked" thread for the next six months.

## 4. V2EX debates: can domestic Chinese code agents actually compete?

[Is there any Chinese code agent that actually works?](https://www.v2ex.com/t/1215881) · `V2EX 41`

The thread asks whether anything from Chinese vendors — ByteDance MarsCode, Zhipu GLM, Alibaba Tongyi Lingma, DeepSeek-derived tools — can replace Cursor or Claude Code for serious work. The rough consensus from the replies: autocomplete is at parity, but multi-file refactors and long-horizon plan-execute still lag noticeably. For Western engineers managing offshore teams in China, this thread is a useful reality check on what tooling those teams are actually shipping with.

## 5. Did Qwen3.7-Coder really beat GLM5.1?

[Qwen3.7 supposedly beat GLM5.1 on coding — has anyone tried it?](https://www.v2ex.com/t/1215786) · `V2EX 28`

LiveCodeBench and SWE-Bench Verified put Qwen3.7-Coder above GLM5.1, but the V2EX reports are mixed: Qwen feels more idiomatic in React/TypeScript work, GLM more stable on large Java codebases. Benchmark drift is normal in 2026, and Chinese developers have already built the habit of running two coding models in rotation. That habit hasn't really crossed over to Western teams yet, and it might be time.

## 6. .NET MAUI is finally migrating from Mono to CoreCLR

[.NET MAUI moves from Mono to CoreCLR](https://www.publickey1.jp/) · `Publickey`

The largest single piece of legacy in cross-platform .NET — the Mono runtime — is finally being replaced wholesale by CoreCLR. MAUI apps will get the same GC and JIT improvements that ASP.NET Core has been compounding for years, with meaningful wins in startup time and memory footprint. Good news for shops still maintaining Xamarin-era apps. iOS AOT will need full compatibility re-testing, so factor that into any migration plan.

## 7. VS Code ships Agent window for multi-AI workflows

[Visual Studio Code releases Agent window preview](https://www.publickey1.jp/) · `Publickey`

The VS Code May 2026 release added a new window type called Agent window, designed to run multiple AI agents on independent tasks in parallel without disrupting the main editor — Claude Code on the backend, Copilot on tests, your own scripted agent on docs. Before this you had to glue several extensions together. Worth testing under VS Code Server / SSH if your team does remote dev — agent lifecycle across reconnects is the obvious failure mode.

## 8. Anthropic publishes first Project Glasswing results

[Project Glasswing: An initial update](https://www.anthropic.com/research/glasswing-initial-update) · `Anthropic`

The April-formed Glasswing consortium (AWS, Anthropic, Apple, Cisco, CrowdStrike, Google, JPMorgan, Linux Foundation, Microsoft, NVIDIA, Palo Alto Networks) released its first deliverables: attack-surface modeling whitepapers for critical software, and a public vulnerability database focused on AI training pipelines. This is the first cross-vendor effort in 2026 with real teeth on AI-supply-chain security; SBOM tool vendors should be plumbing it into their pipelines.

## 9. Google ships Gemini 3.5 Flash straight to GA

[Gemini 3.5 Flash, generally available](https://simonwillison.net/) · `Simon Willison`

Google skipped the preview phase on Gemini 3.5 Flash and went straight to GA at I/O. Simon's bench notes: context window is much more stable under tool-call pressure than 2.5 was, TTFT under 200ms (a real shift for voice agents), pricing positioned a tick below the equivalent Sonnet tier. Expect mid-tier API costs to compress across the board over the next two months.

## 10. xAI's Grok Build enters beta with parallel sub-agents

[xAI Grok Build enters beta](https://www.publickey1.jp/) · `Publickey / xAI`

xAI's coding agent Grok Build is in beta, and the headline feature is **parallel sub-agents** — a main agent forks multiple children to work independent tasks, with results merged at the coordinator. Children are isolated via git worktree, which is interesting because it sidesteps the locking headaches Claude Code's subagent mode runs into. Whether it dents Claude or Cursor share is unclear, but "sub-agents as a first-class feature" is now table stakes across the field.

## Editor's note

The meta-theme today is **agents have moved beyond the chat box**. Agent window, parallel sub-agents, and the V2EX debate over Chinese code agents all point at the same future: an IDE is no longer "editor plus a copilot," it's "editor plus a team of AI workers." Today's must-reads are **#2 on the limits of next-token prediction** and **#3 on the ZIRP-era engineer**. Read the first to understand why agents are technically inevitable; read the second to understand why organizations no longer have a choice about adopting them.
