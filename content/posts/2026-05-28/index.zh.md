---
title: "5月28日 · 今日技术精选"
date: 2026-05-28T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "cloudflare", "llm", "code-agent", "qwen", "dotnet-maui", "vscode", "anthropic", "xai"]
categories: ["daily"]
summary: >-
  Cloudflare 把内部 SRE 工具拆出来做成商品「Flagship」直接对标 Datadog。一篇博客把下一代 token 预测的天花板讲清楚——LLM 正在从「会说」转向「会做」。HN 一篇"敢说不的工程师只是零利率时代的副作用"在中年程序员圈子里刷屏。V2EX 上两条讨论分别在拷问：国产 code agent 还能不能打、Qwen3.7 是不是真比 GLM5.1 强。Publickey 报道 .NET MAUI 终于丢掉 Mono 迁到 CoreCLR；VS Code 推出"Agent window"，多 AI 协作终于有了原生 UI。三条 wildcard：Anthropic 公布 Glasswing 联盟首批成果；Google Gemini 3.5 Flash 直接 GA 跳过 preview；xAI 的 Grok Build 进 beta，能并行起多个 sub-agent。
---

## 今日速览

今天的主线是**两条**：一是基础设施层的洗牌（Cloudflare 直接走进 Datadog 的腹地，.NET MAUI 重写运行时），二是 AI agent 终于从「一个聊天框」演化成「一个工作环境」——VS Code 的 Agent window、xAI 的并行 sub-agent、V2EX 上关于 Cursor / 国产替代的吵架，都是同一件事的不同面。中文读者额外关注两点：Qwen3.7 在 V2EX 上被严肃讨论是不是真把 GLM5.1 超过了，以及国产 code agent 落地到底有没有真的好用——这两条比纯英文圈讨论要诚实得多。HN 上"敢说不的工程师只是零利率副作用"那篇，特别值得国内卷在年龄/裁员焦虑里的工程师读一读。

## 1. Cloudflare 把内部 SRE 工具产品化为「Flagship」

[Cloudflare Flagship](https://developers.cloudflare.com/flagship/) · `HN 199`

Cloudflare 一直自己内部用一套 SRE 工具栈（事件管理、可观测、运行手册自动化），现在直接拆出来卖给客户，名字叫 Flagship。位置很明确：和 Datadog / PagerDuty 撞车，但卖点是「Cloudflare 自己每天用它扛 20% 的全球互联网流量」。值得关注的不是产品本身，而是 Cloudflare 这几年的打法——先免费送 Workers 把流量吸过去，再把内部工具一个个商品化。腾讯云、阿里云的 PaaS 团队应该研究一下这套节奏。

## 2. 下一代 token 预测会把我们带到哪里

[Where does next-token prediction leave us?](https://pop.rdi.sh/where-does-next-token-prediction-leave-us/) · `HN 175`

一篇很冷静的博客，作者梳理了纯 next-token prediction 这条路径在 2026 年的处境：scaling law 在某些维度仍然有效，但越来越多任务（长 horizon planning、工具使用、自我验证）已经不是单靠"再大十倍"能解决的，行业事实上已经全员转向 agent 框架 + RL post-training。这篇不是又一篇"LLM 已死"的标题党，作者举的反例都有数据支撑，建议对照看一下 Anthropic 最新关于 RL on agent rollouts 的论文。

## 3. "敢说不的工程师"只是零利率时代的副作用

[The just-say-no engineer was a ZIRP phenomenon](https://www.seangoedecke.com/the-just-say-no-engineer-was-a-zirp-phenomenon/) · `HN 130`

作者的观点很扎心：那种"我有底气拒绝产品经理乱提需求"的工程师人设，本质上是 2015–2022 零利率时代供给端短缺的产物。资本一旦变贵，公司对"工程师能力 = 能 say no"的容忍度就消失了，留下来的反而是那些「先把活干了再吐槽」的人。这篇在国内中年程序员圈也成立——只是把时间线挪后五年。读完别马上发朋友圈，想想自己最近一次说"不"是为了什么。

## 4. V2EX 在吵：国产 Code Agent 到底有没有能打的

[兄弟们，国产 Code Agent 到底有没有能打的？](https://www.v2ex.com/t/1215881) · `V2EX 41`

楼主直接问：除了 Cursor / Claude Code，国产替代里有没有真的能干活的。回帖里高频出现的是字节的 MarsCode、智谱的 GLM 系列、阿里通义灵码、以及深度求索 (DeepSeek) 的 R2 衍生工具。共识大致是：自动补全这一段国产已经追上，但**多文件重构 + 长上下文 plan-execute**这一段还有明显差距。值得读评论区里讨论"为什么不付费用 Cursor"的那一支——很多用户已经在用国内中转站 + Claude API 的方式回避地理限制。

## 5. Qwen3.7 编码排名真超过 GLM5.1 了？

[Qwen3.7 编码排名超过了智谱 GLM5.1，有人用过吗？](https://www.v2ex.com/t/1215786) · `V2EX 28`

LiveCodeBench 和 SWE-Bench Verified 上 Qwen3.7-Coder 的最新数确实在 GLM5.1 之上，但 V2EX 实测帖里出现了挺多不一致的反馈：有人觉得 Qwen 在 React/TypeScript 项目里更"懂行话"，有人觉得 GLM 在 Java 大型代码库里更稳。Benchmark 漂移已经是 2026 年常态，国内开发者反而比海外更早形成了"两个模型轮换用"的 muscle memory。这条值得关注的是：阿里和智谱在国内开发者心智里的位置已经从「先用谁有补贴」变成「按代码风格选」。

## 6. .NET MAUI 终于离开 Mono 迁到 CoreCLR

[.NET MAUI 将运行时由 Mono 迁移到 CoreCLR](https://www.publickey1.jp/) · `Publickey · JA`

跨平台 .NET 历史包袱里最大的一块——Mono 运行时——终于要被 CoreCLR 全面替换。意味着 MAUI 上的应用以后能拿到和 ASP.NET Core 一样的 GC / JIT 优化，启动时间和内存占用都会有显著改善。这件事对国内还在维护 Xamarin 遗留项目的团队是个好消息：迁移路径终于不再是死胡同。但要注意：iOS 上 AOT 的部分需要重新跑一遍兼容性测试。

## 7. VS Code 推出"Agent window"，多 AI 协作有原生 UI 了

[Visual Studio Code 「Agent window」 のプレビュー版を公開](https://www.publickey1.jp/) · `Publickey · JA`

VS Code 的 May 2026 release 里悄悄上了一个叫 Agent window 的新窗口类型：可以同时挂多个 AI agent 在不同任务上跑（比如一个 Claude Code 写 backend、一个 Copilot 在跑测试），主编辑器不被打断。这是把 IDE 从「编辑器」推到「agent 协作面板」的一大步——以前要装一堆插件凑出来，现在原生支持。国内团队如果用 VS Code Server 远程开发的，可以测试一下 Agent window 在 SSH session 下的行为。

## 8. Anthropic 公布 Project Glasswing 联盟首批成果

[Project Glasswing: An initial update](https://www.anthropic.com/research/glasswing-initial-update) · `Anthropic`

4月组建的「Project Glasswing」联盟（AWS、Anthropic、Apple、Cisco、CrowdStrike、Google、JPMorgan、Linux Foundation、Microsoft、NVIDIA、Palo Alto Networks）公布了首批成果——主要是几份关于 critical software 攻击面建模的白皮书，以及一个针对 AI 训练流水线供应链的公共漏洞数据库。这个联盟值得长期关注：它是 2026 年第一个跨大厂的"AI + 供应链安全"实质性合作组织，国内做 SBOM 工具的团队应该把对接清单列进来。

## 9. Google Gemini 3.5 Flash 跳过 preview 直接 GA

[Gemini 3.5 Flash, now generally available](https://simonwillison.net/) · `Simon Willison`

Google I/O 上 Gemini 3.5 Flash 没有 preview 阶段，直接 GA。Simon Willison 实测下来的几个观察：context window 在工具调用场景下比 2.5 系列稳定很多；首 token 延迟降到 200ms 以下，对实时 voice agent 是质变；定价上 Flash 比同档 Sonnet 还低一档，所以 mid-tier 调用成本应该会被压下来。国内开发者通过 Vertex AI 中转的话，注意一下 region 选择。

## 10. xAI 推出 Grok Build，能并行起 sub-agent

[xAI のコーディング AI 「Grok Build」 のベータ版を公開](https://www.publickey1.jp/) · `Publickey / xAI`

xAI 的 coding agent「Grok Build」进入 beta，最大卖点是**并行 sub-agent**：主 agent 可以同时 fork 多个子 agent 跑独立任务，主 agent 负责协调和合并。这跟 Claude Code 的 subagent 模式思路类似，但 Grok Build 强调"无锁并行"——子 agent 之间用 git worktree 隔离。短期内不一定会撼动 Claude / Cursor 的份额，但「sub-agent 是标配」这个观念基本算坐实了。

## 编者按

今天的元主题是 **agent 终于走出聊天框**——VS Code Agent window、Grok Build sub-agent、V2EX 上吵的国产 code agent 不约而同指向同一个事实：2026 下半年，IDE 和终端的核心交互对象正在从"编辑器 + 一个 AI 副驾"变成"编辑器 + 一群 AI 工作单元"。今日必读是 **2 号 next-token prediction 的局限性** 和 **3 号 ZIRP 工程师人设**——前者帮你理解技术为什么必须走 agent 路线，后者帮你理解组织为什么必须接受 agent。
