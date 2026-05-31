---
title: "5月31日 · 今日技术精选"
date: 2026-05-31T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "anthropic", "sqlite", "zig", "ai-agent", "mcp"]
categories: ["daily"]
summary: "Anthropic 估值冲到 9650 亿美元、Opus 4.8 上线；社区开始辩论 MCP 是不是已经过气；SQLite 被吹成做持久化工作流的全部所需。今天的关键词是：估值、协议、与开发者的工作流。"
---

## 今日速览

周末归周末，AI 行业的资本动作和工程争论没停。Anthropic 一夜之间冲到 9650 亿美元估值并发了 Opus 4.8，社区随即在 V2EX 上吐槽"它说它是 qwen"。另一边，工程师们围绕"MCP 是不是已经死了"和"SQLite 能不能撑起持久化工作流"两个话题各执一词——都是直接关系到下一代 agent 系统怎么搭的硬问题。Zig 也借机发了一次 build system 大改。

## 今日 10 条

### 1. Anthropic 完成 650 亿美元 H 轮融资，投后估值 9650 亿美元

来源：Anthropic Newsroom · [链接](https://www.anthropic.com/news/series-h)

数字本身已经离谱——9650 亿美元是 OpenAI 之外任何 AI 公司从未达到过的量级。这轮过后，国内同行最该关心的不是估值本身，而是它意味着 Anthropic 接下来一两年在算力采购、人才争夺、企业销售上会更激进。对在国内做大模型应用的团队，意味着海外侧的"价格战可能性"被进一步推迟。

### 2. Claude Opus 4.8 发布

来源：Anthropic Newsroom · [链接](https://www.anthropic.com/news/claude-opus-4-8)

官方主打"编码、agent 任务、长链路工作的稳定性"。V2EX 上已经有人[实测吐槽](https://www.v2ex.com/t/1216494)"它说它是 qwen"——这种自我认知错位多半是训练数据里混了别家模型输出导致的，不是什么大事，但作为一种行业的"数据相互污染"信号还挺有意思。值得跑一遍自己的真实代码任务再下结论。

### 3. SQLite is all you need for durable workflows

来源：obeli.sk via Hacker News · [链接](https://obeli.sk/blog/sqlite-is-all-you-need-for-durable-workflows/)

HN 今日 630 分。作者主张：与其上 Temporal、Cadence 这套重型 durable workflow 框架，不如老老实实用 SQLite 做事件日志。论点核心是单机吞吐对绝大多数业务足够、运维心智极低。评论区里反方意见集中在"多机协调"和"failover"——但凡你的工作流上量没到这个程度，这篇值得看一遍。

### 4. Zig：Build System 重做

来源：ziglang.org via Hacker News · [链接](https://ziglang.org/devlog/2026/#2026-05-26)

Zig 的 build system 一直是它最具争议也最有想法的部分。这一轮 rework 把"buildable graph"作为一等公民，依赖描述、缓存模型都重写了。如果你在国内做嵌入式或者 C/C++ 替换路线评估，Zig 的工程化能力（不只是语言本身）正变得越来越关键。

### 5. The Last Technical Interview（Steve Yegge）

来源：Steve Yegge on Medium via Hacker News · [链接](https://steve-yegge.medium.com/the-last-technical-interview-bc13ddcf4564)

Yegge 又开始放大招。他的观点：传统白板算法面试在 AI 时代基本失效，公司应当转向"AI-assisted pair coding"式的评估。这事在北美华人圈讨论度很高，国内大厂还在抱着八股算法面，落差感会越来越强。无论你站哪边，这篇都该读完再发言。

### 6. MCP is dead?

来源：quandri.io via Hacker News · [链接](https://www.quandri.io/engineering-blog/mcp-is-dead)

这篇的标题党成分有点重，但点出了一个真实的问题：MCP（Model Context Protocol）的发展速度、生态成熟度、和"调用工具"这件事的其他实现方式（agent skills、function calling 原生扩展）相比，是不是已经在被绕开？HN 上 340 分 327 评论，正反方都有论据，对在做 agent 平台决策的团队是必读。

### 7. AWS 发布 Kiro Web：浏览器里直接用的 coding AI agent

来源：Publickey · [链接](https://www.publickey1.jp/blog/26/awswebaikiro_web.html)

不用装客户端，浏览器打开就能用。AWS 想抢 Claude Code / Cursor 那批用户。对国内/日本两边的开发者来说，最大的意义是"零安装门槛"——尤其在公司电脑权限严的场景下，这种 web-first 的形态有市场。

### 8. .NET MAUI 终于脱离 Mono，迁到 CoreCLR

来源：Publickey · [链接](https://www.publickey1.jp/blog/26/mononet_mauixamarinmonocoreclr.html)

从 Xamarin 时代继承下来的 Mono 运行时终于退场，统一到 CoreCLR。对在用 .NET MAUI 做跨平台移动应用的团队，意味着冷启动、GC 行为、AOT 体验会有可见的提升。坑也会有新坑，但这是必要的现代化。

### 9. 浏览器里跑安卓系统（V2EX 开源自荐）

来源：V2EX · [链接](https://www.v2ex.com/t/1216344)

作者称"烧了几百亿 token"做出了一套能在浏览器里运行的安卓系统。技术细节看完帖子再判断，但 vibe coding + 大量 token 投入做"以前需要几个工程师季度才能做出来"的项目，这个模式本身就是 2026 年中国开发者圈最值得观察的工作方式变化。

### 10. AI 把我调教了：从 0 消费到月消费 1200 元

来源：V2EX · [链接](https://www.v2ex.com/t/1216578)

一个非常具体的"个人 AI 开销曲线"分享。1200 元/月是中位 Claude / ChatGPT Plus + 第三方 API 的常规组合。值得看的不是数字本身，而是评论区里大家在算"这笔钱替代了什么"——这是国内技术从业者把 AI 工具内化进生产力栈的真实进度。

## 编者按

今天的暗线是"基础设施和工作流再洗一遍"：SQLite 想吃掉 durable workflow，MCP 被质疑、Zig 重写 build system、.NET MAUI 抛弃 Mono——全是底座层的位移。资本侧 Anthropic 拿到 650 亿美元只是把这种位移的速度推得更快。今天必读一篇的话：**SQLite is all you need for durable workflows**——不是因为它一定对，而是因为它逼你重新审视自己当下的工作流栈到底有没有过度工程。备选：**MCP is dead?**。
