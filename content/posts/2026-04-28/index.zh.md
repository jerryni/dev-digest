---
title: "4月28日 · 今日技术精选"
date: 2026-04-28T07:00:00+09:00
draft: false
tags: ["digest", "2026-04", "ai", "agents", "openai", "microsoft", "github-copilot", "ruby", "security", "claude-code"]
categories: ["daily"]
summary: "今日 HN 头条爆雷：Microsoft 和 OpenAI 正式终止独家与收入分成协议（737 分），AGI 条款也已成历史——AI 大厂格局重排。GitHub Copilot 转 usage-based billing 上 532 分，开发者钱包准备好。Mercor 4TB AI 标注员声音样本被偷（431 分），合同工的隐私债开始结账。pgbackrest 停止维护（392 分），Postgres 圈集体地震。微软 VibeVoice 用 MIT 协议开源 Whisper 级语音模型，Mac 上一行 uv 命令跑通。日本圈 Matz 亲自下场写 Ruby AOT 编译器 Spinel。"
---

## 🌏 今日速览

今天的主线明牌：**Microsoft 和 OpenAI 七年的独家深度绑定关系正式松绑**——HN 头条 737 分，Bloomberg 独家，独家计算合同 + 收入分成 + 那条诡异的"AGI 触发条款"今天集体进了博物馆。Simon Willison 还专门写了一篇追踪 AGI 条款历史的考古文章。**GitHub Copilot 改 usage-based 计费**（HN 532 分，408 评论）——团队订阅时代结束，从今天起每个 prompt 都要按 token 算钱，CFO 们得重新盯成本表。**Mercor 4TB 声音样本失窃**（HN 431 分）——4 万名 AI 标注员的声音泄漏，AI 训练数据合规债开始进入还款期。**pgbackrest 停止维护**（HN 392 分）——这工具是 PG 圈最主流的备份方案之一，今天等于地震。日本圈最值得读的两条：Matz **亲自下场写 Ruby AOT 编译器 Spinel**（Zenn），CAMPFIRE 因 GitHub 凭据泄漏导致 22.5 万人个人信息泄漏的复盘。国内圈 V2EX 这两天最实用：AI token 中转 + OpenCode 攻略两连发，Claude Code 的成本焦虑大家都在自救。

---

## 🔥 今日 10 条

### 1. [Hacker News / Bloomberg] Microsoft 和 OpenAI 终止独家计算与收入分成协议
**链接：** https://www.bloomberg.com/news/articles/2026-04-27/microsoft-to-stop-sharing-revenue-with-main-ai-partner-openai
HN 第一（737 分，648 评论）。两家从 2019 年开始的 130 亿美元婚约今天换成了"开放式关系"——Microsoft 不再是 OpenAI 的独家云厂商，OpenAI 也不再向微软支付那笔（外界估算）20% 的收入分成。配菜是 Simon Willison 的[考古文章](https://simonwillison.net/2026/Apr/27/now-deceased-agi-clause/)，专门追踪了那条"如果 AGI 实现，Microsoft 的商业 IP 权利失效"诡异条款的演变史，今天这条款也"已死"。对国内做 AI 基础设施的团队来说，最大的信号是：OpenAI 接下来可以更自由地走 AWS / GCP / Oracle，云市场的分蛋糕逻辑要换。给关注 AGI 法律边界的同学一份冷静读物。

### 2. [Hacker News / GitHub Blog] GitHub Copilot 切换到 usage-based 计费
**链接：** https://github.blog/news-insights/company-news/github-copilot-is-moving-to-usage-based-billing/
HN 第 22（532 分，408 评论）。从今天起 Copilot 不再是"公司给每人买一份订阅就完事"——每次调用按 token 算钱，重度用户的月费可能直接翻倍甚至更多。评论区的两派立场很清晰："这是诚实定价，agent 时代必然如此" vs "团队预算彻底失控，HR 又得开会"。**对国内/在日华人开发者来说，最实用的应对**：(a) 立刻在团队里建一个 token 消耗 dashboard；(b) 重新评估 Claude Code / Cursor / Codex 各家的实际单价；(c) Copilot 的"无限用"心智模型可以放下了。这件事和上周的 Claude Pro Opus 限额（[HN 同日 #18](https://support.claude.com/en/articles/11940350-claude-code-model-configuration)）合起来读：AI 编码工具集体进入 metered 时代。

### 3. [Simon Willison / Microsoft] microsoft/VibeVoice —— MIT 协议的 Whisper 替代品
**链接：** https://github.com/microsoft/VibeVoice
微软今年 1 月发布、Simon Willison 今天才上手测试的语音转文字模型——MIT 协议、自带说话人分离（diarization），M5 Max MacBook Pro 上跑 1 小时音频耗时 8 分 45 秒。Simon 给的 Mac 一行命令很值得收藏：`uv run --with mlx-audio mlx_audio.stt.generate --model mlx-community/VibeVoice-ASR-4bit --audio lenny.mp3 ...`，跑出来的 JSON 直接带 speaker_id 时间戳。**对国内做语音转文字产品的团队**意义在于：本地离线 + MIT 协议 + 自带分离，企业内合规场景一下就好做了。最大限制：单次最多 1 小时，需要切片。

### 4. [V2EX] 自己搞了个 AI token 中转，能用 Codex / Claude Code
**链接：** https://www.v2ex.com/t/1208203
楼主把自己的中转方案发出来给大家测——背景是 Claude Code / Codex 国内访问的稳定性和成本问题，自建中转既可以用国产模型（如 DeepSeek、GLM）作为 fallback，也可以做 token 用量的精细切分。回帖里有一串实战经验：限速、缓存、模型路由、token 计费。**这个帖子和今天 HN 的 GitHub Copilot 涨价配合读最有意思**——海外开发者面对 metered 计费的反应是吐槽，国内开发者直接动手做中转。一种 V2EX 特色的"精打细算"。

### 5. [V2EX] OpenCode 详细攻略，开源版 Claude Code，免费模型与神级插件
**链接：** https://www.v2ex.com/t/1204410
楼主写了一份相当扎实的 OpenCode（[github.com/sst/opencode](https://github.com/sst/opencode)）使用指南——可以接入 Gemini 3 Pro、Claude 4.5 Opus、DeepSeek V4、GLM 5.1 等多家模型，免费额度组合后能撑相当一段时间。Zenn 今天[也有一篇日本人写的 OpenCode 上手帖](https://zenn.dev/xxishan/articles/9cb47819f835fa)，可见这股"找便宜替代"的浪潮国内外同步。**对独立开发者**的实用建议：把 OpenCode 当 Claude Code 的"成本调节阀"——重要任务上 Claude，灰活儿丢给 OpenCode + 国产模型。

### 6. [Zenn] Matz の Ruby AOT 编译器 "Spinel" 试用报告
**链接：** https://zenn.dev/geeknees/articles/edc3cb36ea251c
Matz（松本行弘，Ruby 之父）亲自下场做的 Ruby AOT 编译器 Spinel，作者第一时间上手测试。Ruby 圈这几年最大的疑问之一是"YJIT 之后下一步是什么"——AOT 是其中一条路。文章给了具体的本地构建步骤、benchmark 对比、以及目前的限制（部分动态特性还没支持）。**对国内 Ruby 团队**（说实话已经不多了，但中后台还有一些 Rails 项目）的意义在于：Ruby 性能故事可能要进入新一章。日本作为 Ruby 大本营，Zenn 的反应通常比英文圈早一两天。

### 7. [Zenn] CAMPFIRE 22.5 万人信息泄漏 —— 从 GitHub 凭据看安全
**链接：** https://zenn.dev/awesome_kou/articles/campfire-github-breach-2026
日本最大众筹平台 CAMPFIRE 因 GitHub 凭据泄漏（疑似 PAT 或 OAuth token 被盗），导致 22.5 万人的个人信息外流。作者把事件复盘 + 通用对策做成了一篇结构化文章：怎么扫历史 commit 的泄漏、PAT 必须最小权限、CI 不要用长期 token。**国内/在日华人开发者**应该把这篇当 checklist 用——尤其是个人 side project 在 GitHub 公开仓库里的，今天花 30 分钟用 [trufflehog](https://github.com/trufflesecurity/trufflehog) 扫一遍历史 commit 不亏。

### 8. [Hacker News] 4TB 声音样本被偷 —— Mercor 4 万名 AI 合同工数据泄漏
**链接：** https://app.oravys.com/blog/mercor-breach-2026
HN 第 12（431 分，160 评论）。Mercor 是给 AI 公司提供"专家标注 / 数据生成"的服务商，这次泄漏的 4TB 包含了 4 万名合同工的声音样本（用于 RLHF / 语音模型训练）。最大的合规问题不是数据量，而是**这些样本的同意书条款是否覆盖了"被泄漏后第三方再训练"**的场景——极大概率没有。这件事和今天的 microsoft/VibeVoice（#3）放一起看就很讽刺：开源语音模型让任何人都能 fine-tune，被偷的训练数据立刻有变现路径。**做 AI 数据合规的同学**今天就该把这篇转给法务。

### 9. [Hacker News] pgbackrest 不再维护
**链接：** https://github.com/pgbackrest/pgbackrest
HN 第 24（392 分，204 评论）。PostgreSQL 生态用得最广的备份工具之一今天宣布停止维护——主作者发了 readme 更新，社区分裂成两派：一派准备 fork，一派开始迁移到 pg_basebackup / barman / wal-g。**对国内中大型 Postgres 用户**的影响：（a）短期内别恐慌，已部署的版本继续工作；（b）三个月内做迁移评估；（c）如果你团队有人自荐 maintainer，[issue #4123](https://github.com/pgbackrest/pgbackrest/issues) 是入口。这件事再次提醒一个老话题：核心开源基础设施的 bus factor 是真问题。

### 10. [Hacker News] Show HN：Dirac OSS Agent 在 Gemini-3-flash-preview 上拿下 TerminalBench
**链接：** https://github.com/dirac-run/dirac
HN 第 25（293 分，118 评论）。一位独立开发者把自己的 OSS agent + Gemini 3 Flash Preview 跑 TerminalBench 拿了第一——超过了商业产品的成绩。代码量不大（~3k LOC Python），核心是个紧凑的工具调用循环 + 结构化日志。**两个看点**：(a) 当今 SOTA agent 的实现复杂度其实远低于很多人想象；(b) Flash 等小模型 + 好 harness 已经能在垂直 benchmark 上挑战大模型 + 成熟产品。对国内做 agent 平台的同学：值得抠下来读完，对照看自己的 harness 还能瘦多少。

---

## ✍️ 编者按

今天有两条主线。**第一条是"AI 商业格局正在松动"**：Microsoft 和 OpenAI 解绑 (#1) 是顶部信号，GitHub Copilot 改 metered 计费 (#2) 是中部信号，国内开发者搞 AI token 中转 (#4) 和 OpenCode 攻略 (#5) 是底部信号——三层一起说明同一件事："AI 推理成本"从早期被云厂商和大模型公司补贴的状态，正在快速回到市场定价。**第二条是"AI 生态的合规债开始结账"**：Mercor 声音数据泄漏 (#8) + CAMPFIRE GitHub 凭据泄漏 (#7) + microsoft/VibeVoice 的开源 (#3) 三条放一起看就完整：训练数据被偷 → 开源语音模型加持下变现门槛极低 → 合规和事故风险呈非线性增长。pgbackrest 停止维护 (#9) 是另一条暗线——基础设施的 maintainer 持续性问题，不会因为 AI 而消失，只会因为大家把注意力都给了 AI 而恶化。

**强烈推荐：**
1. **MS / OpenAI 解绑 (#1)** —— 今天的"行业 GPS 重置"，做 AI infra 选型的同学务必读。
2. **GitHub Copilot 改 usage-based (#2)** —— 24 小时内把团队 token 消耗 dashboard 搭起来，下个月再做也来得及，但今天做最准。

—— Dev Digest 编辑
