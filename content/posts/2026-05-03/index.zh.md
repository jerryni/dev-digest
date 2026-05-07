---
title: "5月3日 · 今日技术精选"
date: 2026-05-03T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Kimi", "DeepSeek", "Mercedes", "Haskell"]
categories: ["daily"]
summary: "Kimi K2.6 在编码挑战里击败 Claude/GPT-5.5/Gemini，DeepClaude 把 Claude Code 和 DeepSeek V4 Pro 串起来，OpenAI o1 在急诊分诊准确率超越医生，Agentic Coding 是个陷阱，奔驰承诺把物理按钮装回来，TUIs 复兴。"
---

## 今日速览

今天的主线是"开源中国模型 vs 闭源大厂"。月之暗面 Kimi K2.6 在一个公开编码挑战里击败 Claude、GPT-5.5、Gemini——配合上 HN 上爆火的 DeepClaude（用 DeepSeek V4 Pro 跑 Claude Code agent loop），中国模型在 dev tooling 领域的存在感这周明显抬升。另一边，HN 上《Agentic Coding Is a Trap》和《Why TUIs are back》两篇都和昨天的"bottleneck was never the code"形成连续讨论。OpenAI 的 o1 模型在哈佛急诊分诊试验里准确率明显超越医生，这条对国内做医疗 AI 的团队是重要参考。

---

## 1. Kimi K2.6 在公开编码挑战里击败 Claude/GPT-5.5/Gemini

来源标签：[EN · HN Top]
链接：<https://thinkpol.ca/2026/04/30/an-open-weights-chinese-model-just-beat-claude-gpt-5-5-and-gemini-in-a-programming-challenge/>

月之暗面的开源权重模型在一个公开编码挑战里跑赢三家闭源大厂。HN 评论 200+，多数承认"这是开源中国模型第一次在 dev 任务上明确领先"。值得注意的是参数量级和训练数据来源——这是国内做基座模型的团队最近半年集体进步的代表样本。

## 2. DeepClaude — 用 DeepSeek V4 Pro 跑 Claude Code agent loop

来源标签：[EN · HN Top]
链接：<https://github.com/aattaran/deepclaude>

GitHub 项目，把 Claude Code 的 agent loop 用 DeepSeek V4 Pro 跑——成本骤降，效果"够用"。HN 280 评论里很多人在分享自己的实测数据。这是国内"低成本平替"路线的工程化样本，能直接挪去内部跑。

## 3. OpenAI o1 在急诊分诊里准确率 67%，医生 50-55%

来源标签：[EN · HN Top]
链接：<https://www.theguardian.com/technology/2026/apr/30/ai-outperforms-doctors-in-harvard-trial-of-emergency-triage-diagnoses>

哈佛医学院发表的临床试验——o1 在 ER 分诊的诊断准确率达到 67%，对照组的分诊医生 50-55%。这条对国内做医疗 AI 产品的团队是关键参考：监管路径、责任划分、临床整合方式都是接下来一年的核心议题。

## 4. Agentic Coding Is a Trap

来源标签：[EN · HN Top]
链接：<https://larsfaye.com/articles/agentic-coding-is-a-trap>

一篇克制的反驳。作者认为目前的 agentic coding 工具最大的问题不是质量，是它制造的"我在工程"幻觉——而 review 频率持续下降。和后来 Simon Willison 5/06 的反思形成连续讨论，可以做"5 月初 agent 怀疑周"系列阅读。

## 5. Mercedes-Benz 承诺把物理按钮装回来

来源标签：[EN · HN Top]
链接：<https://www.drive.com.au/news/mercedes-benz-commits-to-bringing-back-phycial-buttons/>

奔驰公开承认全触摸屏方向的产品决策是错的，下代车型恢复物理按钮。HN 500+ 评论一片"早该这样了"。这条对国内造车新势力的产品 / HMI 团队是直接信号——理想/小米/蔚来这两年都在大屏上走得太远，回调窗口正在打开。

## 6. Why TUIs are back

来源标签：[EN · HN Top]
链接：<https://wiki.alcidesfonseca.com/blog/why-tuis-are-back/>

终端 UI 的复兴。作者把 lazygit、k9s、helix、Claude Code 这一系列工具串起来，论点是"开发者厌倦了浏览器作为应用容器"。文章很长但易读，对做开发工具的团队是设计语言层面的参考。

## 7. A couple million lines of Haskell — Mercury 的生产工程

来源标签：[EN · HN Top]
链接：<https://blog.haskell.org/a-couple-million-lines-of-haskell/>

Mercury 公开自己用 Haskell 写了 200 万行生产代码的工程实践。Haskell 在 fintech 仍然是少见但稳的选择。文章讲了人才、CI、debugging 等运营层面的实操经验。

## 8. V2EX：2026 年了，Notepad++ 对比 VSCode 优势在哪

来源标签：[ZH · V2EX]
链接：<https://www.v2ex.com/t/1210012>

国内开发者的常态吐槽。Notepad++ 在内网/无 AI 环境仍是默认。和今天的 #6（TUIs 复兴）放一起看，本质都是"web 时代之外，工具的另一条路径"。

## 9. Specsmaxxing — 用 YAML 写规格来对抗 AI 精神错乱

来源标签：[EN · HN]
链接：<https://acai.sh/blog/specsmaxxing>

作者主张：在 AI 时代，靠"和 AI 聊清楚需求"是失败的，必须把规格写成 YAML 这种结构化形式。HN 295 评论里大量工程师在讨论这个趋势——文档写法可能要从 markdown 重新回到 schema。

## 10. Show HN: WhatCable — Mac 菜单栏识别 USB-C 数据线

来源标签：[EN · Show HN]
链接：<https://github.com/darrylmorley/whatcable>

Swift/SwiftUI 写的小工具，用 Mac 已有的能力读出 USB-C 数据线的真实规格（功率、数据速度、Thunderbolt 支持等）。开源免费，无追踪。USB-C 那堆"看着一样实际差很多"的线，每个开发者都被坑过。

---

## 编者按

今天值得优先读的两条：#1（Kimi K2.6 编码挑战）+ #2（DeepClaude）一起看，是国内开源模型在 dev 工具领域真正抬头的信号。#3（OpenAI o1 在急诊）则是 AI 进入高风险垂直领域的标志性数据点。Agentic Coding (#4) 和 TUIs (#6) 适合做思考工具产品的人慢读。
