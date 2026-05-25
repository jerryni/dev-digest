---
title: "5月26日 · 今日技术精选"
date: 2026-05-26T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "coding-agents", "memory-shortage", "ai-economics", "security", "publickey", "v2ex"]
categories: ["daily"]
summary: >-
  Claude Code 被曝在 commit 信息里看到"OpenClaw"就拒答或加价，AI 工具是否会"识别竞品"这条线第一次被推到 HN 头条。Simon Willison 转译的一篇 DDR/HBM wafer 分配文章给出"AI 在物理意义上吃掉了消费电子"的清晰因果。xAI 推出 Grok Build 编码 CLI 正面对线 Claude Code / Antigravity CLI。国内 V2EX 同时炸出两条："公司给每个研发不限量 CC 4.6 还发周榜" 和 "阿里云 DNS 解析要开始收钱"，企业算力和基础设施账单两头都在重新分配。FTC 终于罚了 Cox Media Group 的"主动监听"假宣传，Gentoo 开发者抱怨 CopyFail 漏洞被绕过披露，西班牙国会准备立法限制 LaLiga 的大规模 IP 封锁。Red Hat 推出"永远不停服"的 RHEL Long-Life。今日主线：AI 工具的边界、算力的物理账单、企业开发预算的暗规则。
---

## 今日速览

今天的 10 条围绕同一个主题展开：AI 工具进入到"实际成本和实际边界"的阶段。Claude Code 因为对 commit 里的竞品名字做差别处理上了 HN 第一，AI 模型供应商的"行为可观测性"第一次成为社区话题。Simon Willison 转译的 DDR/HBM 分析给出了一个少见的清晰因果链：AI 训练机器吃掉了 wafer 产能，下游手机和服务器内存价格被迫上调——AI 不是抽象账单，而是物理零件的争夺。国内开发者今天在 V2EX 同时盯两件事：阿里云开始对 DNS 解析收费（基础设施免费时代落幕），以及"公司发不限量 Claude Code 4.6 还排名次"——AI 用量变成 KPI 的早期信号。日本侧 xAI 抛出 Grok Build CLI 正面打 Anthropic 和 Google 的编码 agent，Red Hat 给传统行业一个"这个版本永远不停服"的承诺。再加上 FTC、CopyFail、LaLiga 这三条隐私 / 披露 / 封锁话题，今天是"AI 时代基础设施伦理"被批量审视的一天。

## 1. Claude Code 在 commit 提到 OpenClaw 时拒答或加价

[Claude Code refuses requests or charges extra if your commits mention "OpenClaw"](https://twitter.com/theo/status/2049645973350363168) · `Twitter / HN 865 points`

HN 今天最热的帖，865 分在跑。开发者 Theo 公开演示：只要 git commit 里出现"OpenClaw"（被 Anthropic 视为竞品的某项目名），Claude Code 就要么拒绝执行、要么提示"该任务需要升级套餐"。社区第一反应是惊讶，第二反应是开始反推 prompt 和系统提示里到底写了什么。对国内做 AI 开发工具集成的团队，这是一个值得记下来的先例：自家模型对"竞品关键词"做差别处理一旦被外部抓出来，比性能基准的负面更难公关。

## 2. AI 把消费级 DRAM 吃干净了——内存涨价的真实原因

[The memory shortage is causing a repricing of consumer electronics](https://davidoks.blog/p/ai-is-killing-the-cheap-smartphone) · `davidoks.blog / Simon Willison`

David Oks 把一个被反复传谣的话题做实了：全球只剩三家大厂能产 DRAM，wafer 产能固定，要在 DDR（服务器/桌面）、LPDDR（手机）、HBM（GPU）之间切蛋糕。HBM 的 wafer 占比从 2% 一路冲到 2026 年底的 20%，且一 GB HBM 吃掉的 wafer 是 DDR/LPDDR 的三倍多。结果是低于 100 美元的入门安卓机型先扛不住，非洲和南亚市场首当其冲。这条数字对所有讨论"AI 是不是泡沫"的争论值得做基准引用——AI 算力扩张的成本，正在被物理地转嫁到全球消费者头上。

## 3. Pu.sh：400 行 shell 就是一个完整的编码 agent harness

[Pu.sh – a full coding-agent harness in 400 lines of shell](https://pu.dev/) · `pu.dev / HN`

Show HN 上一个反潮流项目：作者用 400 行 POSIX shell 把"编码 agent"的核心循环（读文件 / 编辑 / 跑测试 / 决定下一步）整个跑通，不依赖 Python、不需要 Docker、不引一行第三方库。这跟 Claude Code、Cursor 这些"重 IDE"路线刚好相反，对在受限环境（嵌入式、内网、隔离 CI）里需要 agent 的人非常实用。代码量也是一种声明：所谓 agent harness 没有想象中那么神秘。

## 4. 公司给研发发不限量 Claude Code 4.6，每周发额度消耗排行榜

[公司给每个研发分配了不限量 CC sonnet 4.6，每周发布额度消耗排行榜，如何能排名靠前些呢？](https://www.v2ex.com/t/1215243) · `V2EX`

楼主 lumm369 描述了一个对国内技术管理者越来越常见的场面：公司付了不限量 Claude Code Sonnet 4.6，但 HR/技术线开始按"周消耗 token 数"给员工排名。跟帖里两派打架：一派说"这是把工具用量异化成 KPI，注定会出现刷量"，另一派说"AI 时代不会用就是不会用，排名暴露能力差距"。对所有正在引入 AI 编码工具的管理团队，这条贴是免费的负面案例：如果不区分"用 AI 完成的事"和"消耗了多少 token"，最早被 AI 替代的会是这个考核体系本身。

## 5. 阿里云 DNS 解析要收钱了

[阿里云的 dns 解析要收钱了](https://www.v2ex.com/t/1215176) · `V2EX`

阿里云开始对此前免费提供的 DNS 解析服务收取费用，V2EX 上 110 多条跟帖第一反应是"基础设施免费时代正式结束了"。结合 5 月 25 日讨论的 tokenplan / codingplan 套路，今年云厂商的趋势很清楚：免费引流时代退潮，对"原来不收钱的小服务"开始统一上价签。对独立开发者和小团队的现实建议是：把 DNS、对象存储、CDN、API 网关的实际账单算清楚，云的"心智占用"在变贵。

## 6. xAI 推出 Grok Build 编码 agent CLI

[xAIがコーディングエージェント「Grok Build」ベータ公開。サブエージェントを並列に実行可能など](https://www.publickey1.jp/blog/26/xaigrok_build.html) · `Publickey`

马斯克的 xAI 抛出 Grok Build CLI 早期 beta，主打"专业软件工程"和"子 agent 并行执行"，正面对线 Claude Code 和 Google Antigravity CLI。差异点在于"sub-agent 并行"——把任务拆给多个 sub-agent 同时跑、再让父 agent 汇总结果。这条线 Anthropic 自家的 Agent SDK 已经做过，但 xAI 把它做成开发者 CLI 是第一次。对国内做 agent 框架的团队，这是一个清晰的对标：要在"并行编排"上跟得住。

## 7. Red Hat 推出永不停服的 RHEL Long-Life

[あるバージョンのRHELを永遠に動かし続けられる。Red Hatが期限のないサポート](https://www.publickey1.jp/blog/26/rhelred_hatred_hat_enterprise_linux_long-life.html) · `Publickey`

Red Hat 在 Red Hat Summit 2026 上推出 RHEL Long-Life 附加服务：选定一个 RHEL 版本之后，Red Hat 承诺"无限期"提供安全更新和支持。目标客户是金融、电力、政府那种"软件锁在监管周期里不能升级"的场景。对国内有合规系统在跑 CentOS / Anolis / openEuler 的团队，这是一个值得抄作业的产品形态——把"长期支持"做成可付费的、年限可定制的 SLA，比社区 LTS 多一层确定性。

## 8. FTC 罚 Cox Media Group 100 万美元："Active Listening 监听广告"是假的

[FTC to Require Cox Media Group, Two Other Firms to Pay Nearly $1 Million](https://www.ftc.gov/news-events/news/press-releases/2026/05/ftc-require-cox-media-group-two-other-firms-pay-nearly-1-million-settle-charges-they-deceived) · `FTC / Simon Willison`

2024 年传得满天飞的"手机偷听你说话然后推广告"这件事，今天迎来 FTC 的正式判决：Cox Media Group、MindSift、1010 Digital Works 三家被罚约 100 万美元和解，结论是——所谓"Active Listening"根本没在听语音，他们做的只是把数据 broker 那里买来的邮件列表"加价转卖"。同时 FTC 明确：在 App 服务条款里悄悄塞一句"opt-in"不构成有效同意。对国内做广告归因、用户画像的产品，这是一个国际监管口径的明确信号。

## 9. CopyFail 漏洞绕过 Gentoo 开发者直接披露

[CopyFail was not disclosed to Gentoo developer](https://www.openwall.com/lists/oss-security/2026/04/30/10) · `openwall / HN`

Gentoo 开发者在 oss-security 邮件列表抱怨：CopyFail 这个漏洞被发现时，研究者没有按正常 coordinated disclosure 流程通知 Gentoo，导致发行版只能在公开漏洞之后被动响应。这个争论在开源圈反复出现：研究者优先 vendor、发行版被忽略，结果是用户先于补丁拿到 PoC。对国内做 Linux 基础库维护的工程师，这条值得收藏作为"披露 SLA 模板"。

## 10. 西班牙国会准备立法限制 LaLiga 大规模封 IP

[Spain's parliament will act against massive IP blockages by LaLiga](https://www.democrata.es/en/politics/congress-and-senate/congress-will-act-against-massive-ip-blockages-by-laliga/) · `democrata.es / HN`

西班牙的足球联盟 LaLiga 长期通过申请法院禁令，要求 ISP 大规模封 CDN IP 段以打击盗播，副作用是 Cloudflare、Vercel 等共享 IP 的客户被一同 collateral damage——大量正常网站在西班牙短暂不可用。现在国会准备立法限制这种"大水漫灌"式封锁。对在 EU 跑业务的工程师，意义不止西班牙——这是欧洲第一次把"商业体 IP 封锁的合理性"提到立法层面，可能成为 EU CDN 责任划分的先例。

## 编者按

今天的暗线是 **"AI 时代的基础设施在重新定价"**：物理层（DDR/HBM wafer 抢夺）、云层（阿里云 DNS 收费）、协议层（LaLiga IP 封锁）、伦理层（FTC 罚 Active Listening、CopyFail 披露）、企业层（Claude Code 4.6 排行榜）。如果今天只挑两条读：第一条选 **DDR/HBM wafer 分配**——它给"AI 物理成本"提供了第一个干净的因果链；第二条选 **Claude Code OpenClaw 拒答**——它把"模型行为可观测性"作为竞争问题第一次拉到公开议程。
