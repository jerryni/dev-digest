---
title: "6月3日 · 今日技术精选"
date: 2026-06-03T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "openai", "codex", "stanford", "rolldown", "vite", "anthropic", "alphabet", "v2ex"]
categories: ["daily"]
summary: "OpenAI 全线 Codex 进 AWS；Stanford 把 CS336 的全套讲义都放出来了；V2EX 一夜哀嚎 Codex 突然要二次手机验证；日本工具链圈在庆祝 Rolldown 1.0 进 Vite 8.0。"
---

## 今日速览

今天的主线还是"AI 基础设施重新洗牌"。OpenAI 把 Codex 和前沿模型一起塞进 AWS，等于在 GCP/Azure 之外补上了关键一块；Alphabet 转头宣布 800 亿美金股权融资专门砸 AI 算力；Anthropic 昨天递完 S-1，今天又把 Project Glasswing 安全联盟扩了一圈。中文圈这边没人关心这些大新闻——大家集中精力在骂 OpenAI 一夜之间给所有 Codex 账号上了二次手机验证。日文圈的关注点最技术：Rust 写的 JS 打包器 Rolldown 1.0 终于发了，Vite 8.0 直接把它换成默认底盘。

---

### 1. OpenAI 前沿模型 + Codex 正式入驻 AWS — `[Hacker News · 285 pts]`
<https://openai.com/index/openai-frontier-models-and-codex-are-now-available-on-aws/>

OpenAI 把 GPT-5.5 / 5.4 / 5.3 和 Codex 系列全线接入 AWS Bedrock，定价和 Azure 持平。对早期就把后端押在 AWS 的团队是直接的减负，不用再为了用 GPT 单独跑一条出口流量；但更值得关注的是 OpenAI 的姿态变化——之前 Sam 多次强调"算力主权"绑死 Azure，这次明显是市场份额优先于站队。国内通过 Bedrock 中转的玩法可能也会再热一阵，毕竟 AWS 在新加坡和东京的 region 比 Azure 更稳。

### 2. Stanford CS336：从零搭语言模型的完整课程公开了 — `[Hacker News · 480 pts]`
<https://cs336.stanford.edu/>

Percy Liang 那门"Language Modeling from Scratch"今年的全套讲义、作业、参考实现都上线了。从 tokenization、Transformer 实现、数据 pipeline，一直到 RLHF 和评估，每一步都有可跑的 PyTorch 代码。配套的 `assignment1-basics/CLAUDE.md`（昨天上 HN 那份）就是这门课给 AI agent 写的协作规范。对国内自学 LLM 的人来说，比花钱买课实在得多——这是这个领域目前最完整的一份"从 0 到 1"教材，免费的。

### 3. Codex 一夜之间要求所有账号二次手机验证 — `[V2EX · 多个热帖]`
<https://www.v2ex.com/t/1217218>

V2EX 首页今天被 Codex 二次验证刷屏，至少四个独立热帖：登录不了、重新登录被卡、Plus 账号也被风控。同时 OpenAI Plus 美区也开始查手机号。表面是反滥用，实际上是 OpenAI 在 AWS 上线前的合规清账——把那些靠多账号 / 共享池续命的灰色玩法集中处理。对国内做"中转池"生意的影响会非常直接，做 vibe coding 副业的也要做好"账号一夜清零"的预案。

### 4. GitHub Copilot 模型定价调整：GPT-5.5 倍率 57x — `[V2EX · 程序员]`
<https://www.v2ex.com/t/1217216>

新版 Copilot 计费里 GPT-5.5 是 57 倍 premium，相当于一个 request 顶 57 个普通请求；Sonnet 4.6 是 12 倍。这意味着 Copilot Pro+ 那 1500 次额度里，正经用 GPT-5.5 写代码大概 26 个请求就没了。讨论里大家的对策很一致：日常切回 Sonnet，关键 review 时才呼叫 GPT-5.5。这也间接说明，AI coding 的成本曲线还没收敛到"价格不再是日常决策"的程度，离 SaaS 那种平价订阅的体感还远。

### 5. Rolldown 1.0 正式发布，被 Vite 8.0 采用为默认打包器 — `[Publickey · 6月2日]`
<https://www.publickey1.jp/blog/26/rustjavascriptrolldown10vite_80.html>

Vite 团队和 Rolldown 团队合并工具链的努力终于落地：Rust 写的 Rolldown 1.0 是 esbuild 的功能完整替代，性能据测试比 esbuild 高 30-50%，且支持完整的 Rollup 插件 API。Vite 8.0 把 dev 和 build 阶段统一切到 Rolldown，开发体验和生产构建第一次走的是同一条路径。对国内大型前端项目（webpack 时代留下的 monorepo）来说，这是个把构建时间从 90 秒压到 20 秒的契机。

### 6. AWS Kiro Web：浏览器里直接用的 AI 编码 Agent — `[Publickey · 5月28日]`
<https://www.publickey1.jp/blog/26/awswebaikiro_web.html>

AWS 把 Kiro（之前要装本地 IDE）做成了纯 Web 版本，绑定 AWS 账号即开即用。区别于 Cursor / Windsurf 这类编辑器，Kiro 走的是 "spec-driven" 路线：先让你写需求文档，再让 agent 实现。对企业客户的吸引力很明显——不用给开发者每人配一份外部订阅，IT 直接通过 AWS 账单统一管理。国内做"企业内编程 agent"的厂商可以参考这个产品定位。

### 7. Anthropic 扩大 Project Glasswing 安全联盟 — `[Anthropic 官方 · 6月2日]`
<https://www.anthropic.com/news/expanding-project-glasswing>

Project Glasswing 是 4 月份 Anthropic 牵头、AWS / Apple / 谷歌 / 微软 / NVIDIA 等十几家公司联合发起的"关键软件安全"项目。这次扩容主要是加了开源社区和欧洲玩家。对开发者实际影响有限，但这件事对 Anthropic 的政治资本有意义——配合昨天的 S-1 递交，是在 IPO 前主动把"AI 公司也是负责任的基础设施提供方"这个故事讲得更圆。

### 8. Alphabet 宣布 800 亿美金股权融资，专投 AI 基础设施 — `[Hacker News · 205 pts]`
<https://abc.xyz/investor/news/news-details/2026/Alphabet-Announces-Proposed-80-Billion-Equity-Capital-Raise-to-Expand-AI-Infrastructure-and-Compute-2026-b0myAMewCa/default.aspx>

谷歌母公司 Alphabet 单笔股权融资 800 亿美金，明确用途是 AI 算力扩张——TPU 工厂、数据中心、电力采购。这是科技巨头近十年最大规模的一次股权融资。结合微软去年的 800 亿 capex 和 Meta 的 700 亿，2026 年的 AI 基建总盘子已经过 3000 亿美金。对国内做大模型预训练的团队是一个冷峻信号：算力差距在拉大，不是变小。

### 9. 加密推理 blob：OpenAI 推理过程到底能不能加密？ — `[Hacker News · 101 pts]`
<https://blog.cryptographyengineering.com/2026/05/29/fooling-around-with-encrypted-reasoning-blobs/>

Matthew Green 的长文，把 OpenAI 新引入的"encrypted reasoning blob"机制拆开看：每次 chain-of-thought 都被加密上传，号称连 OpenAI 自己都看不到中间推理过程。Green 的结论是技术上设计还行，但 trust model 仍然依赖"OpenAI 不会偷偷换密钥"。对做企业级 AI 部署的工程师有现实意义——很多合规问答场景终于有了"我能拿这个去说服 CISO"的理论支撑。

### 10. Michael Burry：Anthropic / SpaceX 都不值 1 万亿 — `[Hacker News · 42 pts]`
<https://www.businessinsider.com/big-short-michael-burry-spacex-anthropic-ipo-ai-bubble-claude-2026-6>

《大空头》原型 Michael Burry 在 Anthropic 递完 S-1 第二天发推，明确说 Anthropic 9650 亿、SpaceX 1.4 万亿都过头了。HN 评论分成两派：一派说"他每次都喊泡沫，对一次也是对"；另一派认真讨论 Anthropic 当前营收 vs 估值的差距。这条放进来不是因为预测多准，而是 AI 一级市场的"泡沫论"开始从博客圈进入主流财经媒体，做 startup 的人需要意识到融资环境的拐点信号。

---

## 编者按

今天的 meta-theme：**AI 大公司的"基础设施战国时代"正式开打**。OpenAI 抢 AWS、Alphabet 砸 800 亿、Anthropic 把安全联盟扩大——三家头部都在用不同方式锁定未来五年的算力和叙事主权。开发者侧最值得读的两条：**第 2 条 Stanford CS336**（如果你还想了解大模型怎么工作）和**第 5 条 Rolldown 1.0**（如果你管的项目还在 webpack 上）。

Zenn 今天 trending 数据不可抓取，已用其他源补足。
