---
title: "5月27日 · 今日技术精选"
date: 2026-05-27T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "浏览器指纹", "供应链安全", "ai-agent", "web-标准", "ai-编码工具", "核电", "隐私"]
categories: ["daily"]
summary: >-
  LinkedIn 被扒出会扫描浏览器里 6278 个扩展名单并加密回传；Mozilla 给 Chrome 的 Prompt API 打了一个"有害"的标准立场；PyTorch Lightning 中招了 Shai-Hulud 风格的供应链投毒。Docker 把它的 CLI AI agent「Gordon」推到正式版；.NET MAUI 终于离开 Mono 运行时迁到 CoreCLR。比利时因为 AI 数据中心负载预期暴涨，正式停止核电站退役。Rivian 真的给车主开了一个"全部断网"的开关。Armin Ronacher 吐槽用 LLM 重写过的 GitHub issue 全是套话。今天的主题是：信任的边界正在被重新画线——浏览器和站点之间、AI 和代码库之间、AI 改写过的文本和 bug 系统之间。
---

## 今日速览

今天的 10 条放到一起，问题其实是同一个：**2026 年我们到底还能在哪一层信任对方？** LinkedIn 在网页端每次请求都把"你装了哪些扩展"加密塞进去，让浏览器指纹这件事重新变成对抗问题；Mozilla 罕见地用最强烈措辞反对 Chrome 在浏览器内置 LLM，理由是会撕掉 Web 多年来"写一次到处跑"的核心契约；PyTorch Lightning 被供应链投毒，说明 AI 训练链已经变成攻击者的主目标而不是边门。工具层面，Docker 这周把 CLI 里的 AI agent「Gordon」推到 GA；与此同时 Cursor 被 V2EX 用户实测降额，另一拨人开始公开讨论"公司不付费的情况下用什么 AI 写代码"。最后两条 wildcard——比利时因为 AI 用电需求把核电退役计划撤回，以及 Rivian 真的做了一个"全部断网"的车机开关——都说明这一周里很多默认假设正在被翻新。

## 1. LinkedIn 每次请求都在扫你装了哪 6278 个浏览器扩展

[LinkedIn scans for 6,278 extensions and encrypts the results into every request](https://news.ycombinator.com/item?id=47967262) · `404privacy.com / HN 299`

404privacy 反向了 LinkedIn 网页端，发现它会按一张硬编码的 6278 个扩展 ID 表逐个探测（用 web-accessible-resource ping），然后把结果做位图并加密随每个请求回传。这里的"加密"不是端到端，而是为了对抗浏览器扩展层面的拦截。重点不只是"被监视"——而是大型 SaaS 已经把"你装了哪些扩展"当成指纹的一部分。在公司里用扩展白名单的 IT，应该意识到这相当于通过员工的 LinkedIn session 给整个组织"打了标签"。国内开发者要注意：Boss 直聘、脉脉这类如果学样照搬，会很快变成隐私合规问题。

## 2. Mozilla 给 Chrome 的 Prompt API 打了"有害"标签

[Mozilla's opposition to Chrome's Prompt API](https://github.com/mozilla/standards-positions/issues/1213#issuecomment-4347988313) · `github.com/mozilla / HN 564`

Mozilla 在 standards-positions 仓库给 Chrome 的 `window.ai.languageModel` 提案正式打了 "harmful"。核心理由：一个浏览器内置的 LLM 接口没法规范化，因为它的输出既不可重现，也无法跨浏览器版本化。Mozilla 担心这会破坏 Web "一次书写、处处运行"的契约。Apple WebKit 团队也在底下不算高调地附议了。结论很直接：今天如果你在产品里用 Chrome 的 Prompt API，就要做好"它是 Chrome 独占特性"的长期心理准备——很可能再也不会出现在 Firefox 和 Safari 里。

## 3. PyTorch Lightning 中招供应链投毒

[Shai-Hulud themed malware found in the PyTorch Lightning AI training library](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · `semgrep.dev / HN 299`

Semgrep 抓到一个被注入 PyTorch Lightning 间接依赖的恶意包，主题沿用上季度肆虐 npm 的 "Shai-Hulud" 系列。Payload 直奔 HuggingFace token、AWS key、Wandb session——正好覆盖训练流水线手里的全部凭证。这事的真正信号是：AI 训练仓库现在站在 2020 年构建系统的位置，攻击者已经把它当主路径而不是附带战场。在 CI 里烤模型权重的团队，要把训练侧的供应链按生产部署的标准来防。

## 4. Docker 的 AI agent「Gordon」正式 GA

[Docker 专用 AI Agent「Gordon」正式发布，免费账号也能用](https://www.publickey1.jp/blog/26/dockeraigordondocker.html) · `Publickey`

Docker 这周把 Gordon 推到正式版，直接绑在 Docker CLI 里，`docker ai` 一条命令就能让 agent 读你的 Dockerfile、解释构建错误、给出修复建议并直接落到本地文件。免费额度对个人开发者基本够用。值得注意的不是它和 Claude Code、Antigravity 在 IDE 层面竞争——而是它在某一个工具的 CLI 里内置。接下来两个季度 kubectl、terraform、gh 大概率会出同一种形态的内置 agent，国内的 oss-tools 也会迅速跟进。

## 5. .NET MAUI 终于离开 Mono 运行时

[.NET MAUI 移行到 CoreCLR，告别 Xamarin 时代的 Mono](https://www.publickey1.jp/blog/26/mononet_mauinet_mauimonocoreclr.html) · `Publickey`

微软确认下个 .NET MAUI 大版本会在移动端和桌面端从 Mono 切到 CoreCLR——这是 Xamarin 被收购以来等了多年的迁移。对跨平台 .NET 团队的实际影响：iOS 上 AOT 性能明显改善，GC 行为和服务器端 .NET 统一，几个长期 Mono 才有的奇怪行为（特别是泛型接口分派那块）会消失。如果一直拖着没从 Xamarin.Forms 升级，现在运行时已经齐了，可以动手。

## 6. Cursor 对 500 次档用户出手了，老用户在找最后能用的版本

[Cursor 对 500 次用户出手了吗，最近可用的旧版本是多少](https://www.v2ex.com/t/1215208) · `V2EX`

V2EX 上一帖跟踪了 Cursor 静默收紧 $20 Pro 档"500 次 fast request"的真实可用量，多个用户复现：新版本会把以前算作 fast 的请求重新归到 slow。帖子下面变成了一个"哪个历史版本还按宣传走"的互助贴。和上周 Claude Code「OpenClaw」事件一起看就清楚了——AI 编码工具已经从"速率限制是未来的问题"，进到了那种灰色地带执行的阶段，版本固定（version pin）会变成常规操作。

## 7. 公司不给钱，到底用哪个 AI 写代码？

[公司不给钱我该用哪个 AI 码代码？](https://www.v2ex.com/t/1215305) · `V2EX`

V2EX 上一个非常务实的帖子，从国内开发者视角盘点了"自费/零费"挡的 AI 编码工具现状。比较一致的几个选择：阿里云免费额度里的 Qwen3-Coder、Google AI Studio 的 Gemini、本地 4090 跑开源模型。明显缺席的是：Claude（个人付费门槛太高）、Cursor（参见第 6 条）、Copilot（企业账号绑定）。对正在做个人项目、又被卡在公司没采购 AI 工具的程序员，这一帖比厂商的 benchmark 页有用得多。

## 8. 比利时撤回核电站退役计划

[Belgium stops decommissioning nuclear power plants](https://news.ycombinator.com/item?id=47961319) · `dpa-international / HN 712`

比利时联邦政府正式暂停核电站关停计划，并准备立法把现有反应堆寿命延到 2035 年以后。理由直白：AI 和云计算的用电需求把所有 2022 年的预测都打穿了。比利时不是孤例，德国、荷兰、瑞典内部都在吵同一件事，但比利时是欧盟里第一个真正撤回退役时间表的。和上周 HBM 显存供应那条放在一起看：AI 基础设施的成本不是 Nvidia 一家在吃，是整个物理世界在一层一层被收费。

## 9. Rivian 给车主真的开了一个"全部断网"的开关

[Rivian allows you to disable all internet connectivity](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) · `rivian.com / HN 331`

Rivian 在车机里悄悄加了一个开关，可以一键关掉车辆所有外网连接，包括 OTA、车队遥测、远程诊断。不分套餐、不带 upsell。和其他车企"恨不得每块铁皮都联网"的方向完全相反。HN 楼里一群人在抓包验证，目前看是真的全断了。如果你在做安全模型里要考虑车机遥测，可以从此把 Rivian 这个开关当作"行业能做到的下限"来引用。国内新势力会不会跟进，是个挺值得观察的指标。

## 10. Armin Ronacher 吐槽用 LLM 重写过的 GitHub issue

[Armin Ronacher：你重写过的 issue 全是套话，请直接写四点](https://lucumr.pocoo.org/2026/5/24/pi-oss/) · `lucumr.pocoo.org / Simon Willison`

Armin Ronacher（Flask 作者）这周开源新写的 Pi runtime 之后，收到了一大堆明显被 LLM 改写过的 issue。他把这种"AI slop issue"的失败模式总结得很清楚：被 LLM 浓缩之后的报告爱用过分自信的语气，捏造最小复现，模糊真正重要的四点——跑了什么命令、期望什么、实际看到了什么、错误日志原文是什么。开源维护者写 issue 模板的时候，可以把这四点直接放进去。诚实的 bug 报告就四条，再长就是 slop。

## 编者按

今天的主题词是 **"信任的边界正在重画"**。LinkedIn 把"你装了哪些扩展"悄悄塞进自己的指纹；Mozilla 直接说浏览器内的 LLM 接口不能要；PyTorch Lightning 被打穿正是因为它站在 AI 训练上游；Cursor 重新定义什么算"fast"请求；AI agent 钻进每一个工具的 CLI（Docker Gordon）；最后还有 Armin Ronacher 在拒绝 AI 当人和人之间的中介——每一层都在被迫重新讨论"谁能看到、谁能决定、谁能替谁说话"。今天必读两条：先看 **第 2 条（Mozilla vs Prompt API）**，理解为什么 Web 平台没法干净地装下一个 LLM；再看 **第 10 条（Armin 关于 slop issue）**，是同一个问题在人际流程里的版本。
