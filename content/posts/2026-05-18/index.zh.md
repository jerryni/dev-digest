---
title: "5月18日 · 今日技术精选"
date: 2026-05-18T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "安全", "SQLite", "Anthropic", "Rivian", "V2EX"]
categories: ["daily"]
summary: "周一一波杂烩：openwall 上 Gentoo 开发者被供应商绕开漏洞披露的旧事重提，honker.dev 把队列和 cron 塞进单个 SQLite 文件，Simon Willison 写了个 datasette-llm-limits 给团队的 LLM 账单上限；Bun 改 Rust 的事情这次轮到 Zig 社区写公开信。"
---

## 今日速览

周一三条主线：第一条是工具链层在变得更"小而美"——honker.dev 把 durable queue / pub-sub / cron 全压进一个 SQLite 文件，Simon Willison 又顺手为 Datasette 写了个按用户限额的 LLM 控费插件，这类小工具是 AI 时代后端的真实长尾。第二条是供应链与披露伦理：openwall 上"CopyFail 漏洞没通知 Gentoo 维护者"的讨论 312 分上 HN 首页，回头看也牵出 Forgejo 那边的尾巴。第三条是大基建的回摆：HN 首页 712 分的"比利时停止核电去工业化"和 331 分的"Rivian 允许彻底关掉车载联网"——一个在能源、一个在汽车，都指向同一件事：去年看似不可逆的趋势开始有人公开往回拨。

## 今日 10 条

### 1. honker.dev：把 durable queue / 流 / pub-sub / cron 都装进一个 SQLite 文件（HN · EN）

[原文：honker.dev](https://honker.dev/) · [HN 讨论](https://news.ycombinator.com/item?id=47963316)

这是那种"读完你心里要么大喊牛逼要么开始挑刺"的工具：单进程、嵌入式、用 SQLite 做存储，提供持久消息队列、流、pub/sub 和 cron 调度器。HN 上 158 分，最高赞评论在拿它和 NATS、Redis Streams 对比，本质是在问"你的后端真的需要一个独立的中间件吗"。对国内的中小创业公司，这种"零运维 + 一个文件就是基础设施"的方案很适合那种 PMF 还没到、不能为运维多花一个人的阶段。

### 2. CopyFail 漏洞当初没通知 Gentoo 维护者，Forgejo 又冒出新尾巴（HN · EN）

[openwall 邮件列表](https://www.openwall.com/lists/oss-security/2026/04/30/10) · [Forgejo 后续](https://dustri.org/b/follow-up-to-carrot-disclosure-forgejo.html) · [HN 讨论](https://news.ycombinator.com/item?id=47965108)

漏洞披露的伦理问题又被翻出来：报告者把 CopyFail 通报给了某个上游，但 Gentoo 这种被波及的下游发行版没收到。结果就是 Gentoo 用户裸奔了一段时间。HN 上 312 分讨论里反复出现一句话——"披露不是给一个人，是给整条供应链"。在国内做开源运维的同学，这条值得收藏，下次写披露 SOP 可以拿来当反例。

### 3. Simon Willison 写了 datasette-llm-limits，给团队的 LLM 账单上限（Simon Willison · EN）

[原文 / 插件介绍](https://simonwillison.net/2026/May/15/)

和 datasette-llm-accountant 配套使用，可以为每个用户（或全局）设置 LLM 调用的硬上限。Simon 自己的用法是给 Datasette 实例里跑的所有自然语言查询设一个月度预算。技术上没多复杂，但在 AI 时代它解决的是真问题——团队接入 LLM 后，"账单失控"在 V2EX、Slack、Discord 上几乎天天有人哀嚎。能不能把上限写进基础设施层、而不是靠老板提醒，已经成了团队成熟度的一个分水岭。

### 4. V2EX："Bun 的 Rust 重写——一封来自 Zig 社区的公开信"（V2EX · ZH）

[原帖 v2ex.com/t/1213191](https://www.v2ex.com/t/1213191)

Bun 上周宣布从 Zig 迁到 Rust，Zig 社区写了封公开信回应。措辞克制但底气足，大致意思是：你走可以，但请不要把"Zig 不成熟"挂在公开材料里当 PR——Bun 这几年遇到的具体问题，社区有详细的修复路径。V2EX 上的中文讨论分两派：一派觉得 Zig 没人撑大旗这事不光是技术问题，另一派觉得 Bun 这次迁移本身就是 Claude Code 把人力成本压下来的实战展示。结合 5/12 Publickey 那篇"Bun 用 Claude 在做 Zig→Rust"的报道一起读，会更立体。

### 5. V2EX：一个独立开发者做的 macOS Finder 右键增强 iRight（V2EX · ZH）

[原帖 v2ex.com/t/1213192](https://www.v2ex.com/t/1213192)

把"压缩"、"批量重命名"、"复制路径"这些日常操作直接塞进 Finder 右键。代码不复杂但用心，作者还在帖子里附了上架前的体验反馈流程。值得一看的是评论区——好几个 macOS 老用户分享了自己原本用的工具（PathFinder、Default Folder X、Forklift），可以当作一份"非 Apple Silicon 时代之后还活着的 Finder 增强工具"清单。

### 6. Anthropic 的 Claude Platform 正式在 AWS 上线，full set 不再保留（Publickey · JA）

[Publickey 原文](https://www.publickey1.jp/blog/26/anthropicawsclaude_platform_on_awsclaude_platform_on_awsclaudeaws.html)

之前在 AWS Bedrock 上只能用到部分功能的 Claude，现在 Claude Platform on AWS 正式版上线，新功能基本不再"先 Anthropic 直营、后 AWS"地按版本错开。对在日华人开发者来说，意义是：合规上需要走 AWS Japan 的客户，现在不用为"哪些功能能用"反复确认了。日本企业 IT 部门常年在 AWS 上做合规和采购流程，这一步把 Anthropic 从"另一条独立采购线"变回了"Bedrock 目录里的一项"。

### 7. Publickey：存储厂商 CEO 公开说半导体零件价格涨了 4-10 倍，整机要涨价 70%（Publickey · JA）

[Publickey 原文](https://www.publickey1.jp/blog/26/ceo41070.html)

Everpure 的 CEO 在面向投资者的电话里直白讲了零件涨价的级别：从过去的 4 倍到最近的 10 倍。下一步是把企业存储产品整机涨价 70%，并且警告"还会再涨"。这条对国内云厂商和私有部署客户都有直接影响——明年企业级 SSD/HDD 采购预算需要重新做。日文圈讨论里最尖锐的一条评论是："这不是供需问题，是 AI 训练把整个 NAND 周期吃完了。"

### 8. Rivian 提供"彻底关闭车载联网"开关（HN · EN）

[Rivian 官方文档](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) · [HN 讨论](https://news.ycombinator.com/item?id=47967786)

Rivian 用户可以在 App 里一键关掉所有数据回传、远程功能和 OTA。HN 上 331 分，热评里有人提到这和上周 Toyota RAV4 那位车主"自己把 DCM 和 GPS 模块拆掉"的故事是同一种诉求，只是 Rivian 选择把它做成出厂功能。对国产新势力来说，这是一道镜子：除了 Toyota 这种被迫接受的"硬拆"，能不能在出厂设置里给用户一个干净的选项，正在成为隐私意识强的用户的购车筛选条件。

### 9. 比利时议会反向操作：停止核电站去工业化（HN · EN）

[原文 dpa-international.com](https://dpa-international.com/general-news/urn:newsml:dpa.com:20090101:260430-930-14717/) · [HN 讨论](https://news.ycombinator.com/item?id=47961319)

HN 上 712 分。比利时本来按计划要陆续退役剩余的核电站，议会刚通过决议——停止退役、保留运行。背景是欧洲电价持续高、风光出力不稳、AI 数据中心和电动车把基线负载拉得更高。这条对在欧洲做基础设施的人来说是个信号：核电的"政治叙事"在 2024-2026 这两年真的翻了页。技术圈的连带反应是数据中心选址重新评估，比利时和邻近的法国可能重新进入 hyperscaler 的候选清单。

### 10. "你可以打败二分查找"——Daniel Lemire 的一篇硬核基准测试（HN · EN）

[原文 lemire.me](https://lemire.me/blog/2026/04/27/you-can-beat-the-binary-search/) · [HN 讨论](https://news.ycombinator.com/item?id=47924912)

Lemire 用一段 SIMD-friendly 的"分支预测对齐 + 数组探针"代码，在大数组上跑过了标准的二分查找。重点不是 SIMD 本身，而是他给出了非常清楚的"什么尺寸下哪种方法更快"的拐点表。HN 上 226 分，评论里出现了几位编译器后端的工程师在补充 cache line 行为的细节。如果你最近在写自定义 KV/索引层，这篇值得读完再去 benchmark 自己代码。

## 编者按

今天的元主题是"小而美 + 旧规则的回摆"。前面三条（honker.dev、CopyFail 披露、datasette-llm-limits）说明在 AI 暴走的时代，团队开始重新看重"基础设施层的克制"——一个 SQLite 文件、一次披露要把整条供应链走完、把 LLM 账单当成 first-class 治理对象。后面三条（Rivian、比利时核电、Lemire 二分查找）则提醒我们：去年看似板上钉钉的趋势（车联网默认全开、核电淘汰、二分查找已是最优），其实都在被重新质疑。如果只看两条，建议看 #1（honker.dev）感受工具克制的美学，再看 #2（CopyFail）补一节披露伦理课。今日 Zenn 趋势页内容未能渲染、HN 上的 GitHub Trending 也未抓到完整列表，相关 slot 已替换为其他 EN 源。
