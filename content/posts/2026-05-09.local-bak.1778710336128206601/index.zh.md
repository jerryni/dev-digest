---
title: "5月9日 · 今日技术精选"
date: 2026-05-09T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Claude", "Bun", "AWS", "隐私", "Anthropic"]
categories: ["daily"]
summary: "谷歌悄悄把 reCAPTCHA 在去 Google 化的 Android 上玩坏了；一篇『我又回到了 AWS，又一次想起为什么离开』在 HN 拿了 732 分；Bun 的 Rust 重写测试通过率 99.8%；Timothy Gowers 用 ChatGPT 5.5 Pro 做真·研究级数学；欧盟把 VPN 框成『需要封堵的漏洞』。"
---

## 今日速览

今天的主线是平台权力收紧——Google 在 Android 一侧、欧盟在 VPN 一侧、Meta 在 Instagram DM 一侧——中间穿插一篇广为流传的"我又回到了 AWS"事后复盘。如果只看三条：1、4、7。

---

## 1. Google 让 reCAPTCHA 在去 Google 化的 Android 上彻底失效

标签：[EN · HN 热门]
链接：<https://reclaimthenet.org/google-broke-recaptcha-for-de-googled-android-users>

HN 1520 分。reCAPTCHA 的挑战逻辑最近的一次更新，把 CalyxOS、GrapheneOS 等去 Google 化的 Android 系统直接判为可疑流量——大部分主流网站的图形验证都基本过不去。Google 没说是不是有意，但效果非常明确：脱离 Google Mobile Services 的代价又被抬高了一截。和下面第 7 条一起看：本季度"逃离 Google 移动生态"的成本，正在被一块砖一块砖地加上去。

## 2. 「我回到了 AWS，又一次记起当初为什么离开」

标签：[EN · HN 热门]
链接：<http://fourlightyears.blogspot.com/2026/05/i-returned-to-aws-and-was-reminded-hard.html>

HN 732 分。作者本来从 AWS 迁去了一家小云厂，后因为企业客户硬性要求又迁回来——然后写了这周最火的运维事后复盘。核心吐槽：IAM 复杂到成了护城河、控制台和 API 行为漂移、多账号组织结构的认知负担、账单工程已经发展成一个独立岗位。结论不是 AWS 烂，而是"在 AWS 上跑业务的人均认知开销是结构性的，不是技术好就能压下去的"——而这个开销，从来没人在迁移决策里 list 出来过。

## 3. Bun 的 Rust 重写测试通过率冲到 99.8%

标签：[EN · HN 热门]
链接：<https://twitter.com/jarredsumner/status/2053047748191232310>

HN 691 分。Jarred Sumner 宣布 Bun 从 Zig 到 Rust 的实验性移植，已经在 Linux x64 glibc 上通过了 99.8% 的原测试套件——比绝大多数人预期都要快得多。HN 评论里主要在讨论"为什么换"：贡献者更好招、标准库对系统编程更友好、工具链更成熟。结构上的看点是：这是迄今最高调的 Zig→Rust 迁移之一，可能给一批撞上"贡献者招不到"墙的新语言项目立个先例。

## 4. Timothy Gowers 写下用 ChatGPT 5.5 Pro 做数学的真实体验

标签：[EN · HN 热门]
链接：<https://gowers.wordpress.com/2026/05/08/a-recent-experience-with-chatgpt-5-5-pro/>

HN 689 分。菲尔兹奖得主 Timothy Gowers 把一次"用 5.5 Pro 推研究级数学"的过程完整写了下来：模型在哪些地方真的帮到他、哪些地方编得煞有介事但完全错、哪些证明骨架需要他自己来动刀修。结论可以这样转述：对严肃数学家来说这已经不是玩具了，但替代不掉"你必须自己验证"这一环。这个月最有力的"AI 没有平台期"反例。

## 5. Simon Willison：做语音 AI，WebRTC 本身就是问题

标签：[EN · Simon Willison]
链接：<https://simonwillison.net/2026/May/9/luke-curley/>

Simon 引了 Luke Curley 的一篇文章，论点是：WebRTC 在结构上不适合 LLM 语音接口——它为了保实时性会激进丢音频包，这套设计对 Zoom 通话合理，对慢吞吞的生成式响应完全反向（你宁愿多等 200ms 也不想要被损坏的 prompt）。Curley 还指出："浏览器里你根本无法重传一个 WebRTC 音频包"——这种底层细节在 OpenAI 的语音 AI 营销稿里永远不会被提。

## 6. 用 Claude Code：HTML 输出格式被严重低估

标签：[EN · HN]
链接：<https://twitter.com/trq212/status/2052809885763747935>

HN 513 分。Claude Code 团队的 Thariq Shihipar 写了一个很有冲击力的论点：对解释类任务，应该让 Claude 输出 HTML 而不是 Markdown。代价（多花的 token）在 GPT-4 时代是大事，在百万 token 上下文时代基本可以无视；收益（可以塞 SVG 图、颜色高亮、内嵌交互组件）则非常大。如果你从 GPT-4 时代起就习惯让模型"用 Markdown 回答我"，这套算盘可以重新打一遍了。

## 7. 欧盟议会研究报告：VPN 是"需要堵上的漏洞"

标签：[EN · HN 热门]
链接：<https://cyberinsider.com/eu-calls-vpns-a-loophole-that-needs-closing-in-age-verification-push/>

HN 635 分。一份欧洲议会委托研究服务做的报告，把面向消费者的 VPN 定义为欧盟年龄验证体系的障碍，并建议监管介入。具体手段还含糊——可能是供应商登记、强制日志、下游平台义务——但措辞本身才是要点："漏洞"这两个字把一个隐私工具直接重新框定成了需要被治理掉的对象。即使没有立法落地，"网络匿名是不是合法"这个 Overton 窗口已经又被收紧了一截。

## 8. V2EX：AI 让事物贬值，各种层面上

标签：[ZH · V2EX]
链接：<https://www.v2ex.com/t/1211027>

短帖，但论点很硬：以前所有用来标记"作者用心了"的细节——一份精致 README、一个 100 commit 的 GitHub 仓库、一篇结构清晰的博客、一段写得到位的 PR 描述——现在每一个都能在几分钟内被 LLM 量产，因此都不再有信号价值。建议和今天第 4 条放一起看：Gowers 那篇是 AI 在价值链上面往上爬，V2EX 这帖是同一个动作从下面看是什么样子。

## 9. Zenn：AI Agent 时代的数据库设计，Turso 在重写规则

标签：[JA · Zenn]
链接：<https://zenn.dev/emuni/articles/6eef9f97f564b4>

Zenn 上 85 赞。エムニ（Emuni）一位工程师的论点：Agent 工作负载——大量短生命周期、每任务一个独立 DB——恰好是 Turso "数百万个便宜 SQLite 实例"模型的目标场景。文章给了详细成本数：Turso 上一 agent 一库每月几美分，对比 Postgres-per-tenant 几美元。如果你在做多租户 agent 系统，值得拿这个架构姿态对照一下你现在的 Postgres-per-tenant 方案。

## 10. 一个 u32 就拿到 root：io_uring ZCRX freelist LPE

标签：[EN · HN]
链接：<https://ze3tar.github.io/post-zcrx.html>

HN 213 分。Linux io_uring 零拷贝接收路径里的新本地提权——一个非特权用户用一个 u32 攻击者可控的输入就能触发的 freelist 管理 bug。作者把整个利用链写得很教学。io_uring 的安全记录还在继续给运维制造噩梦，那点热路径性能收益不知道值不值这价。如果你跑的是硬化过的多租户 Linux 集群，今天就 patch。

---

## 编者按

今天的主旋律是平台权力在收紧——Google 收 Android、欧盟收 VPN、Meta 收 Instagram E2EE——中间夹一篇关于"想离开 AWS 但回不去"的怀旧文。1 和 7 一起是监管线索，3 和 4 一起是技术进度线索。如果你最近在做多云决策，看第 2 条；如果你认为 AI 已经到平台期，看第 4 条，Gowers 那篇是这个月最有分量的反例。
