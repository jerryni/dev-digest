---
title: "5月1日 · 今日技术精选"
date: 2026-05-01T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "DeepSeek", "Grok", "Uber", "Apple"]
categories: ["daily"]
summary: "DeepSeek V4 几乎追上 frontier 模型（Simon Willison 评测），Uber 4 个月烧掉全年 AI 预算（全砸 Claude Code），Grok 4.3 发布，Apple 不小心把 CLAUDE.md 文件带进 Apple Support app，TI-84 Evo 计算器，Spotify 给真人艺人加 Verified 徽章。"
---

## 今日速览

5 月开局火力全开。Simon Willison 的 DeepSeek V4 评测说"几乎追上 frontier"——HN 670 评论。最让国内同行心情复杂的可能是另一条："Uber 4 个月烧掉了全年 AI 预算，全砸在 Claude Code 上。"Apple 内部疏忽——Apple Support 应用里居然能找到内部使用的 CLAUDE.md 文件——证实 Anthropic 的工程化产品已经渗进 Apple 内部研发流程。Grok 4.3 同步发布。这一天对任何关注 AI tooling 商业化的人都值得读完。

---

## 1. DeepSeek V4 — 几乎追上 frontier（Simon Willison 评测）

来源标签：[EN · Simon Willison · HN Top]
链接：<https://simonwillison.net/2026/Apr/24/deepseek-v4/>

Simon 实测后给出"almost on the frontier"的评价——这是他对模型最高级别的判断之一。结合 5 月 6 日的 DeepSeek V4 Pro 75% 折扣（"5/07 的第 9 条"），可以看到 DeepSeek 的产品节奏——能力 + 价格双线推进。对国内做 AI 应用的团队，这条直接关系到模型选型决策。

## 2. Uber 4 个月烧掉全年 AI 预算，全砸 Claude Code

来源标签：[EN · HN Top]
链接：<https://www.briefs.co.uk/news/uber-torches-entire-2026-ai-budget-on-claude-code-in-four-months/>

Uber 工程团队 4 个月内消耗了为整个 2026 年准备的 AI 工具预算。HN 475+ 评论分两派：一派担忧"Claude Code 让工程师变成代码生成机的工头"，另一派认为"这就是真实的生产力增长"。对国内大厂的预算 / 工具选型负责人，这条是必读，因为它定义了"AI 工具采购到底是消费还是投资"。

## 3. Grok 4.3 发布

来源标签：[EN · HN Top]
链接：<https://docs.x.ai/developers/models/grok-4.3>

xAI 又一次发版，Grok 4.3 在文档里强调推理和工具使用。HN 530+ 评论里很多人在讨论"Grok 在编程任务上是否真正有竞争力"。对中国跨境业务团队，Grok 仍是个供应商风险高、地缘绑定强的选项——但能力上确实在追。

## 4. Apple 不小心把 CLAUDE.md 文件带进 Apple Support 应用

来源标签：[EN · HN Top]
链接：<https://x.com/aaronp613/status/2049986504617820551>

逆向工程发现 Apple Support 应用里有 Anthropic 的 CLAUDE.md 配置文件——证实 Apple 内部已经在用 Claude Code 做工程。Apple 一向对内部工具讳莫如深，这次"漏出"是个标志性时刻。对国内做 AI dev tools 的团队是商业化方向的有力指标。

## 5. Show HN: WhatCable — Mac USB-C 数据线信息工具

来源标签：[EN · Show HN]
链接：<https://github.com/darrylmorley/whatcable>

Mac 菜单栏小工具，识别 USB-C 数据线的真实规格（功率、数据速率、Thunderbolt 支持等）。Swift/SwiftUI，开源免费。简单但是每个开发者都需要的工具。

## 6. TI-84 Evo 计算器发布

来源标签：[EN · HN Top]
链接：<https://education.ti.com/en/products/calculators/graphing-calculators/ti-84-evo>

德州仪器更新 TI-84 系列。HN 480+ 评论分成"看到童年回忆"和"美国教育系统对计算器锁定的批判"两派。对国内做教育硬件的团队，TI 在美国 K-12 数学考试的强制采购地位是值得研究的"教科书级护城河"。

## 7. Spotify 给真人艺人加 Verified 徽章

来源标签：[EN · HN Top]
链接：<https://www.bbc.com/news/articles/c5yerr4m1yno>

Spotify 推出"已验证人类艺人"徽章——把真人音乐家和 AI 生成内容区分开。这一变化对国内做音乐 / 内容平台的团队是必修信号——AI 内容泛滥的反作用力，平台必须做"人类原创性"的标识。

## 8. Apple 不小心暴露 Claude.md 也带出另一个问题：依赖封闭工具的风险

来源标签：[EN · HN]
链接：<https://x.com/aaronp613/status/2049986504617820551>

和 #4 同源但角度不同：Apple 内部用 Anthropic 工具流程，但 Anthropic 任何政策变化都可能影响 Apple 的工程节奏。对于强调供应链 sovereignty 的国内大厂（华为、阿里），这是个反面参考——你建的 AI 工具栈对外部依赖到了什么程度？

## 9. AI 用水量没那么夸张

来源标签：[EN · HN]
链接：<https://californiawaterblog.com/2026/04/26/ai-water-use-distractions-and-lessons-for-california/>

加州水务专家的反驳。"AI 数据中心用水"被舆论严重夸大，比起农业、户外用水都是小巫见大巫。对国内做政策研究的人，这是客观数据来源——舆论 vs 真实数字常常差很远。

## 10. Police 用车牌识别系统跟踪暧昧对象 14 次以上

来源标签：[EN · HN]
链接：<https://ij.org/police-have-reportedly-used-license-plate-readers-to-stalk-romantic-interests-at-least-14-times-in-recent-years/>

调查报告。美国警察至少 14 次记录用车牌识别系统监控自己的恋爱对象。系统设计的失败案例——任何"中央化的监控能力"最终都会被滥用。对国内做城市大脑、智能交通的团队是必修案例。

---

## 编者按

今天的两条必读：#2（Uber 烧光预算）和 #4（Apple 暴露 CLAUDE.md）。一起读会得到完整图景——AI dev tools 从"试用阶段"快速过渡到"主流采购"。#1（DeepSeek V4）则是看待"中国开源模型何时真正成熟"的最直接观察点。
