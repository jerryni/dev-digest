---
title: "5月22日 · 今日技术精选"
date: 2026-05-22T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "隐私", "供应链", "ai-agents", "浏览器", "开发工具"]
categories: ["daily"]
summary: >-
  Rivian 给整车塞了个真正能关掉所有联网的开关；PyTorch Lightning 中招 Shai-Hulud 供应链攻击；Mozilla 公开反对 Chrome 的 Prompt API；Simon Willison 用 5 分钟回顾过去半年的 LLM 走势；Anthropic 把 Stainless 买下来；400 行 Shell 就想做你的编码 Agent。今天的主线是"基座在收紧"。
---

## 今日速览

不算大新闻日，但密度不低。Hacker News 顶端被隐私和供应链故事占据，AI 基础设施层在悄悄整合。Rivian 给出了什么叫"真正的退出选项"的范本；PyTorch Lightning 生态被实战教育了一遍什么叫"真正的供应链攻击"；Anthropic 收购 Stainless 也告诉你：下一层"无聊但赚钱"的 AI 基础设施（SDK 生成、客户端工具链）归属正在确定。如果你在做联网设备或者跑 LLM，建议从头读到尾。

## 1. Rivian 让你彻底关掉车机联网

[Rivian 支持文档：如何禁用所有数据收集](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) · `Hacker News`

Rivian 发了一篇支持文档，把一个完整的"全部断网"开关明明白白写出来了——关掉 OTA、关掉遥测、关掉远程服务，并且不会进入降级模式，不会跳弹窗骚扰。特斯拉、福特、通用都还把数据通道当成必需品；Rivian 是第一家把"真正的退出开关"做出来还公开记录用法的主流车厂。两年内这大概率会变成监管基线。

## 2. Shai-Hulud 蠕虫摸进了 PyTorch Lightning

[Shai-Hulud 主题恶意包出现在 PyTorch Lightning 训练库中](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · `Hacker News`

Semgrep 团队发现一个伪装成 pytorch-lightning 锁定依赖的恶意包，专门偷云凭证和 HuggingFace token。和去年 npm 那波是同一家族，现在迁移到了 ML 工具链——而 ML 工具链恰好是凭证最值钱的地方。如果你的 CI 会缓存模型权重或者拉 artifact，这周就去 audit 一遍 lockfile，别拖到下季度。

## 3. Mozilla 公开反对 Chrome 的 Prompt API

[Mozilla standards-position：反对 Prompt API](https://github.com/mozilla/standards-positions/issues/1213) · `Hacker News`

Mozilla 在 standards-positions 上正式登记了对 Prompt API（浏览器内 LLM 接口）的反对立场。反对点不是"反 AI"，而是把模型行为硬编码进浏览器平台会冻结一个还在快速演化的质量基线，同时新增一块没人要的指纹采集面。Chrome 大概率照发不误，但这条 issue 是目前对"浏览器塞 AI 到底难在哪"最清晰的论述。

## 4. Simon Willison：过去半年的 LLM 浓缩成 5 分钟

[The last six months in LLMs in five minutes](https://simonwillison.net/2026/may/19/six-months-llms/) · `Simon Willison`

Simon 把 11 月到 5 月的事件浓缩成一篇短文：小 context window 的终结、tool-use 协议的收敛、"agent"一词从行话变成承重词，以及价格最终落在了哪。如果你这半年埋头做单一产品需要一次性把视野重新校准，这篇就够了。

## 5. V2EX：vibe code 留下的技术债怎么还

[如何消除 vibe code 产生的技术债？](https://www.v2ex.com/t/1214452) · `V2EX`

一线工程师在 V2EX 上抛了今年迟早每个团队都要面对的问题：实习生或 PM 用 Agent 一把梭出来的功能，重写起来什么样、谁来负责。回复区从"当外包代码处理"到"两天再用同一个 Agent 重写一遍"都有。中文开发者社区聊这个话题比英文圈早、也更直接，建议关注一下。

## 6. V2EX：Antigravity 把 Gemini 额度永久提到 3 倍

[Antigravity： Gemini 模型额度永久提高为原来的三倍](https://www.v2ex.com/t/1214387) · `V2EX`

V2EX 几条独立反馈拼出 Google 没有公告的事实：Antigravity 免费和 Pro 套餐的 Gemini 额度都被悄悄拉到 3 倍。中文圈把它读成 Anthropic + AWS 全量铺开前的一次定价战。这种解读站不站得住先放一边，实际效果就是"业余项目默认走 Antigravity"已经是显而易见的选择了。

## 7. DuckDB 长出了自己的协议层：Quack

[DuckDB 客户端／服务器化的 Quack 协议登场](https://www.publickey1.jp/blog/26/duckdbquackduckdb.html) · `Publickey`

DuckDB 一直是嵌入式分析引擎。Quack 给它加了一层协议，让多个 DuckDB 实例可以互相连——嵌入式仓库现在能被一群机器同时访问。还远没到 ClickHouse 的成熟度，但分析负载场景下，它的形态突然不像"Jupyter 加速器"，而像一个真正的数据库了。

## 8. Bun 用 Claude 把自己从 Zig 迁到 Rust

[Bun 用 Claude 把开发语言从 Zig 迁移到 Rust](https://www.publickey1.jp/blog/26/javascriptbunclaudezigrust.html) · `Publickey`

Bun 作者 Jarred Sumner 发了一份迁移指南，说明他们怎么用 Claude 做 Zig→Rust 的机械翻译、人类只 review diff。重点不是语言选型，而是一支 runtime 团队公开演示如何用 AI 协作迁移一个百万行代码库——以及他们愿意把 playbook 公开。

## 9. Anthropic 收购 Stainless

[Anthropic 收购 Stainless](https://www.anthropic.com/news/anthropic-acquires-stainless) · `Anthropic`

Stainless 是几家头部 AI 厂商客户端背后的 OpenAPI → 强类型 SDK 生成器，Anthropic 自家 SDK 也用它。这笔收购把 SDK 生成搬到了自家屋檐下，信号很明确：Anthropic 想把客户端这一层端到端拿在手里——和十年前 Stripe 在支付 API 上做的剧本一样。预计 Claude SDK 发版节奏会更快，未来大概率会有面向所有人的 Stainless 后继产品。

## 10. Pu.sh：400 行 Shell 的编码 Agent

[Show HN: Pu.sh - 400 行 Shell 写的完整编码 Agent harness](https://pu.dev/) · `Hacker News`

对当前 Agent 框架军备竞赛的一记反驳。Pu.sh 用 400 行 POSIX shell 拼出工具调用、文件编辑、plan/execute 循环，没有 Python，没有 Node。它不是 Claude Code 或 Aider 的生产替代品，但它是"理解 Agent 底层到底在干什么"的强制阅读材料。哪怕你永远不会跑它，也建议读一遍源码。

## 编者按

今天的元主题是"基座在变硬"。Postgres 形态的工作流引擎、DuckDB 加了协议层、Anthropic 把 SDK 这一层收进来、Rust 在一个快速发展的 runtime 内部吃掉 Zig。连 Rivian 的"退出开关"和 PyTorch Lightning 的供应链事件，本质都是关于"数据通路控制权"的整合。如果只读两篇，建议是 Simon Willison 的半年回顾（用来校准方向感）和 Shai-Hulud / PyTorch Lightning 那篇（任何 CI 流程涉及模型 artifact 的团队都该读）。Zenn 今日的 trending 还是返回了空壳 SPA，所以日本视角的两条都来自 Publickey。
