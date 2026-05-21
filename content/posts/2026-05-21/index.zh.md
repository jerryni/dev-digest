---
title: "5月21日 · 今日技术精选"
date: 2026-05-21T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "ai-agents", "antigravity", "compute-grid", "v2ex"]
categories: ["daily"]
summary: >-
  LinkedIn 被发现把 6000+ 浏览器扩展指纹塞进每条请求；比利时直接掉头、停止核电站退役；honker.dev 把 durable 队列塞进 SQLite。国内端 V2EX 两条热帖：TRAE 是不是国产 AI IDE 里"最不差"的、以及"算力网"国家级基建终于要落地。日本端 Publickey 同一天连发 Antigravity 2.0、Dell 桌面 Agent PC、Google Managed Agent API。今天的主线：AI Agent 把基础设施层（编辑器、数据中心、桌面、网络）整体往前推了一格。
---

## 今日速览

今天的关键词是 "Agent 把基建吃进来"——Google 用 Managed Agent API 把"AI Agent + 一台 Linux 沙箱"做成了一次 API 调用；Dell 把 NVIDIA GB10/GB300 塞进桌面机当作"本地 Agent 工作站"卖；Antigravity 2.0 现场演示让 Agent 从零写一个 OS 还能跑 Doom。国内端的对照是 V2EX 上吵了一晚的"算力网"——同一件事，国家级基建版本的开局。安全侧 LinkedIn 偷扫扩展指纹的事件给所有用浏览器登业务后台的人提了个醒。比利时掉头继续运营核电站这条放在 AI 训练耗电飙升的语境下读，比看上去更耐人寻味。

## 1. LinkedIn 把 6,278 个浏览器扩展指纹塞进每条请求

[LinkedIn scans for 6,278 extensions and encrypts the results into every request](https://404privacy.com/blog/linkedin-is-scanning-your-browser-extensions-this-is-how-they-use-the-data/) · `Hacker News`

404privacy 的研究员逆向了 LinkedIn 主站的 JS，发现页面会主动探测 6,278 个已知 Chrome 扩展，把命中结果加密后塞到每一次 API 请求里。换句话说，你装了哪些自动化、抓取、薪资比对、招聘外挂，LinkedIn 现在每次请求都知道。在日华人工程师如果同时挂多个翻译/词典/价格比对扩展，建议至少把跟 LinkedIn 业务直接相关的（自动 connect、Sales Navigator 外挂、爬虫类）放到独立 profile 隔离开。

## 2. 比利时停止核电站退役

[Belgium stops decommissioning nuclear power plants](https://dpa-international.com/general-news/urn:newsml:dpa.com:20090101:260430-930-14717/) · `Hacker News`

比利时政府宣布两座原定退役的反应堆继续运营，明确写明是为了"应对 AI 数据中心和工业用电增长"。继英国、瑞典之后又一个反核国家掉头。把这条和今天 Publickey 的 Dell Deskside Agentic AI、Managed Agent API 放一起看，能更清楚地感觉到——AI 这一波拉的不是 GPU，而是电网。

## 3. honker.dev · 把 durable 队列 / 流 / pub-sub / cron 全塞进 SQLite

[Durable queues, streams, pub/sub, and a cron scheduler – inside your SQLite file](https://honker.dev/) · `Hacker News`

新出的开源库 honker.dev 把 Sidekiq / Faktory / NATS / Cron 这一整套"消息系统 + 调度器"用单文件 SQLite 实现，单进程嵌入即可用，崩了恢复也只需要拷文件。日常做内部 dev tool、自动化机器人、小规模 SaaS 后端的同学可以直接把 Redis + 队列服务的依赖砍掉一层。配合 SQLite WAL 模式，单机几千 TPS 是稳稳跑得动的。

## 4. V2EX · 国产 AI IDE 矮子里挑将军，TRAE 算是最不差的？

[国产的 AI IDE 矮子头上选将军好像也就 TRAE 好用点](https://www.v2ex.com/t/1213384) · `V2EX`

90 楼的讨论。楼主测了一圈通义灵码、CodeGeeX、文心快码、TRAE，结论是 TRAE 在 Agent 模式下完成度最高，但跟 Claude Code / Cursor 比还差至少一个版本。有意思的是评论里出现的真问题："国内能不能本地化部署 Claude Code 的成本是多少"、"用海外 IDE 拉国内代码合规怎么走"，这些是国内一线工程师明面上不能问、私下一直在想的事。

## 5. V2EX · "算力网"要来了

["算力网"要来了](https://www.v2ex.com/t/1213402) · `V2EX`

讨论的是国家层面"东数西算 2.0"路线下的全国统一算力调度。技术细节不多，但底下的争论是真的有信号量：跨省 GPU 调度、训练任务托管、价格统一、谁来当结算层。海外华人工程师可以当成"中国版 EU 算力主权"框架的预演来读。短期看不到对外开放，但国内大模型公司未来两年的训练成本结构肯定会被它改写。

## 6. Publickey · Google Antigravity 2.0，现场演示让 Agent 写出 OS 并跑 Doom

[Google、Antigravity 2.0発表。デモとしてゼロからOSを開発、Doomも実行可能に](https://www.publickey1.jp/blog/26/googleantigravity_20osdoom.html) · `Publickey`

Google 的 Antigravity Agent 平台升到 2.0，主打"长任务规划 + 自主子任务编排"。最炸的演示是给一个空仓库，Agent 自己写了一个 minimal OS、能 boot、能在上面跑 Doom。技术细节之外，对国内开发者更现实的影响是：Google 这条线在和 Anthropic 的 Claude Code、OpenAI 的 Codex 直接抢"端到端工程"市场，三家都开始拼真实可交付项目而不是 benchmark。

## 7. Publickey · Dell Deskside Agentic AI，把 NVIDIA GB10/GB300 塞进桌面

[デル、ローカルでAIエージェントを動かすためのデスクトップPCなど Dell Deskside Agentic AI 発表](https://www.publickey1.jp/blog/26/aipcdell_deskside_agentic_ainvidia_gb10gb300.html) · `Publickey`

Dell 把 GB10/GB300 做进桌面工作站，定位是"开发者本地跑 Agent"。重点不是性能数字，而是定价和使用模式——日本企业明显是目标客户：合规要求高、不愿把代码送上云、又想用 Agent，本地工作站正好踩中。北美华人开发者可以观察这条产品线明年是否会拉低本地推理的入门价格。

## 8. Anthropic · 把前沿 AI 的讨论拉到更广

[Widening the conversation on frontier AI](https://www.anthropic.com/news/widening-conversation-ai) · `Anthropic News`

Anthropic 发了一篇相对偏 Policy 的文章，主旨是"模型能力评估不能只在 AI 实验室内部跑，要拉政府、学界、第三方机构一起做"。对开发者层面的直接影响：Responsible Scaling Policy 之类的合规模型可能开始变成行业内的事实标准，企业接 Claude / 其他前沿模型时合规走查文档会变厚。

## 9. Publickey · Google "Managed Agent API"，一次调用给你一个 Agent + Linux 沙箱

[APIコール一発でGoogleがホストするLinux環境付きのAIエージェントを起動](https://www.publickey1.jp/blog/26/apigooglelinuxaimarkdownmanaged_agent_api.html) · `Publickey`

Google Cloud 上新接口 Managed Agent API：一次 POST 起一个 Agent，附带 Google 托管的 Linux 沙箱、可挂自定义 Markdown 指令、跟 Antigravity 共用 runtime。这条对应的就是 Anthropic Claude Agent SDK + Code Execution 那一套，但走的是"完全托管、按调用计费"路线。给做 SaaS 后端的人提供了一个新的"上云 Agent"选项，省下自己维 sandbox 的力气。

## 10. Linux Foundation · AGNTCon + MCPCon 9 月在东京举办

[Linux Foundation、AIエージェントをテーマにしたイベント AGNTCon + MCPCon を東京渋谷で開催](https://www.publickey1.jp/blog/26/linux_foundationaiagntcon_mcpcon910112.html) · `Publickey`

Linux Foundation 把今年的 AI Agent + MCP 主题大会放在东京涉谷，9 月 10-11 日两天。Agenda 还没出全，但从 LF 把场子放在东京这件事可以看出：日本企业对 Agent 的采购意愿被官方判定为足以撑起一次主场大会。在东京的工程师可以提前安排日程，也是难得的招聘窗口。

## 编者按

今天的 meta-theme 是"AI Agent 不再只是一个 SDK 调用，而是开始要电、要硬件、要标准、要会场"。从 Belgium 留下核电、Dell 卖桌面 Agent PC、Google 做托管 Agent API、LF 把会场搬到东京，能很清楚地读到：行业从"做 Demo"切到"做基础设施"的阶段。必读两条是 **LinkedIn 扫扩展**（如果你日常用 LinkedIn 谈合作或招聘，影响立刻可见）和 **Google Managed Agent API**（如果你在做 SaaS 后端，未来 12 个月会被它拉去重做架构）。
