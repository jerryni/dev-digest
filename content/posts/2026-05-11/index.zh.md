---
title: "5月11日 · 今日技术精选"
date: 2026-05-11T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Claude", "浏览器", "安全", "供应链", "Anthropic"]
categories: ["daily"]
summary: "Mozilla 在标准位置上正式反对 Chrome 的 Prompt API；与此同时 Mozilla 自己用 Claude Mythos 把 Firefox 单月安全修复数从 20 多条干到 423 条。LinkedIn 被抓包：每次请求都偷偷扫描 6,278 个浏览器扩展再加密上传。PyTorch Lightning 供应链中招 Shai-Hulud 主题恶意包。Anthropic 拉上 Blackstone、H&F、高盛搞了个企业 AI 服务公司。V2EX 集体进入 Claude Code 倦怠期。"
---

## 今日速览

今天这一天讲的是平台权力归谁定义。Mozilla 和 Google 在公开吵架，吵的是浏览器要不要内置 LLM Prompt API；同一周，Mozilla 工程团队却用 Anthropic 的 Mythos 预览版把 Firefox 安全漏洞修复速度从原来的 20-30/月直接干到 423/月。LinkedIn 被发现每次 API 请求都在加密上传"你装了哪些扩展"的指纹——堪称 2026 年最激进的浏览器指纹采集案之一。AI 厂商这边，Anthropic 联合三家私募/投行成立了一家面向企业的 AI 服务公司，明显在往价值链上游走。如果只看三条：1、2、8。

---

## 1. Mozilla 正式反对 Chrome 的 Prompt API

标签：[EN · HN 热门]
链接：<https://github.com/mozilla/standards-positions/issues/1213#issuecomment-4347988313>

HN 564 分。Mozilla 把对 Web Prompt API 的官方立场从 "neutral" 改成了 "negative"。要点不在于反对 AI 本身——而是把模型驱动的 prompt API 直接塞进 Web 平台，等于让浏览器厂商默认垄断了"你用哪个模型"，给平台方加了一个针对开放 Web 的内容审查杠杆，还顺带多了一个浏览器指纹采集面。如果你团队正在做依赖 Chrome 端侧 prompt 路径的产品，开周会前先看完这篇。国内开发者尤其要注意：Chrome 端侧 API 的政策走向会直接影响国内 Web 浏览器内核团队（Edge、各种 Chromium 套壳）下一步要不要跟进，以及怎么跟进。

## 2. Mozilla 用 Claude Mythos 一个月修了 423 个 Firefox 安全漏洞

标签：[EN · Simon Willison / Mozilla Hacks]
链接：<https://hacks.mozilla.org/2026/05/behind-the-scenes-hardening-firefox/>

Mozilla 写了一篇罕见诚恳的复盘，讲他们如何利用 Anthropic Mythos 预览版的"特权访问"把安全管线翻新了一遍。两件事变了：一是模型本身找真漏洞的能力上了台阶（其中有 20 年没人发现的 XSLT bug 和 15 年的 `<legend>` bug），二是 Mozilla 自己搭的"harness"——筛选、串联、降噪——成熟到了能压住误报洪水的程度。数据：Firefox 2025 全年每月 20-30 个安全修复，2026 年 4 月直接 423 个。和第 1 条一起看：同一家公司同一周公开抵制浏览器内置 AI，又公开宣传用 AI 当安全武器。两个立场其实都自洽，但同时摆出来才有意思。

## 3. LinkedIn 偷偷扫描你装了哪 6,278 个扩展，再加密上传到服务器

标签：[EN · HN 热门]
链接：<https://404privacy.com/blog/linkedin-is-scanning-your-browser-extensions-this-is-how-they-use-the-data/>

HN 299 分还在涨。404privacy 团队逆向了 LinkedIn 的 Web 客户端，发现每次页面加载它都会探测 6,278 个具名扩展是否存在，然后把指纹塞进每个 API 请求的加密 blob 里发回服务器。最可能的用途是反爬虫/反自动化，但副作用是当今生产环境里最激进的浏览器指纹采集面之一，而且"加密上传"这个动作显然是冲着躲避网络层抓包去的。做反爬的同学会觉得有意思，注重隐私的会觉得绝望。欧盟数据保护机构应该很快就会有动作。

## 4. V2EX：高强度使用 Claude Code 半年后，我终于无法忍受了

标签：[ZH · V2EX]
链接：<https://www.v2ex.com/t/1211200>

4 小时 102 楼。楼主把一个重度 Claude Code 用户的怨气一次性倒出来：每次更新后模型像变笨了；rate limit 撞墙；上周修过的 bug 这周又被它重新引入；那个不透明的"context compaction"经常把你最需要的部分悄悄丢掉。回复分成两派：一派表示已经迁到 Codex / Cursor / Aider；另一派说换了也一样，你只是过了蜜月期。这帖子是中文圈对 AI 编码工具情绪的一个温度计——agentic engineering 元年走完一半，"过曝"已经开始。北美/日本华人开发者圈子可以对照下自己的体感。

## 5. V2EX：AI 让事物贬值，各种层面上

标签：[ZH · V2EX]
链接：<https://www.v2ex.com/t/1211027>

短帖，但论点很硬：生成式 AI 正在贬值所有"过去用来证明你认真"的东西——一份精致 README、一篇结构清晰的博客、一段写得很到位的 PR 描述、一个有 100 个 commit 的 GitHub 仓库。这些过去都自带"作者上心了"的信号，现在都不再是。本周 Simon Willison 在他的 podcast 里讲过同样一件事（参见我们 5 月 8 日那期），但中文版这帖的笔触更冷一点，更像是劳动市场的悲观判断，而不是审美感叹。和上一条放一起看挺合适。

## 6. Zenn：AI Agent 时代的数据库设计，Turso 在重写规则

标签：[JA · Zenn]
链接：<https://zenn.dev/emuni/articles/6eef9f97f564b4>

エムニ（Emuni）一位工程师的好文。论点是：AI Agent 工作负载——大量短生命周期、每任务一个独立数据库——恰好是 Turso "数百万个便宜 SQLite 实例"模型的目标场景。文章把成本算给你看（Turso 上一个 agent 一个库每月几美分，对比 Postgres-per-tenant 每月几美元），讲了运维上的简化，以及"每个 agent 有自己的私有 store"这个前提下会自然冒出来的设计模式。在做多租户 agent 系统的同学值得评估一下。

## 7. Publickey：企业存储 CEO 公开喊话——芯片成本涨了 4-10 倍，产品涨价 70%

标签：[JA · Publickey]
链接：<https://www.publickey1.jp/blog/26/ceo41070.html>

Everpure（前身 Pure Storage）董事长兼 CEO Charles Giancarlo 在客户公告里写明：过去一年公司采购的关键半导体部件成本上涨了 4-10 倍，所以产品价格上调约 70%，且未来还可能继续涨。宏观背景就是大家熟悉的那个故事：AI 训练和推理把 HBM 和高密度闪存吃干净了，对企业存储这一层来说成本曲线根本不是按这种斜率设计的。给国内做基础设施采购的朋友一句话：你上季度做的 2026 年硬件预算已经过时了。

## 8. Anthropic + Blackstone + Hellman & Friedman + 高盛：新成立的企业 AI 服务公司

标签：[EN · Anthropic]
链接：<https://www.anthropic.com/news/enterprise-ai-services-company>

Anthropic 宣布与 Blackstone、Hellman & Friedman、Goldman Sachs 三家合资成立一家新的企业 AI 服务公司。结构：PE 资本撑腰的服务臂，专门帮大企业把 Claude 接进复杂的内部工作流——重在实施和集成，不是卖模型。战略上的解读是 Anthropic 不愿意把企业 AI 的服务利润全让给 Accenture、Deloitte 这条传统咨询链，所以要直接下场。和上周那条 SpaceX/xAI 算力交易（我们 5 月 8 日那期第 8 条）放一起看：Anthropic 在价值链的每一段都在买入选择权。

## 9. GitHub Trending：字节跳动 UI-TARS-desktop

标签：[EN · GitHub Trending]
链接：<https://github.com/bytedance/UI-TARS-desktop>

今日 Trending 第一：字节开源的桌面端 computer-use Agent。UI-TARS 用的是专门在 GUI 交互轨迹（点击坐标、键盘输入、屏幕状态）上微调的视觉-语言模型。Desktop 版打包成本地应用，可以真的操作你的电脑——这就直接进了 Claude for Chrome、OpenAI Operator 那个赛道，但走的是开源权重路线。一直想等一个开源版本再让 Agent 摸你电脑的同学，可以认真评测一下。国内做 RPA / 自动化的团队也值得跟踪，这种开源底座对国内厂商再封装是友好的。

## 10. PyTorch Lightning 供应链中招：Shai-Hulud 主题恶意包

标签：[EN · HN]
链接：<https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/>

HN 299 分。Semgrep 安全团队发现 PyTorch Lightning 的依赖链里被塞进了一个恶意包，攻击者以《沙丘》里的 Shai-Hulud 沙虫为内部代号。Payload 瞄准开发者凭据和任何拉这个包的 AI 训练管线。重点不在 payload 本身，而是这是本季度第二次高调针对 ML 训练栈的供应链攻击——一个被污染的 wheel 包能毒化所有下游训练出来的模型。如果你的 CI 跑 PyTorch Lightning，今天就去锁版本、查 lockfile。

---

## 编者按

今天的总主题是"平台权力的边界由谁来画"。第 1 条和第 2 条是同一家公司同一周里看起来完全相反的两个动作——单看都自洽，并列起来才看得见故事。第 8 条是结构性的：Anthropic 在抢服务收入，不只是 API 收入。第 10 条最无聊但最紧急——请现在就去检查 PyTorch Lightning 的 lockfile。
