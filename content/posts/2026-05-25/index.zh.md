---
title: "5月25日 · 今日技术精选"
date: 2026-05-25T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "privacy", "ai-agents", "supply-chain", "china-ai", "google", "browsers"]
categories: ["daily"]
summary: >-
  Rivian 让车主一键彻底切断车机与外网的所有连接，传统车厂被迫被对齐到一个新隐私默认值。LinkedIn 被发现扫描 6278 款浏览器扩展并把结果加密塞进每次请求，浏览器作为指纹来源再被重新发现一次。SQLite 又长出新的器官：honker.dev 把队列、流、Pub/Sub、cron 都塞进单个 .db 文件。Shai-Hulud 主题恶意包钻进 PyTorch Lightning，AI 训练侧的供应链第一次被正面打。V2EX 这边国内 token 套餐被吐槽，"自掏腰包给公司干活"的话题再上桌。日本侧 Google 在 I/O 后第二波放出 Managed Agent API 和 Antigravity 2.0。SpaceX S-1 顺手曝出 Anthropic 每月 12.5 亿美元买算力的合同。Mozilla 正面反对 Chrome 内置 Prompt API。今天的主线：AI 时代的隐私默认值、供应链信任、算力账单，都在重写之中。
---

## 今日速览

今天的新闻互相照应：Rivian 把"完全离线"做成一个开关，LinkedIn 反向把"你装了什么扩展"做成指纹——两件事都是在重新分配"默认值的拥有权"。Shai-Hulud 把恶意代码塞进 AI 训练库 PyTorch Lightning，意味着 AI 供应链已经不能假设"上游可信"。国内开发者今天关注的两件事——某些 token 套餐的实际可用性、以及"自费买 token 干公司工作"——其实是同一件事：在 AI 真的进入日常之后，企业和个人之间的算力账谁来掏，还没规则。日本侧 Google 在 I/O 之后第二轮放料，Managed Agent API 和 Antigravity 2.0 把"AI agent as a managed runtime"的玩法补完。再加上 SpaceX 招股书里曝出的 Anthropic 12.5 亿美元/月合同，AI 的"物理底盘"正在被新一轮锁定。

## 1. Rivian 允许彻底关闭车机与外网的所有连接

[Rivian allows you to disable all internet connectivity](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) · `Rivian / HN`

Rivian 在支持页里明确写了一段：车主可以一键关闭车辆和外网的所有数据交换，不是只关"诊断数据"，而是连 OTA、地图更新、车队遥测都断掉。在车机后台默认连接厂商云、且很多功能必须联网才能用的现在，这条 SOP 等于在传统车厂头上立了一个新隐私下限。值得注意的是，这是产品页直接给出来的，不是 EFF 喊出来的——这种"主动写进 KB"的姿态比口号有用。

## 2. LinkedIn 扫描 6278 款浏览器扩展并加密塞进每次请求

[LinkedIn scans for 6,278 extensions and encrypts the results into every request](https://404privacy.com/blog/linkedin-is-scanning-your-browser-extensions-this-is-how-they-use-the-data/) · `404privacy.com / HN`

研究者反编译 LinkedIn 的 JS 后发现，页面会主动探测 6278 个扩展是否被安装，把结果做加密指纹后跟着每一次后端请求一起上传。这种"扩展指纹"在浏览器端被默认认为不可见——但 web 平台本身没有阻止这种侧信道。对国内做 To B SaaS 和广告归因的团队意义是：扩展指纹已经在头部社交产品的生产链路里跑了，问题不是能不能做，而是要不要做、能不能合规做。

## 3. honker.dev：把队列、流、Pub/Sub、cron 全装进一个 SQLite 文件

[Durable queues, streams, pub/sub, and a cron scheduler – inside your SQLite file](https://honker.dev/) · `honker.dev / HN`

又一个"SQLite 当后端"的项目，但这次更激进：作者把消息队列、流处理、Pub/Sub、定时器统统封到单个 .db 里，所有 worker 直接读这个文件，不需要 Redis、不需要 RabbitMQ、不需要 cron 守护进程。"小项目用不上 Kafka"这个空白领域被一直拼，但把 cron 也塞进来的版本是第一次见。对独立开发和小团队部署来说，省下的运维心智不止一倍。

## 4. 阿里云 tokenplan 和百度 codingplan 慎买

[阿里云 tokenplan 和 百度 codingplan 慎买](https://www.v2ex.com/t/1214866) · `V2EX`

V2EX 网友 zhengmin4516 列了一串具体场景，说阿里云的 tokenplan 和百度的 codingplan 在实际用量、有效期、退款条款上跟宣传出入大，跟帖里几十位用户接力补刀。核心吐槽点是：promo 写"无限"实际限速、按月不按用量结算让长尾用户吃亏。在 Claude / OpenAI 的境外卡支付逐渐稳定的背景下，国内 token 套餐要靠"信任红利"才有人买，这种贴一旦传开会真切影响下个季度的转化。

## 5. 自掏腰包给公司买 token 干活——你也这样吗

[你们多少人是自己付费买 token 干公司的工作任务了？](https://www.v2ex.com/t/1214981) · `V2EX`

楼主 libasten 抛出一个普遍但少有人讲的问题：公司没批 Claude / Cursor 预算，但活儿不用 AI 已经做不完了，结果一帮人在用自己的信用卡买 token。跟帖意见两极——有人说"工具自费就跟自己买好键盘一样正常"，也有人说"等于把生产力成本悄悄从公司转嫁到个人"。这条贴值得财务和 HR 看：AI 时代的"自费器材清单"已经形成，企业不主动管，员工会自己定下来。

## 6. Google 发布 Managed Agent API：一行 API 启动带 Linux 环境的 AI 代理

[APIコール一発でGoogleがホストするLinux環境付きのAIエージェントを起動](https://www.publickey1.jp/blog/26/apigooglelinuxaimarkdownmanaged_agent_api.html) · `Publickey`

Google 在 I/O 后又补了一刀：Managed Agent API 允许开发者只发一个 HTTP 请求，就在 Google 后台拉起一个带完整 Linux 沙箱的 AI 代理，行为指令直接用 Markdown 写。这意味着"agent runtime"被产品化了——开发者不再自己搭 Docker、不再自己 wrap MCP，直接用 GCP 算账单。对国内做 agent 产品的团队，这是一个清晰的对标：要么"管理执行环境"、要么"管理工作流"，二选一。

## 7. Google Antigravity 2.0：现场演示从零写 OS、跑 Doom

[Google、「Antigravity 2.0」発表。デモとしてゼロからOSを開発、Doomも実行可能に](https://www.publickey1.jp/blog/26/googleantigravity_20osdoom.html) · `Publickey`

Antigravity 2.0 在 I/O 后正式登场，Google 的演示尺度颇大：让 agent 从零开始写一个能跑 Doom 的迷你 OS。这种 demo 实际目的是把 "高复杂度长时任务" 的可信度做成视觉证据，正面打 Claude Code、Cursor 的市场认知。配套也宣布 Android 正式支持、推出 Android Knowledge Base / Android Skills——对国内 Android 团队，是评估"是否接 Antigravity 工具链"的关键时点。

## 8. Shai-Hulud 主题恶意代码钻进 PyTorch Lightning AI 训练库

[Shai-Hulud Themed Malware Found in the PyTorch Lightning AI Training Library](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · `semgrep.dev / HN`

Semgrep 的研究员发现 PyTorch Lightning 依赖链里被植入了带有 Shai-Hulud（沙丘里巨虫）品牌特征的恶意包——目标是 AI 训练流水线本身。这种位置非常凶险：你训练的模型不直接受影响，但训练机器上的 SSH key、cloud creds、wandb token 都被收割。"AI 供应链"过去主要讨论模型权重的污染，现在被拉到训练侧依赖污染——风险面从下游推理直接前移到上游训练。所有跑 ML 工作流的团队今天就该检查 lockfile。

## 9. SpaceX 招股书曝光：Anthropic 每月支付 12.5 亿美元买算力

[SpaceX S-1 文件 — Anthropic 与 COLOSSUS / COLOSSUS II 算力合同](https://www.sec.gov/Archives/edgar/data/1181412/000162828026036936/spaceexplorationtechnologi.htm) · `SEC / Simon Willison`

SpaceX 招股书里有一段直接命名 Anthropic：双方签订云服务合同，Anthropic 每月支付 12.5 亿美元，合同至 2029 年 5 月，可由任一方提前 90 天终止。这是一组少见的数字——把"前沿模型公司的物理底盘到底有多贵"做成可披露金额。对照同期 Anthropic 与 AWS 的合作，"AI 算力多源采购"的格局已经从口头叙述变成 SEC 文件。这条数字应该被任何讨论 AI 经济性的稿件作为基准引用。

## 10. Mozilla 公开反对 Chrome 内置 Prompt API

[Mozilla's opposition to Chrome's Prompt API](https://github.com/mozilla/standards-positions/issues/1213#issuecomment-4347988313) · `GitHub mozilla/standards-positions`

Mozilla 在标准立场库里给 Chrome 提出的 Prompt API 投下明确反对票，理由集中在三点：把 LLM 做成浏览器 API 会让网页指纹更密；浏览器内置模型的版本/能力差异会变成新的 web fragmentation；以及"在 web 标准里嵌入特定厂商能力"的先例。这事对前端工程师的意义是：Chrome 想让网页直接 `await ai.prompt(...)` 的方向，正在遇到来自 Mozilla 的体系性阻力——Web 平台未来到底是"内置 AI"还是"通过 fetch 调远端 AI"，这一票会影响很久。

## 编者按

今天的 10 条围绕三条暗线串起来：**隐私默认值的所有权**（Rivian / LinkedIn / Mozilla）、**AI 供应链信任**（Shai-Hulud / 国内 token 套餐 / Antigravity 与 Managed Agent）、**算力账单的可见性**（SpaceX-Anthropic 合同 / 自费买 token）。如果今天只挑两条读：第一条选 **Shai-Hulud 钻进 PyTorch Lightning**——它把"AI 供应链"从概念词推到具体 CVE；第二条选 **SpaceX S-1 里的 12.5 亿美元/月数字**——它给所有"AI 是不是泡沫"的争论提供了一个可被引用的下限。
