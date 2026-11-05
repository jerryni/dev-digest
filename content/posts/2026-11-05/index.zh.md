---
title: "11月5日 · 今日技术精选10本"
date: 2026-11-05T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "ai", "opensource", "developer-tools"]
categories: ["daily"]
summary: "从 Go 的 JSON API、智能体可视化到 AI 辅助代码审查，今天关注可验证的工程边界。"
---

# 11月5日 · 今日技术精选10本

## 今日速览

今天的线索很一致：AI 已经不只是写几行代码，而是开始进入数据应用、代码审查和模型权重等更深的工程层。另一面，NAS 勒索恢复和 SSH 客户端的讨论提醒我们，基础设施的老问题并没有因为智能体热潮而消失。

## 精选条目

### 1. [Go 的新 JSON API](https://go.dev/blog/jsonv2)
`HN · Go`

Go 团队介绍了新的 JSON API，目标是把常见编码需求做得更可控，同时修正旧接口长期积累的边角行为。对维护大型 Go 服务的人来说，迁移成本和兼容策略比新功能本身更值得先看清；这是一次很典型的“标准库也需要现代化”的更新。

### 2. [NVIDIA auto-ontology 登上 GitHub Trending](https://github.com/NVIDIA/auto-ontology)
`GitHub Trending · 开源`

NVIDIA 的 auto-ontology 把自动生成和维护领域本体这件事推到开源视野里。RAG 或企业知识图谱项目往往卡在数据模型而非向量检索，这类工具的价值取决于它能否把生成结果接入人工校验、版本控制与变更追踪。

### 3. [Datasette Agent 0.5a0 的侧栏工作区](https://simonwillison.net/2026/Nov/3/datasette-agent/)
`Simon Willison · AI工具`

Datasette Agent 新增 panel，让聊天与数据表或查询页面并排存在，并可通过对话生成、修改基于数据的应用。真正有意思的不是“从提示词造页面”，而是把结果留在可浏览、可检查的数据上下文旁边；这比把答案塞回一段聊天记录更像可工作的软件。

### 4. [三端原生 SSH、SFTP 与 AI 客户端](https://www.v2ex.com/t/1254583)
`V2EX · 开发工具`

一位开发者发布了覆盖三端的原生 SSH 客户端，把 SFTP 和 AI 功能放进同一应用。远程运维工具是否值得替换，关键不在功能表有多长，而在密钥管理、断线恢复和跨设备会话能否稳定；社区讨论正好是观察这些真实摩擦的入口。

### 5. [群晖 NAS 遭勒索后的 SSD 缓存恢复](https://www.v2ex.com/t/1254586)
`V2EX · 存储安全`

这条实战帖讨论 NAS 被勒索后，能否从 SSD 缓存找回文件。它不构成通用恢复方案，却再次说明备份不是一个设备或一个盘位，而是可离线验证的恢复流程；对个人开发者和小团队，定期演练恢复比购买更大容量更优先。

### 6. [EasyEEG：把代理式 AI 放入脑波研究流程](https://zenn.dev/hackathons/google-cloud-japan-ai-hackathon-vol5/projects/bf62c6a94633a5)
`Zenn · Agentic AI`

EasyEEG 尝试用代理协助实验目标制定、电极准备、波形观察与记录分析，同时强调伦理护栏和最小化数据保留。医疗与研究场景不适合把“能跑”当成“可用”；它把权限、审批和留痕放进展示中，这一点比模型名更值得借鉴。

### 7. [Hachi Atelier：从植物照片到可打印 STL](https://zenn.dev/katsunori04/articles/a3fb70431bbb1c)
`Zenn · 生成式制造`

这个项目将图像识别、生成式设计和隔离执行串成 3D 打印花盆的工作流，并把生成代码限定在沙箱中运行。AI 生成物是否真正可交付，往往取决于后面的几何检查和反馈循环；“先生成、再验证、再修复”是比一次性出图更可靠的工程路线。

### 8. [GitHub Octoverse：TypeScript 连续两年居首](https://www.publickey1.jp/blog/26/github2typescriptrustosscc_switchomarchygithub_octoverse_2026.html)
`Publickey · 开源生态`

Publickey 汇总 GitHub Octoverse 2026：TypeScript 连续两年成为使用最多的语言，Rust 的拉取请求增速突出。排行榜不能替代技术选型，但它会影响人才、工具链和库维护的重心；对跨端与平台团队，TypeScript 的网络效应仍在扩大。

### 9. [Copilot Dreaming：把开发活动整理为个人记忆](https://www.publickey1.jp/blog/26/github_copilot_dreaminggithub_universe_2026.html)
`Publickey · GitHub Universe`

GitHub 发布 Copilot Dreaming，主张在后台回顾工作并整理个人记忆与指导信息。开发者应当把它当作数据治理问题来审视：哪些上下文会被持久化、如何更正过时结论、团队知识与个人偏好如何隔离，决定了这类功能能否进入日常流程。

### 10. [Kimi K3.1 Pro 开放模型权重](https://huggingface.co/moonshotai/Kimi-K3.1-Pro)
`HN · 开放模型`

Kimi K3.1 Pro 的权重发布，让本地部署和二次研究多了一个可评估对象。选开放权重时别只看基准：许可、推理栈、显存占用、工具调用稳定性和是否能做内部微调，才是团队能否把模型真正用起来的分水岭。

## 编者按

今天的主题是“把能力放进边界里”：数据应用需要可见的上下文，生成制造需要验证回路，开发者记忆则需要治理边界。首推 Go 的 JSON API 与 Datasette Agent，它们分别代表了基础能力与交互工作流的务实演进。Anthropic 新闻页未见可确认的近 24 小时技术发布，因此没有为凑数纳入旧闻。
